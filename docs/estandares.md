# Estandares y Schemas de Metadatos

## Estrategia: "Recolectar con amplitud, almacenar lo util, exponer lo requerido"

GUIA no intenta ser 100% compliant con todos los estandares desde el dia 1. Implementa lo necesario por fase.

```mermaid
graph LR
    subgraph consume["GUIA Consume (Fase 0)"]
        DC["Dublin Core\nQualified"]
        COAR["COAR\nVocabularies"]
        ALICIA["ALICIA 2.1.0\n38 campos"]
        RENATI["RENATI\nnamespace tesis"]
        OAIRE3["OpenAIRE v3\n(via DSpace)"]
    end

    subgraph interno["Modelo Interno GUIA"]
        CANON["Modelo canonico\nPostgreSQL + pgvector"]
    end

    subgraph expone["GUIA Expone"]
        OAI_DC["oai_dc\nFase 2 (Hub)"]
        OAI_OAIRE["oai_openaire\nFase 2 (Hub)"]
        JSONLD["JSON-LD\nschema.org\nFase 1"]
        MCP_E["MCP Server\nFase 1"]
    end

    consume --> CANON
    CANON --> expone

    style consume fill:#1a4a2a,color:#fff
    style interno fill:#1e3a5f,color:#fff,stroke:#f39c12,stroke-width:2px
    style expone fill:#4a3a1a,color:#fff
```

---

## Estandares por fase

### Fase 0 — Consumir de DSpace/OJS peruanos

```mermaid
graph TB
    subgraph dspace["DSpace UPeU"]
        OAI["OAI-PMH endpoint\nmetadataPrefix=dim"]
    end

    subgraph harvest["Harvester GUIA"]
        SICKLE["sickle\n(OAI-PMH client)"]
        NORM["Normalizador"]
        DRIVER_MAP["Tabla DRIVER→COAR\n(repos no actualizados)"]
    end

    subgraph store["PostgreSQL"]
        ITEMS["guia_item\n(modelo canonico)"]
        VECTORS["pgvector\n(embeddings)"]
    end

    OAI -->|"Qualified DC\n+ renati.* + thesis.*"| SICKLE
    SICKLE --> NORM
    DRIVER_MAP --> NORM
    NORM -->|"URIs COAR\nnormalizadas"| ITEMS
    ITEMS -->|"abstract + title\n→ embeddings"| VECTORS

    style harvest fill:#0d1b3e,color:#fff
    style store fill:#1e3a5f,color:#fff
```

**Por que `metadataPrefix=dim` y no `oai_dc`:** DSpace Intermediate Metadata (`dim`) expone todos los campos calificados incluyendo `renati.*` y `thesis.*`. Simple DC (`oai_dc`) pierde esos campos. Cambio de 1 linea en el harvester:

```python
records = sickle.ListRecords(metadataPrefix='dim', set='col_...')
```

**Tabla de traduccion DRIVER→COAR** — para repositorios que no han actualizado a ALICIA 2.1.0:

```python
DRIVER_TO_COAR = {
    "info:eu-repo/semantics/doctoralThesis": "http://purl.org/coar/resource_type/c_db06",
    "info:eu-repo/semantics/masterThesis":   "http://purl.org/coar/resource_type/c_bdcc",
    "info:eu-repo/semantics/bachelorThesis":  "http://purl.org/coar/resource_type/c_7a1f",
    "info:eu-repo/semantics/article":        "http://purl.org/coar/resource_type/c_6501",
    "info:eu-repo/semantics/openAccess":     "http://purl.org/coar/access_right/c_abf2",
    "info:eu-repo/semantics/embargoedAccess":"http://purl.org/coar/access_right/c_f1cf",
    "info:eu-repo/semantics/restrictedAccess":"http://purl.org/coar/access_right/c_16ec",
    "info:eu-repo/semantics/closedAccess":   "http://purl.org/coar/access_right/c_14cb",
}
```

---

### Fase 1 — schema.org / JSON-LD para visibilidad web

Cuando el Hub o el dashboard del Node tengan paginas publicas de items, embeber JSON-LD en el `<head>`:

