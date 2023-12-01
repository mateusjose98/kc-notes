# Anotações sobre a ferramenta Keycloak

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


Vamos ver no banco se o usuário está persistido com o comando
``` 
docker compose exec db bash
mysql -uroot -proot
show databases;use keycloak; select* from user_entity;
```