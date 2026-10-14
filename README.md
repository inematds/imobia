# imobia — imobiliária no automático

[![imobia](guia/assets/banner.jpg)](https://inematds.github.io/imobia/guia/)

**🇧🇷 [Português](README.md) · 🇺🇸 [English](README.en.md) · 🇪🇸 [Español](README.es.md)**

> **Status:** proposta em discussão. O sistema ainda não foi construído.

## O que é

O imobia é o plano de um sistema próprio de atendimento para uma imobiliária de venda e locação com 5 corretores. O cliente manda mensagem no WhatsApp e uma inteligência artificial responde na hora, entende o que ele procura e mostra só imóveis que existem no cadastro. Quando chega a hora de visitar ou negociar, a conversa passa para o corretor, que responde pelo Telegram. Não tem formulário para preencher: o que pode ser automático, é.

## 📖 Página do projeto

Landing com o plano: **https://inematds.github.io/imobia/guia/**

## Documentos

- [`docs/plano-arquitetura.md`](docs/plano-arquitetura.md): arquitetura proposta, componentes, dados, riscos e fases.
- [`docs/discussao-2026-10-13.md`](docs/discussao-2026-10-13.md): registro da conversa que originou o projeto.
- [`docs/pesquisa-2026-10-13.md`](docs/pesquisa-2026-10-13.md): referências analisadas (imob360, wacrm, EspoCRM, Chatwoot, Twenty, Evolution API).

## Resumo da arquitetura

```
Cliente (WhatsApp) → Evolution API → App imobia (IA + match + agenda) → Postgres
                                          ↓
                         Bot do Telegram (equipe) · Painel web (só leitura)
```

## Decisão em aberto

Como a equipe usa o Telegram: **A)** um tópico por cliente num grupo (recomendado), **B)** privado por corretor, **C)** misto.

---
[INEMA.CLUB](https://inema.club)
