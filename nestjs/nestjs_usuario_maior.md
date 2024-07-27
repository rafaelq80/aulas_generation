<h1>Checar se o usuário é maior de idade</h1>

<br />

<h2>👣 Passo 01 - Adicionar o atributo dataNascimento na Classe Model</h2>



Adicione o atributo **dataNascimento** na Entidade **Usuario**:

```ts
    @IsDateString()
    @Column({type: "date"})
    dataNascimento: Date
```

<br />

<h2>👣 Passo 02 - Instalar a Biblioteca Moment JS</h2>



O **Moment.js** é uma Biblioteca Open Source que permite validar, manipular e fazer o parse (conversão) de datas no JavaScript de uma maneira muito simples e poderosa.

Para instalar a Biblioteca, execute o comando abaixo no terminal:

```bash
npm install moment
```

<br />

<div align="left"><img src="https://i.imgur.com/40SR2gG.png" title="source: imgur.com" width="25px"/><a href="https://momentjs.com/" target="_blank"><b>Documentação da Biblioteca Moment JS</b></a></div>

<br />

<h2>👣 Passo 03 - Importar a Biblioteca Moment JS</h2>



> [!CAUTION]
>
> **Este passo é muito importante!** 

<br />

Importe a Biblioteca **moment** na Classe de Serviço **UsuarioService** através da linha abaixo:

```ts
import * as moment from "moment";
```

Caso a importação a Biblioteca **moment** não seja efetuada com a linha acima, ao utilizar a Biblioteca, será exibida a mensagem de erro abaixo:

```bash
ERROR [ExceptionsHandler] (0 , moment_1.default) is not a function
```

<br />

<h2>👣 Passo 04 - Criar o Método calcularIdade() na Classe de Serviço</h2>



Na Classe de Serviço **UsuarioService**, adicione o Método abaixo:

```ts
    public calcularIdade(dataNascimento: Date): number {

        var agora = moment(new Date()); 
        var aniversario = moment(dataNascimento);
        var idade = agora.diff(aniversario, 'years');

        return idade;
    }
```

Vamos entender a implementação do Método **calcularIdade()**:

<div align="center"><img src="https://i.imgur.com/SkQ9uMz.png" title="source: imgur.com" /></div>

**Linha 3:** Obtém o momento exato da data atual em anos.

**Linha 4:** Obtém o momento exato da data de aniversário em anos.

**Linha 5:** Calcula a diferença entre a data atual e data de aniversário em anos.

**Linha 6:** Retorna a idade do usuário em anos.

<br />

<h2>👣 Passo 05 - Chamar o Método calcularIdade na Classe de Serviço</h2>



Adicione as linhas abaixo dentro dos Métodos **create** e **update**, para verificar antes de persistirs os dados no banco de dados, se o usuário é maior ou menor de idade:

```ts
	if (this.calcularIdade(objetoUsuario.dataNascimento) < 18)
            throw new HttpException('Usuário menor de idade!', HttpStatus.BAD_REQUEST);
```

O código final da Classe **UsuarioService** você confere abaixo:

```ts
import { HttpException, HttpStatus, Injectable } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { Bcrypt } from '../../auth/bcrypt/bcrypt';
import { Usuario } from '../entities/usuario.entity';
import * as moment from "moment";

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

        let usuario = await this.usuarioRepository.findOne({
            where: {
                id
            }
        });

        if (!usuario)
            throw new HttpException('Usuario não encontrado!', HttpStatus.NOT_FOUND);

        return usuario;

    }

    async create(objetoUsuario: Usuario): Promise<Usuario> {
        
        let buscaUsuario = await this.findByUsuario(objetoUsuario.usuario);

        if (!buscaUsuario) {

            if (this.calcularIdade(objetoUsuario.dataNascimento) < 18)
                throw new HttpException('Usuário menor de idade!', HttpStatus.BAD_REQUEST);

            if (!objetoUsuario.foto)
                objetoUsuario.foto = 'https://i.imgur.com/Sk5SjWE.jpg'
            
            objetoUsuario.senha = await this.bcrypt.criptografarSenha(objetoUsuario.senha)
            return await this.usuarioRepository.save(objetoUsuario);
        }

        throw new HttpException("O Usuario ja existe!", HttpStatus.BAD_REQUEST);

    }

    async update(objetoUsuario: Usuario): Promise<Usuario> {

        let updateUsuario: Usuario = await this.findById(objetoUsuario.id);
        let buscaUsuario = await this.findByUsuario(objetoUsuario.usuario);

        if (!updateUsuario)
            throw new HttpException('Usuário não encontrado!', HttpStatus.NOT_FOUND);

        if (buscaUsuario && buscaUsuario.id !== objetoUsuario.id)
            throw new HttpException('Usuário (e-mail) já Cadastrado!', HttpStatus.BAD_REQUEST);

        if (this.calcularIdade(objetoUsuario.dataNascimento) < 18)
            throw new HttpException('Usuário menor de idade!', HttpStatus.BAD_REQUEST);

        if (!objetoUsuario.foto)
            objetoUsuario.foto = 'https://i.imgur.com/Sk5SjWE.jpg'

        objetoUsuario.senha = await this.bcrypt.criptografarSenha(objetoUsuario.senha)
        return await this.usuarioRepository.save(objetoUsuario);

    }

    public calcularIdade(dataNascimento: Date): number {

        var agora = moment(new Date()); 
        var aniversario = moment(dataNascimento);
        var idade = agora.diff(aniversario, 'years');

        return idade;
    }
    
}
```

