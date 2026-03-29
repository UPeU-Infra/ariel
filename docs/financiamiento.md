# Financiamiento

## Mapa completo de fuentes de financiamiento para ARIEL

---

## Visión general del pipeline

```mermaid
graph TD
    subgraph inmediato["Inmediato — Semilla (2026)"]
        MIF["🙏 WillPlan Mission Impact Fund\nGC-IASD\nS/ 30K–100K USD\nDeadline: 1 mayo 2027"]
        SAD_FUND["✝️ División Sudamericana\nFondo propio de TI/Educación\nPor confirmar monto"]
        UPeU_FUND["🏛️ UPeU\nPartida presupuestal\nI+D+i institucional"]
    end

    subgraph corto["Corto plazo (2026–2027)"]
        IOI["🌐 IOI Fund for Network Adoption\nInvest in Open Infrastructure\nHasta USD 1.5M\nPróxima conv. 2026–2027"]
        MELLON["📚 Mellon Foundation\nHigher Learning Program\nUSD 250K–500K\nCiclo 2027"]
    end

    subgraph sostenibilidad["Sostenibilidad (2028+)"]
        SCOSS["♻️ SCOSS\nGlobal Sustainability Coalition\nFinanciamiento recurrente"]
        MEMBRESIA["💳 Modelo membresía\nAporte por nodo participante\n~USD 500–2,000/año por institución"]
    end

    subgraph piloto["ARIEL Piloto SAD"]
        P["⭐ Prototipo funcional\n5–10 universidades"]
    end

    inmediato --> piloto
    corto --> piloto
    piloto --> sostenibilidad

    style inmediato fill:#1a4a1a,color:#fff
    style corto fill:#1e3a5f,color:#fff
    style sostenibilidad fill:#4a1a5a,color:#fff
    style piloto fill:#7a3a00,color:#fff
```

---

## Fuente 1 — WillPlan Mission Impact Fund (GC-IASD)

!!! info "Fondo denominacional adventista"
    Administrado por el departamento de **Planned Giving & Trust Services** de la Conferencia General. Financiado por herencias y legados de miembros adventistas.

| Campo | Detalle |
|---|---|
| **Monto** | USD $30,000 – $100,000 por proyecto |
| **Tipo** | No reembolsable |
| **Deadline** | 1 de mayo de cada año |
| **Solicitante** | Entidad adventista formal (UPeU → SAD → GC) |
| **Estado** | Abierto — ciclo 2027 |
| **Fit** | Alto si se enmarca como herramienta de misión educativa |

**Narrativa para la solicitud:** ARIEL como cumplimiento de Isaías 29:18 — hacer audibles y visibles los "libros" que las universidades adventistas producen. La red convierte la producción académica denominacional en testimonio de la misión educativa adventista ante el mundo.

---

## Fuente 2 — División Sudamericana (SAD)

!!! tip "Socio estratégico y co-financiador"
    La SAD tiene presupuesto propio para proyectos de tecnología educativa y puede co-financiar el piloto directamente, especialmente a través de IATec.

| Campo | Detalle |
|---|---|
| **Monto** | Por confirmar (negociación institucional) |
| **Tipo** | Aporte institucional / partida presupuestal |
| **Solicitante** | UPeU + IATec ante la SAD |
| **Ventaja** | No requiere convocatoria pública — decisión interna |
| **Palanca** | El piloto beneficia directamente a las 13 universidades de la SAD |

---

## Fuente 3 — IOI Fund for Network Adoption

!!! success "El fondo más alineado conceptualmente"
    Invest in Open Infrastructure financió a **LA Referencia** ($1.5M) — que es exactamente el modelo que ARIEL replica pero para la IASD.

| Campo | Detalle |
|---|---|
| **Monto** | Hasta USD $1,500,000 |
| **Tipo** | Grant no reembolsable |
| **Próxima convocatoria** | Estimada 2026–2027 |
| **Solicitante ideal** | UPeU + IATec + SAD como consorcio |
| **Precedente directo** | LA Referencia (América Latina) — ganador del ciclo inaugural |
| **URL** | investinopen.org |

```mermaid
graph LR
    IOI["IOI Fund\nInvest in Open\nInfrastructure"] -->|"Ciclo inaugural\n2025"| LA_REF["LA Referencia\n✅ USD 1.5M"]
    IOI -->|"Próximo ciclo\n2026–2027"| ARIEL["⭐ ARIEL\n(postular)"]

    style IOI fill:#1e3a5f,color:#fff
    style ARIEL fill:#7a3a00,color:#fff,stroke:#f39c12,stroke-width:2px
```

---

## Fuente 4 — Mellon Foundation

| Campo | Detalle |
|---|---|
| **Monto** | USD $250,000 – $500,000 |
| **Tipo** | Grant — Higher Learning Program |
| **Ciclo** | 2027 (2026 cerrado) |
| **Preferencia** | Instituciones académicas formales como solicitantes |
| **Fit** | Moderado — prefieren proyectos con tracción ya demostrada |

---

## Fuente 5 — SCOSS (Sostenibilidad a largo plazo)

| Campo | Detalle |
|---|---|
| **Tipo** | Financiamiento recurrente para infraestructuras OA no comerciales |
| **Requisito** | Infraestructura activa, no comercial, con base de usuarios real |
| **Ciclo actual** | 2025–2027 |
| **Fit** | Alto en Fase 3 — cuando ARIEL tenga 50+ instituciones activas |
| **Precedentes** | LA Referencia, DOAB, OAPEN, PKP, Open Citations |

---

## Modelo de sostenibilidad post-seed

```mermaid
pie title Estructura de ingresos proyectada (madurez)
    "Membresías de instituciones participantes" : 40
    "Subsidio denominacional (SAD / GC)" : 30
    "SciBack — servicios de despliegue de nodos" : 20
    "Grants y fondos OA (SCOSS, IOI)" : 10
```

**Cuota por institución participante (estimación):**

| Tamaño institución | Cuota anual estimada |
|---|---|
| Pequeña (<500 estudiantes) | USD $500 |
| Mediana (500–3,000 estudiantes) | USD $1,000 |
| Grande (>3,000 estudiantes) | USD $2,000 |
| Universidad principal (Andrews, Loma Linda) | USD $5,000 |

Con 50 instituciones activas: ingresos base ~USD $50,000–$100,000/año — suficiente para cubrir operación del hub.

---

## Línea de tiempo de financiamiento

```mermaid
gantt
    title Hoja de ruta de financiamiento ARIEL
    dateFormat  YYYY-MM
    axisFormat  %Y

    section Semilla
    WillPlan MIF — preparar solicitud    :active, 2026-03, 2026-10
    WillPlan MIF — aplicar (deadline 1 mayo 2027) :milestone, 2027-05, 0d
    SAD — negociación institucional      :2026-04, 2026-09

    section Crecimiento
    IOI Fund — preparar concept note     :2026-06, 2026-12
    IOI Fund — postular                  :2026-12, 2027-06
    Mellon Foundation 2027               :2027-01, 2027-08

    section Sostenibilidad
    Modelo membresía — lanzar            :2027-06, 2028-01
    SCOSS — aplicar                      :2028-01, 2028-12
```
