---
title: "Tutorial 2 - Build e boot de kernel ARM com kw"
date: 2026-03-04
---

# Tutorial 2 - Compilando e bootando um kernel ARM com kw

## Objetivo

Compilar um kernel Linux para ARM64 e executá-lo na máquina virtual, utilizando o **kworkflow (kw)** para organizar e automatizar o processo.

---

## Contexto

Dando continuidade ao setup do ambiente (tutorial 1), o foco aqui foi:

- obter o código do kernel (IIO tree)
- configurar o build para ARM64
- compilar o kernel
- preparar o ambiente para testes na VM

---

## O que fiz

Comecei instalando o `kworkflow (kw)`, que será a principal ferramenta para gerenciar builds, configurações e deploys ao longo dos tutoriais.

Em seguida, clonei a árvore do subsistema IIO em uma branch ativa de desenvolvimento. Isso garante um ambiente mais próximo do que é usado na prática.

Com o código em mãos, inicializei e configurei o `kw`, definindo:

- arquitetura alvo (`arm64`)
- cross-compiler (`aarch64-linux-gnu-`)
- conexão com a VM via SSH

Depois, gerei um arquivo `.config` enxuto:

- usei `defconfig` como base
- atualizei com `olddefconfig`
- refinei com `localmodconfig`, baseado nos módulos da VM

Isso resultou em uma configuração mais leve e adequada ao ambiente de teste.

Utilizei também o `kw build --menu` para revisar opções via menuconfig.

Por fim, compilei o kernel com `kw build` e instalei os módulos na VM com `kw deploy --modules`.

---

## O que aprendi

- O processo de build do kernel depende fortemente da configuração (`.config`)
- Cross-compilation é essencial para trabalhar com arquiteturas diferentes
- O `kw` simplifica bastante tarefas repetitivas do workflow
- É possível gerar um kernel mais enxuto usando `localmodconfig`

