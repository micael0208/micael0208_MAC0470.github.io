---
title: "Tutorial 5 - Enviando patches por email com git"
date: 2026-03-25
---

# Tutorial 5 - Enviando patches por email com git

## Objetivo

Aprender a enviar contribuições (patches) usando `git send-email`, seguindo o workflow tradicional do kernel Linux.

---

## Contexto

Diferente de plataformas como GitHub ou GitLab, o desenvolvimento do kernel Linux acontece via **listas de email**.

- patches são enviados por email;
- discussões acontecem por threads; 
- não existe “pull request”

---

## O que fiz

Primeiro configurei o Git com minhas informações e servidor SMTP. Com isso pronto, usei o próprio Git para enviar patches

## Observação

Esse tutorial foi mais conceitual, mas aprendi que o kernel usa email como principal meio de colaboração, que cada commit vira um patch e que patchsets permitem enviar múltiplas mudanças organizadas.
