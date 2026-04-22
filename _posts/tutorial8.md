---
title: "Tutorial 8 - Experimento com iio_dummy"
date: 2026-04-01
---

# 🧪 Tutorial 8 - Experimento com iio_dummy

## 🎯 Objetivo

Explorar na prática o driver `iio_dummy`, entendendo como o user space interage com dispositivos do subsistema IIO.

---

## 🧠 Contexto

Após estudar a estrutura interna do `iio_simple_dummy`, o próximo passo foi utilizá-lo na prática.

👉 carregar o driver  
👉 inspecionar dispositivos  
👉 interagir via sysfs  

---

## ⚙️ O que fiz

Comecei compilando o módulo, instaleio-o e o carreguei.
Com o módulo ativo, fiz verificação do seu estado.
Depois, fiz exploração do dispositivo. Os dispositivos IIO aparecem em /sys/bus/iio/devices/.
Cada device expõe atributos como arquivos. A leitura desses arquivos equivale a leitura de dados do sensor. Enquanto a escrita equivale à configuração do dispositivo.
Para criar dispositivos dinamicamente, usei configfs. Criei um dispositivo dummy, o que instancia novo dispositivo IIO no sistema.

## O que aprendi

- Dispositivos IIO são expostos via sysfs;
- Interação com sensores pode ser feita diretamente por arquivos;
- configfs permite criar dispositivos dinamicamente;
- O iio_dummy é útil para testar sem hardware real.
