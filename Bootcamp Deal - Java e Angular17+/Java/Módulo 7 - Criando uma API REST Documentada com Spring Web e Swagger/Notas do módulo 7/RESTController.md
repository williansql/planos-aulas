

## Primeiro Controller

Vamos criar nosso primeiro controller para uma demonstração de uso de nossos serviços pela web

## REST Contoller

Um **REST Controller** em Spring nada mais é que uma classe contendo anotações específicas para a disponibilização de recursos HTTPs baseados em nossos serviços e regras de negócio.
> [!tip] #### Anotações e configurações mais comuns
> - **@RestController:** Responsável por designar o bean de component que suporta requisições HTTP com base na arquitetura REST.
> - **@RequestMapping:** ("prefix"): Determina qual a URI comun para todos os recursos disponibilizados pelo **controller**.
> - **@GetMapping:** Determina que o método aceitará requisições **HTTP** do tipo **GET**
> - **@PostMapping:** Determina que o método aceitará requisições **HTTP** do tipo **POST**
> - **@PutMapping:** Determina que o método aceitará requisições **HTTP** do tipo **PUT**
> - **@DeleteMapping:** Determina que o método aceitará requisições **HTTP** do tipo **DELETE**.
> - **@RequestBody:** Converte um JSON para o tipo de objeto esperado como parâmetro no método.
> - **@PathVariable:** Consegue determinar que parte da URI será composta por parâmetros recebidos nas requisições.

## Controle de Usuários

Vamos disponibilizar as funcionalidades de CRUD da entidade **_User.Java_** através de uma API.
> [!warning] Antes de iniciar esta etapa, recomendamos revisar a etapa abaixo ou criar um **==Repositório Fake.==**