```json
{
  "@context": "https://schema.org",
  "@type": "Thesis",
  "name": "Contaminacion del suelo en la region Junin",
  "author": {"@type": "Person", "name": "Flores, Juan"},
  "datePublished": "2025-06-15",
  "inLanguage": "es",
  "url": "https://repositorio.upeu.edu.pe/handle/20.500.12840/1234",
  "description": "Se evaluo la concentracion de metales pesados...",
  "keywords": ["contaminacion", "suelo", "metales pesados"],
  "sourceOrganization": {"@type": "Organization", "name": "Universidad Peruana Union"}
}
```

**Tipos schema.org relevantes:** `ScholarlyArticle`, `Thesis`, `Book`, `Dataset`.

Google Scholar indexa automaticamente paginas con JSON-LD correcto = visibilidad gratuita.

---

### Fase 2 — OAI-PMH endpoint del Hub (OpenAIRE v4)

El Hub expone 3 `metadataPrefix`:

| Prefix | Estandar | Para quien |
|--------|---------|-----------|
| `oai_dc` | Simple Dublin Core | Obligatorio por protocolo OAI-PMH |
| `oai_openaire` | OpenAIRE v4 | OpenAIRE, redes europeas |
| `dim` | DSpace Intermediate | LA Referencia, agregadores LATAM |

Validar contra: `https://www.openaire.eu/validator-and-registration/`

---

## Vocabularios COAR

GUIA almacena URIs COAR, nunca strings libres.

### Tipos de recurso (dc.type)

| Tipo | URI COAR |
|------|----------|
| Tesis doctoral | `http://purl.org/coar/resource_type/c_db06` |
| Tesis de maestria | `http://purl.org/coar/resource_type/c_bdcc` |
| Trabajo de pregrado | `http://purl.org/coar/resource_type/c_7a1f` |
| Articulo original | `http://purl.org/coar/resource_type/c_2df8fbb1` |
| Articulo de revision | `http://purl.org/coar/resource_type/c_dcae04bc` |
| Preprint | `http://purl.org/coar/resource_type/c_816b` |
| Libro | `http://purl.org/coar/resource_type/c_2f33` |
| Capitulo de libro | `http://purl.org/coar/resource_type/c_3248` |
| Comunicacion congreso | `http://purl.org/coar/resource_type/c_5794` |
| Conjunto de datos | `http://purl.org/coar/resource_type/c_ddb1` |

### Derechos de acceso (dc.rights)

| Estado | URI COAR |
|--------|----------|
| Acceso abierto | `http://purl.org/coar/access_right/c_abf2` |
| Embargado | `http://purl.org/coar/access_right/c_f1cf` |
| Restringido | `http://purl.org/coar/access_right/c_16ec` |
| Cerrado | `http://purl.org/coar/access_right/c_14cb` |

---

## ALICIA 2.1.0 — Campos obligatorios

### 11 campos universales (todos los tipos de documento)

```mermaid
graph TD
    subgraph obligatorios["Campos OBLIGATORIOS — Todo documento"]
        A1["dc.contributor.author"]
        A2["dc.title"]
        A3["dc.publisher"]
        A4["dc.date.issued"]
        A5["dc.type\n(URI COAR)"]
        A6["dc.language.iso\n(ISO 639-3)"]
        A7["dc.rights\n(URI COAR)"]
        A8["dc.description.abstract\n⭐ BASE DEL RAG"]
        A9["dc.subject"]
        A10["dc.subject.ocde"]
        A11["dc.identifier.uri\n(Handle)"]
    end

    style obligatorios fill:#1a4a2a,color:#fff
    style A8 fill:#f39c12,color:#000,stroke:#e74c3c,stroke-width:3px
```

### Campos adicionales para tesis (RENATI/SUNEDU)

```mermaid
graph TD
    subgraph renati["Campos RENATI — Solo tesis"]
        R1["renati.author.dni"]
        R2["dc.contributor.advisor"]
        R3["renati.advisor.orcid"]
        R4["renati.advisor.dni"]
        R5["renati.type"]
        R6["thesis.degree.name"]
        R7["renati.level\n(Maestria/Doctorado/Pregrado)"]
        R8["thesis.degree.discipline"]
        R9["renati.discipline"]
        R10["thesis.degree.grantor"]
        R11["renati.juror"]
    end

    style renati fill:#4a1a1a,color:#fff
```

