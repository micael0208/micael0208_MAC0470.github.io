---
title: "Tutorial 6 - Enviando patches com email USP (OAuth)"
date: 2026-03-25
---

# Tutorial 6 - Enviando patches com email USP (OAuth)

## Objetivo

Configurar o envio de patches com `git send-email` usando um email USP, utilizando OAuth 2.0 para autenticação.

---

## Contexto

Ao utilizar contas USP (baseadas em Gmail), a autenticação tradicional via SMTP não é suportada:

- App Password não está disponível;
- “Less Secure Apps” foi desativado

Para contornar isso, utilizamos **OAuth 2.0**, que permite autenticação segura sem uso de senha direta.

---

## O que fiz

O tutorial apresenta duas abordagens complementares para lidar com OAuth.

---

### Opção A — Credential helper

Configurei um helper de credenciais para integrar o OAuth ao `git send-email`.

O processo consistiu em:

- configurar cliente OAuth (client ID e secret);
- autenticar via navegador;
- gerar e armazenar o token de acesso

Depois disso, configurei o Git para usar OAuth. Assim, o envio de patches passou a funcionar diretamente com git send-email

### Opção B - Email proxy

Como alternativa, configurei um proxy SMTP com suporte a OAuth.

Segui o fluxo:
- configurar o emailproxy.config com email e credenciais OAuth;
- subir o container com Docker;
- iniciar o proxy SMTP local

Depois, configurei o kw send-patch para usar o proxy.

Nesse modelo, o Git envia o email localmente e o proxy realiza a autenticação OAuth com o Gmail.

## Teste

COm ambas as configurações funcionando, enviei um patch simples.

## O que aprendi

- OAuth é essencial para integração com serviços modernos;
- git send-email pode ser estendido via helpers ou proxies
- Separar autenticação do envio torna o sistema mais flexível;
- kw send-patch simplifica a preparação e envio de patches.
