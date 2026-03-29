# Propuesta Ejecutiva

## ARIEL — Adventist Repository for Institutional and Educational Literature

**Versión:** 1.0 — Marzo 2026
**Institución proponente:** Universidad Peruana Unión (UPeU)
**Socios estratégicos:** IATec · División Sudamericana (SAD)
**Alcance inicial:** División Sudamericana → expansión global

---

## 1. El fundamento: Isaías 29:18

!!! quote "El nombre del proyecto"
    En hebreo bíblico, **Ariel** (אֲרִיאֵל) aparece 6 veces en el Antiguo Testamento con significados que convergen: "León de Dios", "Altar/Hogar de Dios", nombre simbólico de Jerusalén. En Isaías 29, el capítulo termina con esta promesa:

    > *"En aquel día los sordos oirán las palabras del libro, y los ojos de los ciegos verán desde la oscuridad y las tinieblas."* — Isaías 29:18

    El instrumento de restauración en ese capítulo es explícitamente **el libro** — el conocimiento hecho accesible. ARIEL es ese libro hecho red.

---

## 2. El problema

### 2.1 Una escala sin infraestructura

```mermaid
graph LR
    subgraph sistema["Sistema Educativo Adventista"]
        direction TB
        U["118+ universidades\n50+ países"]
        E["163,312 estudiantes"]
        D["14,206 docentes"]
        P["5K–15K publicaciones/año"]
    end

    subgraph brecha["Brecha Actual"]
        direction TB
        R["< 6 repositorios\noperativos (~5%)"]
        F["Cero red federada"]
        I["Producción invisible\nen índices globales"]
        M["Sin política OA\ndenominacional"]
    end

    sistema --> brecha

    style sistema fill:#1a4a7a,color:#fff
    style brecha fill:#7b1a1a,color:#fff
```

### 2.2 La dependencia de una sola institución

Actualmente, **10 de los 20 principales usuarios** del repositorio de Andrews University son otras universidades adventistas. El resto del sistema no tiene infraestructura propia y usa Andrews como proxy.

!!! danger "Riesgo sistémico"
    Si Andrews University cambia su política o plataforma, la visibilidad de toda la producción científica adventista global colapsa. La producción de África, Asia y Latinoamérica — en español, portugués, francés, swahili, bahasa — no tiene plataforma propia.

### 2.3 Comparación con redes equivalentes

```mermaid
xychart-beta
    title "Cobertura de redes de repositorios"
    x-axis ["OpenAIRE", "LA Referencia", "CRRA Católica", "BETH Teológica", "Red Adventista hoy"]
    y-axis "Instituciones cubiertas" 0 --> 2500
    bar [2209, 100, 50, 1500, 6]
```

---

## 3. La solución: ARIEL

### 3.1 Definición

**ARIEL** es una plataforma de agregación y descubrimiento de la producción científica de las universidades e institutos de la Iglesia Adventista del Séptimo Día, operando como hub federado interoperable con las principales redes académicas globales.

### 3.2 Plataformas que ARIEL agrega

```mermaid
graph TD
    HUB["⭐ HUB ARIEL\nariel.network"]

    DSpace["📚 DSpace\nRepositorios institucionales\nTesis · Artículos · Reportes"]
    OJS["📰 OJS\nRevistas académicas\nadventistas"]
    GLAM["🏛️ DSpace GLAM\nColecciones patrimoniales\nMuseos · Archivos"]
    CRIS["🔬 DSpace-CRIS\nInvestigadores · Proyectos\nFinanciamiento (Fase 3)"]
    Indico["📅 Indico\nActas de congresos\n(Fase 2)"]

    DSpace -->|OAI-PMH nativo| HUB
    OJS -->|OAI-PMH nativo| HUB
    GLAM -->|OAI-PMH nativo| HUB
    CRIS -->|OAI-PMH + CERIF| HUB
    Indico -->|API REST| HUB

    style HUB fill:#1e3a5f,color:#fff,stroke:#f39c12,stroke-width:3px
    style DSpace fill:#2980b9,color:#fff
    style OJS fill:#27ae60,color:#fff
    style GLAM fill:#8e44ad,color:#fff
    style CRIS fill:#d35400,color:#fff
    style Indico fill:#7f8c8d,color:#fff
```

!!! info "¿Qué no entra en ARIEL?"
    **Koha** (catálogo de biblioteca física) queda fuera del alcance. ARIEL agrega *producción científica* — lo que los investigadores crean. Koha gestiona lo que las bibliotecas compran o suscriben. Son capas distintas del ecosistema.

---

## 4. Arquitectura de expansión

