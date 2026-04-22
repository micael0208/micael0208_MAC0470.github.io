---
title: "Tutorial 7 - Anatomia do iio_simple_dummy"
date: 2026-04-01
---

# Tutorial 7 - Anatomia do iio_simple_dummy

## Objetivo

Entender a estrutura de um driver do subsistema **IIO (Industrial I/O)** analisando o driver de exemplo `iio_simple_dummy`.

---

## Contexto

O `iio_simple_dummy` é um driver didático usado para:

👉 simular sensores;
👉 demonstrar conceitos do IIO;
👉 servir como referência para novos drivers

A ideia foi estudar sua estrutura para entender como drivers reais são organizados.

---

## O que analisei

Segui uma abordagem simples:

- estrutura dos canais;
- funções de leitura e escrita;
- inicialização do driver (probe)

---

### Canais (`iio_chan_spec`)

Os canais representam os dados do dispositivo.

Exemplos típicos:

- acelerômetro → X, Y, Z;
- sensor de luz → visível / infravermelho; 
- temperatura → valor único

Cada canal é descrito por `struct iio_chan_spec`, que define:

- tipo (`IIO_VOLTAGE`, `IIO_ACCEL`, etc.)
- índice (`channel`, `channel2`)
- atributos disponíveis (`raw`, `scale`, `offset`)
- suporte a buffer (`scan_index`, `scan_type`)

obs: isso define como os dados aparecem para o user space

---

### Leitura (`read_raw`)

A função `iio_dummy_read_raw()`:

- identifica o que deve ser lido via `mask`
- usa o tipo do canal (`chan->type`)
- retorna valores do estado interno do driver

obs: é o caminho principal de dados: kernel → user

---

### Escrita (`write_raw`)

A função `iio_dummy_write_raw()`:

- recebe dados do user space  
- atualiza o estado interno (`iio_dummy_state`)  
- usa locking quando necessário  

obs: permite configurar ou simular valores do dispositivo

---

### Inicialização (`probe`)

A função `probe` conecta tudo:

- aloca estrutura do dispositivo (`iio_dev`)
- inicializa estado interno
- define canais e operações
- registra o device no kernel

obs: é o ponto onde o driver “entra em funcionamento”

---

## O que aprendi

- O IIO é altamente configurável via `iio_chan_spec`
- Channels são a base de tudo no subsistema
- `read_raw` e `write_raw` definem a interface com user space
- `probe` organiza e registra o dispositivo

