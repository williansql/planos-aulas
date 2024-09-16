
> [!quote] [[Módulo 06 - Adicionando segurança a uma API REST com Spring Security]]

## Introdução

O Spring Security é apenas um grupo de filtros de servlet que ajudam você a adicionar autenticação e autorização ao seu aplicativo da web.

## Terminologia

- **A autenticação**
	> refere ao processo de verificação da identidade de um usuário, com base nas credenciais fornecidas. Um exemplo comum é inserir um nome de usuário e uma senha ao fazer login em um site. Você pode pensar nisso como uma resposta à pergunta: _Quem é você?_
	
- **Autorização**
	> se refere ao processo de determinar se um usuário tem permissão adequada para executar uma ação específica ou ler dados específicos, supondo que o usuário seja autenticado com êxito. Você pode pensar nisso como uma resposta à pergunta: _Um usuário pode fazer / ler isso?_
	
- **Princípio**
	> refere-se ao usuário autenticado no momento.
	
- **Autoridade concedida**
	> refere-se à permissão do usuário autenticado.
	
- **Função** 
	> refere-se a um grupo de permissões do usuário autenticado.


## Habilitando Segurança

Em um projeto Spring Boot Web você precisa somente incluir a dependência no pom.xml

