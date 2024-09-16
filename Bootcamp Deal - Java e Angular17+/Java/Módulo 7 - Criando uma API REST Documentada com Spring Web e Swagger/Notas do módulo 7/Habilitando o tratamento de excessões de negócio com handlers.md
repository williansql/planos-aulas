
> [!quote] [[Módulo 7 - Criando uma API REST Documentada com Spring Web e Swagger]]

## Exception Handlers

Exceções são mais comuns em qualquer fluxo de trabalho.

O tratamento de exceção, na ciência da computação, é o mecanismo responsável pelo tratamento da ocorrência de condições que alteram o fluxo normal da execução de programas de computadores

> [!tip] ![[Exception handling in Rest Sservice.canvas|Exception handling in Rest Sservice]]

Nossas aplicações precisam ser resilientes a possíveis comportamentos inesperados baseados na proposta de negócio e falando recursos HTTPs, realizamos implementações que centralizam e gerenciam este tipo de tratamento de excessões.

## Exception Handler

Um manipulador de exceção é o código que estipula o que um programa fará quando um evento anômalo interromper o fluxo normal das instruções desse programa.

> [!warning] Existem alguns tipos de tratamento de excessões em uma aplicação Spring Web, iremos ilustrar duas delas e focar na ControllerAdvice mais utilizada em nossos projetos.

#### Solução 1: Nível do controller - @ExceptionHandler

A primeira solução funciona no nível do @Controller, onde cada método trata uma exceção de forma declarativa com @ExceptionHandler.

#### Solução 2: O ResponseStatusExceptionResolver

Sua principal responsabilidade é usar a anotação @ResponseStatus disponível em exceções personalizadas e mapear essas exceções para códigos de status HTTP.

## RestControllerAdvice

Spring 3.2 traz suporte para um @ExceptionHandler global com a anotação **@ControllerAdvice**.
A anotação @ControllerAdvice nos permite consolidar nossos multiplos @ExceptionHandlers espalhados de antes em um único componente global de tratamento de erros.
- Isso nos dá controle total sobre o corpo da resposta, bem como o código de status.
- ele fornece o mapeamento de várias exceções ao mesmo método, para serem tratadas em conjunto.
- Ele faz bom uso da resposta RESTful ResponseEntity mais recente.

## GlobalExceptionHandler

Vamos configurar um tratamento de exceções global para interceptar todas as exceções que ocorrem em nossa aplicação, sem precisar tornar declarativo em todos os recursos.

> [!warning] Antes de continuar com este tutorial, certifique-se que você  já possui um projeto Spring Web para incluir as implementações abaixo.

#### Customizando nossas mensagens

Primeiro de tudo uma resposta HTTP mesmo sendo um Erro pode ser considerada um Objeto que será convertido em JSON expondo informações relacionadas a exceção disparada.

 