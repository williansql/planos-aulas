
> [!quote] [[Módulo 06 - Adicionando segurança a uma API REST com Spring Security]]

O Spring possui algumas configurações para definir os usuários na sua camada de segurança, por padrão ele habilita um usuário de nome user e gera uma senha aleatoriamente a cada inicialização. Para aplicações em produção esta não é uma abordagem um tanto aconselhável, e é por isso que vamos conhecer algumas outras configurações de segurança.

## Em application properties

O Spring Security verifica se existe alguma configuração de segurança no arquivo **Application.properties.**

_Exemplo:_
**spring.security.user.name=user**
**spring.security.user.password=user123**
**spring.security.user.roles=USERS**

## Em memória

Esta configuração permite criar mais de um usuário e perfis de acesso.
é necessário criar uma classe que estenda _WebSecurityConfigurerAdapter_ conforme abaixo:


