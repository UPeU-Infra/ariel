# Contexto del Proyecto

## Origen y estado actual

---

## Sobre este documento

Esta sección documenta el contexto técnico y estratégico del proyecto ARIEL para el equipo interno. Resume las decisiones tomadas, las investigaciones realizadas y el estado actual.

---

## El nombre: ARIEL

**ARIEL = Adventist Repository for Institutional and Educational Literature**

Segunda expansión para contextos no confesionales:
**ARIEL = Academic Repository for Institutional and Educational Literature**

El nombre tiene raíz bíblica sólida. **Ariel** (אֲרִיאֵל) aparece 6 veces en el Antiguo Testamento. El fundamento central es **Isaías 29:18**:

> *"En aquel día los sordos oirán las palabras del libro, y los ojos de los ciegos verán desde la oscuridad y las tinieblas."*

La conexión con un repositorio académico de acceso abierto es genuina, no forzada: el instrumento de restauración en ese capítulo es explícitamente **el libro** — el conocimiento hecho accesible.

**Dominio objetivo:** `ariel.network` — actualmente en venta en Dan.com (~$500–$5,000 USD). El TLD `.network` es aceptado por todos los agregadores académicos (OpenAIRE, LA Referencia, BASE, OpenDOAR) — el protocolo OAI-PMH no tiene restricciones de TLD.

**Por qué no ARIA:** WAI-ARIA es un estándar técnico del W3C para accesibilidad web, ampliamente conocido en IT. Generaría confusión crónica en conversaciones técnicas.

---

## Decisiones tecnológicas

### Stack por fase

| Fase | Tecnología | Razón |
|---|---|---|
| Piloto SAD 2026 | InvenioRDM | Docker Compose, UI moderna, OAI-PMH nativo, CERN/Zenodo |
| SAD completa + IAD 2027 | Hub DSpace-CRIS | Cuando DSpace 10 madure — cero impedancia de schema |
| Global 2028+ | OpenAIRE Graph stack | CERIF nativo, probado a escala continental |

### Schema unificador
**OpenAIRE Guidelines for Literature Repositories v4** — compatible con CERIF, Dublin Core y DataCite simultáneamente. Garantiza indexación en BASE, CORE, OpenAlex y cumplimiento de reguladores nacionales.

### Plataformas que ARIEL agrega (en orden de prioridad)
1. **DSpace** — core del proyecto
2. **OJS** — revistas académicas adventistas (muchas ya existen, OAI-PMH nativo)
3. **DSpace GLAM** — colecciones patrimoniales (Fase 2)
4. **DSpace-CRIS** — entidades CRIS cuando las universidades lleguen a ese nivel (Fase 3)
5. **Indico** — solo actas de congresos, no gestión de eventos (Fase 2)
6. **Koha** — **fuera de alcance** (catálogo de biblioteca física, distinto propósito)

---

## Relación con SciBack

SciBack (DSpace 7 SaaS para universidades peruanas) es el **operador técnico natural** de ARIEL:

```
SciBack despliega DSpace en universidad adventista
    → universidad se integra a ARIEL automáticamente
    → ARIEL agrega su contenido al hub
    → contenido aparece en LA Referencia, OpenAIRE, OpenAlex
    → universidad sube en Webometrics Transparent Ranking
    → universidad cumple normativa nacional (ALICIA, BDTD, etc.)
```

El pipeline comercial se complementa: vender DSpace → integrar al hub ARIEL → posicionar a la universidad en la red global adventista y académica.

---

## Institución promotora: UPeU

La **Universidad Peruana Unión (UPeU)** es la institución proponente por:

- Ya tiene DSpace activo y aprobado por ALICIA/CONCYTEC (agosto 2021)
- Próximamente implementará DSpace-CRIS (primer nodo CRIS adventista en SAD)
- Pertenece a la División Sudamericana — contexto natural para el piloto
- Tiene relación directa con IATec (brazo tecnológico de la SAD)
- Cumple con SUNEDU y CONCYTEC — credibilidad regulatoria demostrada

---

## Socios estratégicos

| Socio | Rol en ARIEL | Por qué |
|---|---|---|
| **IATec** | Infraestructura y legitimidad técnica | Brazo tech oficial SAD, opera en 40+ países, migró a AWS/Azure 2025 |
| **División Sudamericana (SAD)** | Endorsement institucional | Acceso a 13 universidades, canal hacia la GC |
| **ASDAL** | Red de bibliotecarios adventistas | Ya tiene la red humana — ARIEL le da la infraestructura |

---

## Estado de financiamiento al 2026-03-28

| Fondo | Monto | Estado |
|---|---|---|
| WillPlan Mission Impact Fund (GC) | $30K–$100K | Preparar solicitud — UPeU como solicitante |
| División Sudamericana (SAD) | Por confirmar | Negociación institucional pendiente |
| IOI Fund for Network Adoption | Hasta $1.5M | Próxima conv. estimada 2026–2027 |
| Mellon Foundation | $250K–$500K | Ciclo 2027 |
| SCOSS | Recurrente | Fase 3 — cuando haya tracción |

---

## Próximos pasos

- [ ] Reunión con DTI UPeU — presentar propuesta ejecutiva
- [ ] Reunión con IATec — confirmar rol tecnológico y posible infraestructura
- [ ] Endorsement formal División Sudamericana
- [ ] Inventario de universidades SAD con DSpace/OJS activos
- [ ] Adquirir dominio `ariel.network`
- [ ] Aplicar WillPlan MIF 2027 (deadline 1 mayo 2027)
- [ ] Preparar concept note IOI Fund
- [ ] Registrar ARIEL en OpenDOAR como red
- [ ] Contactar ASDAL para alianza
- [ ] Verificar estudio de 92 directores de bibliotecas (Andrews/ASDAL 2024)
