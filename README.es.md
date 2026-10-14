# imobia — inmobiliaria en automático

[![imobia](guia/assets/banner-es.jpg)](https://inematds.github.io/imobia/guia/es/)

**🇧🇷 [Português](README.md) · 🇺🇸 [English](README.en.md) · 🇪🇸 [Español](README.es.md)**

> **Estado:** propuesta en discusión. El sistema todavía no fue construido.

## Qué es

imobia es el plan de un sistema propio de atención para una inmobiliaria de venta y alquiler con 5 corredores. El cliente escribe por WhatsApp y una inteligencia artificial responde al instante, entiende lo que busca y muestra solo inmuebles que existen en el catálogo. Cuando llega el momento de visitar o negociar, la conversación pasa al corredor, que responde por Telegram. No hay formularios para llenar: lo que puede ser automático, lo es.

## 📖 Página del proyecto

Landing con el plan: **https://inematds.github.io/imobia/guia/es/**

## Documentos (en portugués)

- [`docs/plano-arquitetura.md`](docs/plano-arquitetura.md): arquitectura propuesta, componentes, datos, riesgos y fases.
- [`docs/discussao-2026-10-13.md`](docs/discussao-2026-10-13.md): registro de la conversación que originó el proyecto.
- [`docs/pesquisa-2026-10-13.md`](docs/pesquisa-2026-10-13.md): referencias analizadas (imob360, wacrm, EspoCRM, Chatwoot, Twenty, Evolution API).

## Arquitectura en resumen

```
Cliente (WhatsApp) → Evolution API → App imobia (IA + match + agenda) → Postgres
                                          ↓
                         Bot de Telegram (equipo) · Panel web (solo lectura)
```

## Decisión abierta

Cómo usa el equipo Telegram: **A)** un tema por cliente en un grupo (recomendado), **B)** privado por corredor, **C)** mixto.

---
[INEMA.CLUB](https://inema.club)