```mermaid
graph TD
    subgraph fase1["Fase 1 — Piloto SAD (2026)"]
        SAD_UPeU["UPeU — Perú\n✅ DSpace activo"]
        SAD_UNASP["UNASP — Brasil\n(3 campus)"]
        SAD_UAP["UAP — Argentina"]
        SAD_UAB["UAB — Bolivia"]
        SAD_UNAD["UNAD — Colombia"]
    end

    subgraph fase2["Fase 2 — SAD completa + IAD (2027)"]
        IAD["División Interamericana\n13 instituciones"]
        SAD_resto["SAD completa\n13 instituciones"]
    end

    subgraph fase3["Fase 3 — Global (2028+)"]
        NAD["NAD — Norteamérica"]
        ECD["ECD — África Oriental"]
        SSD["SSD — Asia Pacífico Sur"]
        Resto["Otras 6 divisiones"]
    end

    HUB["⭐ HUB ARIEL"]

    fase1 --> HUB
    fase2 --> HUB
    fase3 --> HUB

    HUB --> LA_REF["LA Referencia"]
    HUB --> OpenAIRE["OpenAIRE"]
    HUB --> OpenAlex["OpenAlex"]

    style HUB fill:#1e3a5f,color:#fff,stroke:#f39c12,stroke-width:3px
    style fase1 fill:#1a4a1a,color:#fff
    style fase2 fill:#1a3a5a,color:#fff
    style fase3 fill:#4a1a5a,color:#fff
```

---

## 5. Los 7 argumentos que justifican ARIEL

=== "Escala"
    **118+ universidades en 50+ países** con 163,312 estudiantes y 14,206 docentes constituyen el segundo sistema educativo privado mundial. No existe infraestructura digital que integre su producción científica.

=== "Brecha"
    Solo **~6 instituciones** tienen repositorios identificables sobre un universo de 118+. Tasa de adopción **menor al 5%**, muy inferior al promedio global.

=== "Invisibilidad"
    Entre **5,000 y 15,000 publicaciones académicas anuales** en el sistema adventista son inaccesibles para Scopus, WoS, OpenAlex y otros investigadores adventistas.

=== "Modelos validados"
    OpenAIRE (193M registros), LA Referencia (5M registros), CRRA/Atla y BETH demuestran que las **redes federadas denominacionales son técnicamente factibles** y generan valor medible.

=== "Presión regulatoria"
    Perú (Ley 30035), Colombia (Resolución 0777/2022), Brasil (CAPES OA) obligan a repositorios interoperables. ARIEL permite cumplir la normativa nacional **y** estar conectadas globalmente en un solo movimiento.

=== "Oportunidad denominacional"
    La Conferencia General **no tiene política de acceso abierto**. ARIEL puede ser el catalizador para la primera política formal adventista, alineada con las Declaraciones de Budapest, Berlín y Bethesda.

=== "Rankings"
    Webometrics Transparent Ranking mide repositorios directamente. Sin infraestructura federada, las universidades adventistas están en **desventaja competitiva documentada** en QS, THE y Scimago.

---

## 6. Actores y roles

```mermaid
graph TD
    subgraph promotor["Institución Promotora"]
        UPeU["🏛️ Universidad Peruana Unión\nUPeU — Lima, Perú\nLíder institucional del proyecto"]
    end

    subgraph tecnologia["Socio Tecnológico"]
        IATec["⚙️ IATec\nInstituto Adventista de Tecnología\nBrazo tech oficial SAD\n40+ países"]
    end

    subgraph denominacional["Respaldo Denominacional"]
        SAD["✝️ División Sudamericana\nEndorsement institucional\nCanal hacia GC"]
    end

    subgraph operador["Operador Técnico"]
        SciBack["🛠️ SciBack\nDespliegue y mantenimiento\ndel hub ARIEL"]
    end

    subgraph universidades["Nodos de Contenido"]
        U1["Universidades SAD"]
        U2["Universidades IAD"]
        U3["Otras divisiones"]
    end

    promotor --> denominacional
    promotor --> tecnologia
    tecnologia --> operador
    denominacional --> universidades
    universidades --> HUB["⭐ HUB ARIEL"]
    operador --> HUB

    style promotor fill:#1e3a5f,color:#fff
    style tecnologia fill:#1a4a2a,color:#fff
    style denominacional fill:#4a1a1a,color:#fff
    style operador fill:#4a3a1a,color:#fff
    style HUB fill:#1e3a5f,color:#fff,stroke:#f39c12,stroke-width:3px
```

---

## 7. Próximos pasos inmediatos

- [x] Nombre y dominio objetivo: **ariel.network**
- [x] Revisión de literatura — brecha documentada
- [x] Arquitectura técnica definida
- [ ] Reunión con DTI UPeU — presentar propuesta
- [ ] Reunión con IATec — confirmar rol tecnológico
- [ ] Endorsement formal de la División Sudamericana
- [ ] Inventario de universidades SAD con DSpace/OJS activos
- [ ] Aplicar WillPlan Mission Impact Fund (deadline 1 mayo 2027)
- [ ] Preparar concept note para IOI Fund (convocatoria 2026–2027)
- [ ] Registrar ARIEL en OpenDOAR como red
- [ ] Adquirir dominio ariel.network

[:fontawesome-solid-arrow-right: Ver Financiamiento](financiamiento.md){ .md-button .md-button--primary }
[:fontawesome-solid-arrow-right: Ver Arquitectura Técnica](arquitectura.md){ .md-button }
