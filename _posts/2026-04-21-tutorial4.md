---
title: "Tutorial 4 - Character Device Drivers"
date: 2026-04-21
---

# Tutorial 4 - Character Device Drivers

## Objetivo

Introduzir o conceito de **character devices** e implementar um driver simples que permite comunicação entre user space e kernel.

---

## Contexto

Depois de trabalhar com módulos no tutorial anterior, o próximo passo foi criar algo que interage diretamente com o sistema.

Character devices são uma das formas mais simples de fazer isso:

- funcionam como arquivos;
- permitem leitura e escrita sequencial; 
- fazem ponte entre user space e kernel

---

## O que fiz

Implementei um driver simples (`simple_char`) com operações básicas:

- `open`
- `read`
- `write`
- `release`

Associei essas operações a um `file_operations` e registrei o device no kernel com um número **major/minor**.

Depois, criei manualmente o nó do dispositivo:

```bash
mknod simple_char_node c <major> 0
chmod 666 simple_char_node
```

Com isso, passei a interagir com o driver como se fosse um arquivo comum:
- escrevendo com echo
- lendo com cat
- testando com programas em C

Usei dmesg para acompanhar o comportamento do driver em tempo real.

## O que aprendi

- Character devices expõem drivers como arquivos em /dev
- Major/minor identificam qual driver atende o device
- file_operations define como o driver responde às syscalls
- copy_to_user e copy_from_user são essenciais para comunicação segura

## Ferramentas usadas

- cat /proc/devices: listar devices registrados
- mknod: criar nó do dispositivo
- stat: verificar major/minor
- dmesg -w: acompanhar logs em tempo real
