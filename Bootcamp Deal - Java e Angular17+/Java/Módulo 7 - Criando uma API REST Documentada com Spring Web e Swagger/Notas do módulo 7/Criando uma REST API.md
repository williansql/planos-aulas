


## Introdução

Implementar recursos HTTP para interação de arquivos JSON pelas aplicações.

## O que é API

Uma API **interface application program** é um código programável que faz a _ponte_ de comunicação entre duas aplicações distintas.

## Rest e RESTful

A API REST **representational state transfer** é como um guia de boas práticas e **RESTful** é a capacidade de determinado sistema aplicar os princípios de REST.

## Princípios

Para que uma arquitetura seja RESTful, é necessário ter uma série de princípios ou padrões.
Vejamos quais são eles:

- **Cliente servidor:** significa aprimorar a portabilidade entre várias plataformas de interface do usuário e do servidor, permitindo uma evolução independente do sistema.
- **Interface uniforme:** representa um interação uniforme entre cliente e servidor. para isso, é preciso ter uma interface que identifique e represente recurso, mensagens autodescritivas, bem como hypermedia **HATEOAS**.
- **Stateless:** indica que cada interação via API tem acesso a dados completos e compreensíveis.
- **Cache:** necessário para reduzir o tempo médio de resposta, melhorar a eficiência, desempenho e escalabilidade da comunicação.
- **Camadas:** permite que a arquitetura seja menos complexa e altamente flexível.

## Nível de maturidade

Para padronizar e facilitar o desenvolvimento de APIs REST, Leonard Richardson propôs um modelo de maturidade para esse tipo de API, definido em 4 níveis.

> [!tip] **Glory of REST**
> - Level 3: ==**Hypermedia Controls**==
> - Level 2: ==**HTTP Verbs**==
> - Level 1: ==**Resources**==
> - Level 0: ==**The Swamp of POX**==

#### Nível 0: Ausência de regras

Esse é considerado o nível mais básico e uma API que implementa apenas esse nível não pode ser considerada REST pois não segue qualquer padrão.
**Ex:**

| Verbo HTTP | URI             | Operação  |
| :--------- | --------------- | --------- |
| POST       | /getUsuario     | Pesquisar |
| POST       | /salvarUsuario  | Salvar    |
| POST       | /alterarUsuario | Alterar   |
| POST       | /excluirUsuario | Deletar   |
 > [!warning] Um único verbo com nomes que não seguem nenhum padrão.


#### Nível 1: Aplicação de Resources

| Verbo HTTP | URI         | Operação  |
| :--------- | ----------- | --------- |
| GET        | /usuarios/1 | pesquisar |
| POST       | /usuarios   | salvar    |
| PUT        | /usuarios/1 | alterar   |
| DELETE     | /usuarios/1 | deletar   |
 > [!warning] Observe que o nome dos recursos foram equalizados e para não gerar ambiguidade é necessário definir um o verbo apropriadamente.

#### Nível 2: Implementação de verbos HTTP

> [!note] Como a definição dos verbos já foi requisitada no Nível 1, o Nível 2 se encarrega de validar a aplicabilidade dos verbos para finalidades específicas como:

| Verbo HTTP | Função        |
| :--------- | ------------- |
| GET        | Retorna dados |
| POST       | Grava dados   |
| PUT        | Altera dados  |
| DELETE     | Remove dados  |
> [!warning] Existe uma discussão quando precisamos retornar dados através de parâmetros via body recebidos pelo método **POST**

#### Nível 3: HATEOAS

**HATEOAS** significa _Hypermedia as the engine of aplication state._ Uma API que implementa esse nível fornece aos seus clientes links que indicarão como poderá ser feita a navegação entre seus recursos. Ou seja, quem for consumir a API precisará saber apenas a rota principal e a resposta dessa requisição terá todas as demais rotas possíveis.

> [!warning] O nível 3 é sem dúvidas o menos explorado, muitas APIs existentes no mercado não implementam esse nível.

```
{
 	"id": 1,
 	"nome": "willians",
 	"sobrenome": "lisardo",
 	"links": [
 		{
 			"rel": "self",
 			"href": "http://localhost:8080/api/clientes/1"
 		},
 		{
 			"rel": "alterar",
 			"href": "http://localhost:8080/api/clientes/1"
 		},
 		{
 			"rel": "excluir",
 			"href": "http://8080/api/clientes/1"
 		}
 	]
} 
```


## Springboot REST API

Se preferir criar um projeto Spring Boot do zero, clique na imagem abaixo:

> [!tip] <a href="https://start.spring.io/" > <img src="https://miro.medium.com/v2/resize:fit:700/1*-uckV8DOh3l0bCvqZ73zYg.png" width="250px" ></a>

Ou simplesmente adicione o starter do spring-starter-web.

## Spring initializr

Site que oferece os recursos para criação de um projeto Springboot com uso do ==Maven== ou ==Gradle==
- Acesse o site: [Spring Initializr](https://start.spring.io/)
- Selecione a opção Maven ou Gradle.
- Selecione a opção Language - Java

#### Preenchimento

- **Group**: Nome do grupo organizacional.
- **Artifact**: Identificação do projeto.
- **Name**: Nome do Projeto (igual ao artifact).
- **Description**: Descrição do projeto.
