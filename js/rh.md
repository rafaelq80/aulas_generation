<h1>Sistema de Gerenciamento de um RH</h1>



*Dado o Diagrama de Classes abaixo, construa uma aplicação que contenha um Menu principal, que forneça todas as operações do CRUD para um Sistema de RH:*



```mermaid
classDiagram
class Colaborador {
<<Abstract>>
  - id : number
  - nome : string
  - cargo : number
  - salario : number
  + get id() number
  + get nome() string
  + get cargo() number
  + get salario() number
  + set id(id: number) void
  + set nome(nome: string) void
  + set cargo(cargo: number) void
  + set salario(salario: number) void
  + abstract calcularSalario() number
  + visualizar() void
}
class Gerente {
  - gratificacao: number
  + get gratificacao() number
  + set gratificacao(gratificacao: number) void
  + calcularSalario() number
  + calcularGratificacao(valor: number) number
  + visualizar() void
}
class Vendedor {
  - comissao: number
  + get comissao() number
  + set comissao(comissao: number) void
  + calcularSalario() number
  + calcularComissao(percentual: number) number
  + visualizar() void
}
class Temporario {
  + visualizar() void
}
class ColaboradorRepository{
<< Interface >>
+ procurarPorId(id: number) void
+ listarTodos() void
+ cadastrar(colaborador: Colaborador) void
+ atualizar(colaborador: Colaborador) void
+ deletar(id: number) void
+ calcularSalario(id: number) void
+ calcularGratificacao(id: number, percentual: number) void
+ calcularComissao(id: number, percentual: number) void
}
class ColaboradorController{
+ procurarPorId(id: number) void
+ listarTodos() void
+ cadastrar(colaborador: Colaborador) void
+ atualizar(colaborador: Colaborador) void
+ deletar(id: number) void
+ calcularSalario(id: number) void
+ calcularGratificacao(id: number, percentual: number) void
+ calcularComissao(id: number, percentual: number) void
+ gerarId() number
+ buscarNaCollection(id: number) Conta
}
Colaborador <|-- Gerente
Colaborador <|-- Vendedor
Colaborador <|-- Temporario
Colaborador <.. ColaboradorRepository
ColaboradorRepository <|.. ColaboradorController

```

<br />

<h2>Menu Principal</h2>



<div align="center"><img src="https://i.imgur.com/lwoWNZI.png" title="source: imgur.com" /></div>

<br />

**Observações:**

- Gratificação e Comissão iniciam zeradas
- A Opção 6 - Calcular Salário deve ser aplicado somente aos Objetos das Classes Gerente e Vendedor
- A Opção 7 - Calcular Gratificação deve ser aplicada somente aos Objetos da Classe Gerente
- A Opção 8 - Calcular Comissão deve ser aplicada somente aos Objetos da Classe Vendedor
- Observe que os Objetos da Classe Temporário não podem executar o método Calcular Salário, porque o temporário tem salário fixo, mas o Método Calcular Salário será implementado na Classe porque é um Método Abstrato. Como resolver este problema, utilizando interfaces?

<br />

**Cálculos:**

- **Calcular Salário:** 
  - **Gerente:** salario + gratificacao (calculada)
  - **Vendedor:** salario + comissao (calculada)

- **Calcular Gratificação:** (percentual / 100) * salario  
  - *Adicionar o resultado no atributo gratificacao*
  - *O Percentual não pode ultrapassar 40%*

- **Calcular Comissão:** (percentual / 100) * salario
  - *Adicionar o resultado no atributo comissao*
  - *O Percentual não pode ultrapassar 10%*