---

## Modelo interno canonico — PostgreSQL

```sql
CREATE TABLE guia_item (
    -- Identidad
    id              UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    source_repo     TEXT NOT NULL,           -- URL base del repositorio
    source_id       TEXT NOT NULL,           -- OAI identifier
    handle          TEXT,                    -- dc.identifier.uri
    doi             TEXT,                    -- dc.identifier.doi

    -- Clasificacion (COAR URIs, nunca strings)
    resource_type   TEXT NOT NULL,           -- URI COAR dc.type
    access_right    TEXT NOT NULL,           -- URI COAR dc.rights
    language        TEXT,                    -- ISO 639-3

    -- Contenido principal
    title           TEXT NOT NULL,           -- dc.title
    title_alt       TEXT[],                  -- dc.title.alternative
    abstract        TEXT,                    -- dc.description.abstract (BASE DEL RAG)
    date_issued     DATE,                   -- dc.date.issued
    publisher       TEXT,                   -- dc.publisher
    source_journal  TEXT,                   -- dc.source / dc.relation.isPartOf

    -- Autores y responsables
    authors         JSONB,                  -- [{name, orcid, dni, order}]
    advisor         TEXT,                   -- dc.contributor.advisor (tesis)

    -- Clasificacion tematica
    subjects        TEXT[],                 -- dc.subject (palabras clave)
    subject_ocde    TEXT[],                 -- dc.subject.ocde

    -- RENATI / ALICIA Peru (nullable, solo tesis)
    renati_type     TEXT,                   -- renati.type
    renati_level    TEXT,                   -- renati.level
    degree_name     TEXT,                   -- thesis.degree.name
    degree_program  TEXT,                   -- thesis.degree.discipline
    degree_grantor  TEXT,                   -- thesis.degree.grantor

    -- RAG / pgvector
    embedding       VECTOR(1536),           -- embedding del abstract+title
    full_text       TEXT,                   -- texto completo via GROBID (Fase 1)

    -- Tracking
    harvested_at    TIMESTAMP DEFAULT NOW(),
    updated_at      TIMESTAMP DEFAULT NOW(),
    embargo_end     DATE,

    UNIQUE(source_repo, source_id)
);

-- Indice vectorial para busqueda semantica
CREATE INDEX ON guia_item USING ivfflat (embedding vector_cosine_ops);
```

---

## Flujo completo de metadatos

```mermaid
sequenceDiagram
    participant DS as DSpace UPeU
    participant HV as Harvester (sickle)
    participant NM as Normalizador
    participant PG as PostgreSQL
    participant VE as pgvector
    participant RA as RAG Engine
    participant US as Usuario

    DS->>HV: OAI-PMH ListRecords (dim)
    HV->>NM: Record XML con DC + renati.* + thesis.*
    NM->>NM: Normalizar tipos DRIVER→COAR
    NM->>NM: Validar 11 campos obligatorios ALICIA
    NM->>PG: INSERT guia_item (metadatos estructurados)
    PG->>VE: Generar embedding(abstract + title)
    
    Note over HV,VE: Fase 1: GROBID full-text → embedding adicional

    US->>RA: "Que tesis de maestria hay sobre IA?"
    RA->>VE: Busqueda vectorial (cosine similarity)
    RA->>PG: Filtro: renati_level = 'Maestria'
    VE-->>RA: Top-K documentos relevantes
    RA-->>US: Respuesta con fuentes citadas
```

---

## Estandares descartados y por que

| Estandar | Razon de descarte | Alternativa |
|---------|-------------------|-------------|
| CERIF | Europeo, complejo, sin mandato en LATAM | Campos RENATI cubren el caso peruano |
| VIVO | Perfiles de investigadores, RDF complejo, sin adopcion LATAM | ORCID API directo (Fase 2) |
| MODS / METS | Preservacion digital, overkill para RAG | Dublin Core Qualified via `dim` |
| DRIVER | Superado por OpenAIRE v3/v4 desde 2014 | Tabla traduccion DRIVER→COAR |
| ETD-MS formal | Namespace propio NDLTD | Campos RENATI ya son equivalentes |
