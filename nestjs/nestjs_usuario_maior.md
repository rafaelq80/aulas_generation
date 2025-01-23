<h1>Projeto Integrador - Checar se o usuário é maior de idade</h1>

<br />

<h2>👣 Passo 01 - Adicionar o atributo dataNascimento na Classe Model</h2>



Adicione o atributo **dataNascimento** na Entidade **Usuario**:

```ts
    @IsDateString()
    @Column({type: "date"})
    dataNascimento: Date
```

<br />

<h2>👣 Passo 02 - Instalar a Biblioteca date-fns</h2>



A Biblioteca **date-fns** é uma Biblioteca Open Source que permite validar, manipular e fazer o parse (conversão) de datas no JavaScript de uma maneira muito simples e poderosa.

Para instalar a Biblioteca, execute o comando abaixo no terminal:

```bash
npm install date-fns --save
```

<br />

<div align="left"><img src="https://i.imgur.com/xYGHJlb.png" title="source: imgur.com" width="25px"/><a href=https://date-fns.org/docs/Getting-Started" target="_blank"><b>Documentação da Biblioteca Date-FNS</b></a></div>

<br />

<h2>👣 Passo 03 - Criar o Método calcularIdade() na Classe de Serviço</h2>



Na Classe de Serviço **UsuarioService**, adicione o Método abaixo:

```ts
public calcularIdade(dataNascimento: Date): number {

        return differenceInYears(new Date(), dataNascimento);
        
}
```

A função `differenceInYears` da biblioteca date-fns calcula a diferença em anos entre duas datas. No exemplo acima, está sendo calculada a diferença entre a data do momento em que o método foi executado e a data de nascimento do usuário, retornando o resultado em anos.

<br />

<h2>👣 Passo 04 - Chamar o Método calcularIdade na Classe de Serviço</h2>



Adicione as linhas abaixo dentro dos Métodos **create** e **update**, para verificar antes de persistir os dados no banco de dados, se o usuário é maior ou menor de idade:

```ts
	if (this.calcularIdade(usuario.dataNascimento) < 18)
            throw new HttpException('Usuário menor de idade!', HttpStatus.BAD_REQUEST);
```

O código final da Classe **UsuarioService** você confere abaixo:

```ts
import { HttpException, HttpStatus, Injectable } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { Usuario } from '../entities/usuario.entity';
import { Bcrypt } from '../../auth/bcrypt/bcrypt';
import { differenceInYears } from 'date-fns';

@Injectable()
export class UsuarioService {
    constructor(
        @InjectRepository(Usuario)
        private usuarioRepository: Repository<Usuario>,
        private bcrypt: Bcrypt
    ) { }

    async findByUsuario(usuario: string): Promise<Usuario | undefined> {
        return await this.usuarioRepository.findOne({
            where: {
                usuario: usuario
            }
        })
    }

    async findAll(): Promise<Usuario[]> {
        return await this.usuarioRepository.find();

    }

    async findById(id: number): Promise<Usuario> {

        const usuario = await this.usuarioRepository.findOne({
            where: {
                id
            }
        });

        if (!usuario)
            throw new HttpException('Usuario não encontrado!', HttpStatus.NOT_FOUND);

        return usuario;

    }

    async create(usuario: Usuario): Promise<Usuario> {
        
        const buscaUsuario = await this.findByUsuario(usuario.usuario);

        if (buscaUsuario)
            throw new HttpException("O Usuario já existe!", HttpStatus.BAD_REQUEST);

        if (this.calcularIdade(usuario.dataNascimento) < 18)
            throw new HttpException('Usuário menor de idade!', HttpStatus.BAD_REQUEST);

        usuario.senha = await this.bcrypt.criptografarSenha(usuario.senha)
        return await this.usuarioRepository.save(usuario);

    }

    async update(usuario: Usuario): Promise<Usuario> {

        await this.findById(usuario.id);

        const buscaUsuario = await this.findByUsuario(usuario.usuario);

        if (buscaUsuario && buscaUsuario.id !== usuario.id)
            throw new HttpException('Usuário (e-mail) já Cadastrado!', HttpStatus.BAD_REQUEST);

        if (this.calcularIdade(usuario.dataNascimento) < 18)
            throw new HttpException('Usuário menor de idade!', HttpStatus.BAD_REQUEST);
        
        usuario.senha = await this.bcrypt.criptografarSenha(usuario.senha)
        return await this.usuarioRepository.save(usuario);

    }

    public calcularIdade(dataNascimento: Date): number {

        return differenceInYears(new Date(), dataNascimento);
        
    }

}
```
