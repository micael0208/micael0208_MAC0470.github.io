---
title: "Tutorial 3 - Módulos de kernel e configuração de build"
date: 2026-03-11
---

# Tutorial 3 - Módulos de kernel e configuração de build

## Objetivo

Aprender a:

- criar e compilar módulos de kernel
- integrar novos componentes ao build do kernel
- carregar, testar e remover módulos em tempo de execução

---

## Contexto

Após compilar e executar um kernel customizado (tutorial 2), o próximo passo foi interagir diretamente com ele.

Aqui entra o conceito de **módulos de kernel (.ko)**:

- código que pode ser carregado e descarregado dinamicamente;
- sem necessidade de recompilar todo o kernel

---

## O que fiz

Comecei explorando a configuração do kernel com `menuconfig`, entendendo como habilitar ou desabilitar funcionalidades.

Depois, trabalhei na criação de módulos simples dentro da árvore do kernel, adicionando:

- arquivos `.c` com a implementação
- entradas em `Kconfig` e `Makefile`

Com isso, consegui integrar os módulos ao sistema de build do kernel.

Para compilação, usei dois fluxos:

- build completo (kernel + módulos)
- build parcial com `M=<diretório>` para compilar apenas meu código

Isso acelerou bastante os testes.

Após compilar, passei a manipular os módulos diretamente na VM:

- carregando com `insmod` e `modprobe`
- removendo com `rmmod`
- verificando informações com `modinfo`

Também usei `dmesg` para observar logs do kernel, o que foi essencial para validar o comportamento dos módulos.

---

## O que aprendi

- Módulos permitem desenvolvimento incremental no kernel
- `Kconfig` e `Makefile` são fundamentais para integrar código ao build
- `modprobe` gerencia dependências automaticamente
- `dmesg` é a principal ferramenta de debug no kernel

---

## Ferramentas utilizadas

- `make M=<dir>` → compila apenas um módulo
- `insmod` / `rmmod` → controle manual de módulos
- `modprobe` → controle com resolução de dependências
- `modinfo` → inspeção de módulos
- `dmesg` → logs do kernel

