
> [!quote] [[Módulo 04 - Introdução a spring framework com spring boot]]

## Spring Framework 

é um framework open source desenvolvido para a plataforma Java baseado nos padrões de projetos, inversão de controle e injeção de dependência.
Sua estrutura é composta por módulos afins de reduzir a complexidade no desenvolvimento de aplicações simples ou corporativa.

## Spring Módulos

> [!tip] exemplo: ![[Spring Módulos.canvas|Spring Módulos]]

## Spring vs Java EE

Olhando um pouco a história, há muito, mas muito tempo atrás, o Java EE era realmente muito complicado e nem era necessário entrar numa discussão, usar o Spring era um caminho mais simples e mais fácil de evoluir. aí chegou a versão 5 do Java EE e a discussão voltou a ficar um pouco mais quente.

## Inversão de Controle

**Inversion of Control** ou **IoC**, trata-se do redirecionamento do fluxo de execução de um código retirando parcialmente o controle sobre ele e delegando-o para um container.
O principal propósito é minimizar o acoplamento do código.

## Sem IoC

> [!tip] ![[sem ioc.canvas|sem ioc]]


## Com IoC

> [!tip] ![[com ioc.canvas|com ioc]]


## Injeção de dependências

Injeção de dependência é um padrão de desenvolvimento com finalidade de manter baixo o nível de acoplamento entre módulos de um sistema.

> [!tip] ![[injeção d depêndencias.canvas|injeção d depêndencias]]


## Beans

Objeto que é instanciado (criado), montado e gerenciado por um container através do princípio de inversão de controle.

## Scopes

> [!tip] ![[scopes.canvas]]


## Singleton

O container do Spring IoC define apenas uma instância do objeto.

## Prototype 

Será criado um novo objeto a cada solicitação ao container.

## HTTP - Request

Um bean será criado para cada requisição HTTP.

>_Os objetos existirão enquanto a requisição estiver em execução_

## HTTP - Session

Um bean será criado para a sessão do usuário.

> _Precisamos acessar a mesma solicitação duas vezes para testar os escopos específicos da web._

## HTTP - Global

Ou Application Scope cria um bean para o ciclo de vida do contexto da aplicação.

> _Objetos compartilhados por toda a aplicação._

## Autowired

Uma anotação (indicação) onde deverá ocorrer uma injeção automática de dependência.

- **byName**: É buscado um método set que corresponde ao nome do Bean.
- **byType**: é considerado o tipo de classe para inclusão do Bean.
- **byConstructor**: Usamos o contrutor para incluir a dependência.

ajsdb