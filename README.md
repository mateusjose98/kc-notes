# Anotações sobre a ferramenta Keycloak

## Keep the basics

## OAuth 2.0

OAuth 2.0 é um protocolo de autorização amplamente utilizado na web para conceder acesso a recursos protegidos, sem a necessidade de compartilhar credenciais sensíveis, como senhas. Ele foi projetado para facilitar a integração segura entre diferentes aplicativos e serviços. O processo básico do OAuth 2.0 envolve três atores principais: o proprietário do recurso (usuário, resource owner), o cliente (aplicativo solicitante, client) e o servidor de autorização (auth server). O usuário concede permissões ao cliente para acessar seus recursos no servidor de autorização, que emite um token de acesso. Esse token é então enviado pelo cliente ao servidor de recursos para obter acesso aos dados protegidos.

Durante a autenticação, o cliente obtém um código de autorização do servidor de autorização após o usuário efetuar login e conceder permissões. Esse código é então trocado por um token de acesso. O OAuth 2.0 suporta diferentes fluxos de concessão, como o fluxo de autorização implícita, o fluxo de autorização de código e o fluxo de concessão de senha do proprietário. Cada um atende a diferentes cenários de uso, proporcionando flexibilidade na implementação. Além disso, o OAuth 2.0 não especifica o formato do token, permitindo a utilização de JSON Web Tokens (JWT) ou outros formatos, dependendo dos requisitos de segurança e implementação.

A principal vantagem do OAuth 2.0 é a capacidade de delegar permissões de acesso limitadas, sem a necessidade de compartilhar credenciais sensíveis. Isso melhora a segurança e a experiência do usuário, ao mesmo tempo em que facilita a integração entre serviços.

##  OpenID Connect (OIDC)
O OpenID Connect (OIDC) é uma extensão do OAuth 2.0 e fornece uma camada de autenticação para o protocolo de autorização. Enquanto o OAuth 2.0 é focado na autorização e no acesso a recursos protegidos, o OpenID Connect visa fornecer um método padronizado para autenticar usuários, permitindo que clientes obtenham informações sobre a identidade do usuário autenticado. Em essência, o OpenID Connect adiciona uma camada de identidade ao OAuth 2.0.

No contexto do OpenID Connect, os três principais participantes (atores) são o usuário (proprietário do recurso), o cliente (aplicativo solicitante) e o provedor de identidade (servidor de autorização que suporta OIDC). O fluxo típico envolve o cliente autenticando o usuário no provedor de identidade, que então emite um token de ID (ID Token) contendo informações sobre a identidade do usuário, como nome, e-mail e outras informações específicas.

A relação entre o OAuth 2.0 e o OpenID Connect reside na maneira como esses protocolos podem ser usados em conjunto. O OpenID Connect é construído sobre o OAuth 2.0 e estende seus recursos para fornecer autenticação, enquanto ainda utiliza os conceitos de tokens de acesso do OAuth 2.0 para autorização. Isso significa que, ao utilizar o OpenID Connect, você também obtém os benefícios de autorização do OAuth 2.0, como a capacidade de conceder permissões específicas para acessar recursos protegidos.

Em resumo, o OpenID Connect aprimora o OAuth 2.0, proporcionando autenticação e informações de identidade, tornando-o uma escolha comum para implementações que exigem tanto autorização quanto autenticação em um único fluxo de interação com o usuário.

## O que é o Keycloak?

Patrocinado pela Red Hat, o Keycloak é um software open source de um servidor JBoss feito para trabalhar em conjunto com sua aplicação em implementações mais comuns de autenticação e de autorização. Links importantes:
(1) https://www.keycloak.org/
(2) https://quay.io/repository/keycloak/keycloak

Ao rodar o docker compose, se tudo deu certo, estaremos com um keycloak rodando e conectado a uma base mysql! Acessando a porta 8888 veremos a interface inicial do nosso keycloak:
![Alt text](image.png)
Após login:
![Alt text](image-1.png)

Crie um usuário na interface
![Alt text](image-2.png)

Vamos ver no banco se o usuário está persistido:
Entre no bash do container "db"

```
docker compose exec db bash
```

Entrando no mysql

```
mysql -uroot -proot
```

Buscando os usuários atualmente cadastrados na base

```
use keycloak; select * from user_entity;
```
