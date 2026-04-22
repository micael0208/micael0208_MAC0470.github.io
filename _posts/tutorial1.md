---
title: "Tutorial 1 - Setup do ambiente com QEMU + libvirt"
date: 2026-02-25
---

# Tutorial 1 - Setup do ambiente de desenvolvimento do Kernel

## Objetivo

Configurar um ambiente seguro para desenvolvimento do kernel Linux utilizando máquinas virtuais ARM64 com QEMU + libvirt.

A ideia é **não mexer no sistema host diretamente**, evitando quebrar o sistema enquanto testamos kernels customizados.

---

## Contexto

Esse é o primeiro de uma série de tutoriais focados em desenvolvimento no kernel, usando o subsistema **IIO (Industrial I/O)** como base prática.

A proposta é:

- compilar kernels
- testar módulos
- iterar rápido
- sem medo de quebrar tudo

---

## O que fiz

Comecei criando o ambiente base. A ideia aqui era ter um diretório controlado pelo `libvirt`, então criei o `/home/lk_dev` e ajustei as permissões. Confesso que essa parte pareceu meio burocrática no começo, mas depois ficou claro que sem isso a VM simplesmente não consegue acessar nada.

Depois segui pra manipulação da imagem da VM. Usei algumas ferramentas do `libguestfs`, que no início são bem pouco intuitivas. Tive que entender melhor como inspecionar a imagem e descobrir qual partição era o `rootfs` antes de conseguir expandir o disco corretamente.

Com a imagem pronta, extraí o kernel e o initrd da VM. Isso pareceu um detalhe pequeno, mas foi essencial pois, mais pra frente, vamos bootar a máquina com kernels modificados, então já era importante entender onde essas coisas vivem.

Por fim, comecei a gerenciar a VM com o `virsh`. Foi aqui que as coisas começaram a ficar mais concretas: subir a VM, acessar via console e depois via SSH. Nesse ponto já dá pra sentir que o ambiente está funcionando de verdade.
