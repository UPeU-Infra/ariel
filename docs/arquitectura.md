# Arquitectura Técnica

## Stack tecnológico recomendado por fase

---

### Visión general

```mermaid
graph TD
    subgraph nodos["Nodos (cada universidad)"]
        DS["DSpace 7.x\nRepositorio institucional"]
        OJ["OJS 3.x\nRevistas académicas"]
        CR["DSpace-CRIS\n(Fase 3)"]
    end

    subgraph protocolo["Protocolo de interoperabilidad"]
        OAI["OAI-PMH\n+ OpenAIRE Guidelines v4"]
    end

    subgraph hub["HUB ARIEL — ariel.network"]
        HARV["Harvester\n(pyoaiharvest / InvenioRDM)"]
        IDX["Índice unificado\n(OpenSearch)"]
        API["API REST\n(FastAPI)"]
        WEB["Portal web\n(InvenioRDM / Vue 3)"]
    end

    subgraph upstream["Red global"]
        LA["LA Referencia"]
        OA["OpenAIRE"]
        OAL["OpenAlex"]
        BASE["BASE · CORE · Google Scholar"]
    end

    nodos --> OAI
    OAI --> HARV
    HARV --> IDX
    IDX --> API
    API --> WEB
    IDX --> upstream

    style hub fill:#1e3a5f,color:#fff
    style nodos fill:#1a4a2a,color:#fff
    style upstream fill:#4a1a5a,color:#fff
```

---

## Fase 1 — Piloto SAD (2026)

### Tecnología recomendada: InvenioRDM

```mermaid
flowchart LR
    subgraph infra["Infraestructura (AWS)"]
        EC2["EC2 t3.xlarge\nInvenioRDM + OpenSearch"]
        S3["S3\nAssets y backups"]
        RDS["PostgreSQL\n(Docker o RDS)"]
    end

    subgraph invenio["InvenioRDM"]
        UI["Portal bilingüe\nES / EN"]
        Search["Búsqueda facetada\nrápida"]
        OAI2["Endpoint OAI-PMH\npropio"]
        Profiles["Perfiles de autor\ne institución"]
    end

    subgraph harvest["Harvesting"]
        H1["DSpace UPeU"]
        H2["DSpace Montemorelos"]
        H3["OJS SAD instituciones"]
        H4["Más nodos..."]
    end

    H1 & H2 & H3 & H4 -->|OAI-PMH| invenio
    invenio --- infra

    style infra fill:#1a3a1a,color:#fff
    style invenio fill:#1e3a5f,color:#fff
    style harvest fill:#3a1a1a,color:#fff
```

**Razón de elección — InvenioRDM:**

| Criterio | Detalle |
|---|---|
| Desarrollador | CERN — usado por Zenodo, TU Graz, KTH |
| UI | Moderna, similar a OpenAlex en limpieza |
| Harvesting | OAI-PMH nativo incorporado |
| Deploy | Docker Compose — stack conocido |
| CERIF | Extensible — mapeado Dublin Core → DataCite |
| Costo | Open source (MIT) |

---

## Fase 2 — SAD completa + IAD (2027)

### Upgrade a Hub DSpace-CRIS

```mermaid
flowchart TD
    subgraph nodos_sad["SAD — 13 instituciones"]
        N1["UPeU 🇵🇪"]
        N2["UNASP 🇧🇷"]
        N3["UAP 🇦🇷"]
        N4["UAB 🇧🇴"]
        N5["UNACP 🇨🇴"]
        N6["Más..."]
    end

    subgraph nodos_iad["IAD — 13 instituciones"]
        M1["Montemorelos 🇲🇽"]
        M2["UNAC 🇨🇴"]
        M3["Más..."]
    end

    HUB["⭐ HUB ARIEL\nDSpace-CRIS central\n(cuando DSpace 10 madure)"]

    nodos_sad -->|OAI-PMH + CERIF| HUB
    nodos_iad -->|OAI-PMH + CERIF| HUB

    HUB --> LA_REF["LA Referencia"]
    HUB --> OPENDOAR["OpenDOAR\n(red registrada)"]

    style HUB fill:#1e3a5f,color:#fff,stroke:#f39c12,stroke-width:3px
```

**¿Por qué migrar a DSpace-CRIS en Fase 2?**

Cuando DSpace 10 fusione el core con DSpace-CRIS (4Science), cada nodo expondrá entidades CRIS completas: `Researcher → Project → Publication → Organization → Funding`. El hub adventista puede entonces construir el **grafo de conocimiento adventista**: quién investiga qué, con qué fondos, en qué institución, con qué impacto.

---

## Fase 3 — Escala global (2028+)

### OpenAIRE Graph como infraestructura base

```mermaid
graph TD
    subgraph divisiones["Todas las divisiones IASD"]
        SAD["SAD 🌎 Sudamérica"]
        IAD["IAD 🌎 Centroamérica"]
        NAD["NAD 🇺🇸 Norteamérica"]
        ECD["ECD 🌍 África Oriental"]
        SSD["SSD 🌏 Asia Pacífico Sur"]
        EUD["EUD 🇪🇺 Europa"]
        OTROS["+ 7 divisiones"]
    end

    HUB_GLOBAL["⭐ ARIEL Global Hub\nOpenAIRE Graph stack\nCERIF nativo"]

    divisiones --> HUB_GLOBAL

    HUB_GLOBAL --> OpenAIRE["OpenAIRE\n193M publicaciones europeas"]
    HUB_GLOBAL --> LA_REF["LA Referencia\n5M registros LATAM"]
    HUB_GLOBAL --> OpenAlex["OpenAlex\nGrafo global"]

    style HUB_GLOBAL fill:#1e3a5f,color:#fff,stroke:#f39c12,stroke-width:3px
    style divisiones fill:#1a3a4a,color:#fff
```

---

## Schema de metadatos: compatibilidad simultánea

```mermaid
graph LR
    CERIF["CERIF\n(DSpace-CRIS)"] --> OAGV4["OpenAIRE\nGuidelines v4\n✅ Compatible"]
    DC["Dublin Core\n(DSpace básico)"] --> OAGV4
    DataCite["DataCite 4.x\n(InvenioRDM)"] --> OAGV4

    OAGV4 --> ALICIA["ALICIA 🇵🇪\n✅"]
    OAGV4 --> BDTD["BDTD 🇧🇷\n✅"]
    OAGV4 --> SNRD["SNRD 🇦🇷\n✅"]
    OAGV4 --> RRAAE["RRAAE 🇪🇨\n✅"]
    OAGV4 --> BASE_idx["BASE · CORE\n· OpenAlex ✅"]

    style OAGV4 fill:#1e3a5f,color:#fff,stroke:#f39c12,stroke-width:2px
```

**El schema unificador es OpenAIRE Guidelines v4** — permite cumplir con todos los reguladores nacionales simultáneamente con mappings por país mínimos.

---

## Requisitos por nodo (cada universidad)

Para integrarse a ARIEL, una universidad adventista necesita:

- [x] **Repositorio activo** — DSpace 7.x recomendado
- [x] **OAI-PMH habilitado** — configuración por defecto en DSpace
- [x] **Subdominio propio** — `repositorio.universidad.edu.xx`
- [x] **Metadatos mínimos** — Dublin Core + OpenAIRE Guidelines v4
- [ ] **Registro en OpenDOAR** — proceso simple, voluntario
- [ ] **Acuerdo de participación ARIEL** — gobernanza y licencias

SciBack provee el despliegue y mantenimiento de cada nodo como servicio gestionado.
