# Visión general

Este proyecto corresponde a un **Pharmaceutical Order Tracking System**, desarrollado para gestionar y visualizar en tiempo real los pedidos entre una **obra social** y **tres droguerías**.

El sistema se divide en **roles de usuario** (administradores, farmacias, droguerías, obra social), cada uno con acceso restringido al contenido que le corresponde.

---

## Arquitectura general

```mermaid
flowchart TD
    subgraph Frontend [Frontend - React + TS]
        A1[Router / Store / Assets]
        A2[Core - Auth, Hooks, UI]
        A3[Features]
        A4[Shared Components]
        A3 --> F1[Dashboard]
        A3 --> F2[Tracking]
        A3 --> F3[Login]
        A3 --> F4[Liquidacion]
    end

    subgraph Backend [Backend / Integración]
        B1[(SAP HANA)]
        B2[(PostgreSQL)]
        B3[(Firebase Auth)]
    end

    subgraph Infra [Infraestructura]
        C1[Vite Config]
        C2[Playwright Tests]
    end

    Frontend -->|RTK Query / API REST| Backend
    A2 --> B3
    A3 --> B1
    A3 --> B2
    Frontend --> Infra
