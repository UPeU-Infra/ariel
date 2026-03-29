# Revisión de Literatura

## Evidencia empírica que justifica ARIEL

---

## Escala del sistema educativo adventista

```mermaid
graph LR
    subgraph stats["Estadísticas GC Education Dept. 2024"]
        A["🏛️ 118+ universidades\nen 50+ países"]
        B["👩‍🎓 163,312 estudiantes\nnivel terciario"]
        C["👨‍🏫 14,206 docentes"]
        D["📚 2° sistema educativo\nprivado del mundo"]
    end
```

| División | Instituciones |
|---|---|
| East-Central Africa (ECD) | 26 |
| Southern Asia-Pacific (SSD) | 21 |
| Inter-American (IAD) | 13 |
| North American (NAD) | 13 |
| **South American (SAD)** | **13** |
| Southern Asia (SUD) | 12 |
| Divisiones europeas | 10 |
| South Pacific (SPD) | 6 |
| Northern Asia-Pacific (NSD) | 5 |

*Fuente: [adventist.education/education-statistics](https://www.adventist.education/education-statistics/)*

---

## La brecha: repositorios confirmados vs. universo total

```mermaid
xychart-beta
    title "Repositorios operativos vs. total de universidades"
    x-axis ["Total universidades", "Con repositorio identificable"]
    y-axis "Instituciones" 0 --> 150
    bar [118, 6]
```

**Repositorios adventistas confirmados activos:**

| Institución | Plataforma | División |
|---|---|---|
| Andrews University (EEUU) | Digital Commons (BePress) | NAD |
| Loma Linda University (EEUU) | SCOPE | NAD |
| UPeU (Perú) | DSpace — aprobado ALICIA 2021 | SAD |
| Universidad de Montemorelos (México) | DSpace | IAD |
| Universidad Adventista de Colombia | Repositorio institucional | IAD |
| SETAI | Repositorio institucional | IAD |

**Tasa de adopción: < 5% del total. Sin federación entre ellas.**

---

## Andrews University: el proxy involuntario

!!! warning "El síntoma del problema"
    **10 de los 20 principales usuarios** del Digital Commons de Andrews University son otras universidades adventistas. El resto del sistema no tiene infraestructura propia y usa Andrews como proxy.

- Lanzado: junio 2015
- Primer millón de descargas: agosto 2018 (3 años)
- Visitantes de 191 países en períodos de 30 días
- 12,260+ documentos al primer millón

*Fuente: [nadadventist.org — Millionth Download](https://www.nadadventist.org/news/millionth-download-digital-commons-andrews-university/)*

---

## Comparación con redes equivalentes

```mermaid
quadrantChart
    title Madurez vs. Escala de redes de repositorios
    x-axis "Escala (instituciones)" --> "Grande"
    y-axis "Madurez de la red" --> "Alta"
    quadrant-1 Referentes a seguir
    quadrant-2 Maduros pero pequeños
    quadrant-3 Oportunidades
    quadrant-4 Escala sin consolidar
    OpenAIRE: [0.95, 0.95]
    LA Referencia: [0.55, 0.75]
    CRRA Católica: [0.25, 0.65]
    BETH Teológica: [0.70, 0.60]
    ARIEL hoy: [0.85, 0.02]
    ARIEL objetivo: [0.85, 0.80]
```

| Red | Instituciones | Registros | Años |
|---|---|---|---|
| OpenAIRE | 2,209 fuentes | 193M publicaciones | 15 |
| LA Referencia | ~100 | 5M+ registros | 12 |
| CRRA (católica) | 50 | Miles (recursos raros) | 15 |
| BETH (teológica) | ~1,500 | 3M+ títulos | 50+ |
| **Red adventista actual** | **~6** | **Sin datos** | **No existe** |

---

## Marco regulatorio que presiona a las universidades adventistas

```mermaid
graph TD
    subgraph peru["🇵🇪 Perú — Marco más maduro"]
        L30035["Ley 30035 (2013)\nObliga repositorios\na todas las universidades"]
        ALICIA["ALICIA / CONCYTEC\nRegistro nacional"]
        SUNEDU["SUNEDU\nFiscalización y sanciones"]
    end

    subgraph colombia["🇨🇴 Colombia"]
        R777["Resolución 0777/2022\nPolítica Nacional\nCiencia Abierta 2022–2031"]
        PND["Ley 2294/2023\nInfraestructuras abiertas\ne interoperables"]
    end

    subgraph brasil["🇧🇷 Brasil"]
        IBICT["IBICT / BDTD\nActiva desde 2002"]
        CAPES["CAPES — Grupo OA 2023\nCriterios de cumplimiento"]
    end

    subgraph adventista["Universidades adventistas"]
        UPeU2["UPeU 🇵🇪\n✅ Ya cumple — ALICIA 2021"]
        UNIQ["UNIQ 🇵🇪\n⏳ En proceso"]
        UNASP2["UNASP 🇧🇷\n⏳ Sujeto a MEC"]
        UNAC2["UNAC 🇨🇴\n⏳ Sujeto a Minciencias"]
    end

    peru --> UPeU2 & UNIQ
    brasil --> UNASP2
    colombia --> UNAC2
```

!!! danger "Ausencia crítica"
    La Conferencia General **no tiene ninguna política formal de acceso abierto**. ARIEL puede ser el catalizador para la primera política denominacional.

---

## Lecciones de proyectos similares

=== "LA Referencia (modelo a seguir)"
    - 12 años de operación, 10 países, ~100 universidades, 5M+ registros
    - Financiado por BID + gobiernos + IOI Fund ($1.5M ciclo inaugural 2025)
    - Interoperable con OpenAIRE desde el inicio
    - **Lección:** el mandato gubernamental y el financiamiento bilateral fueron clave

=== "CRRA Católica (advertencia)"
    - Catholic Research Resources Alliance: 50 instituciones, 15 años
    - En 2023 votaron **disolver la organización** y pasar a Atla
    - **Lección crítica:** sin mandato denominacional formal, la sostenibilidad falla
    - ARIEL necesita respaldo institucional de SAD/GC desde el inicio, no solo de individuos

=== "BETH Teológica (escalabilidad)"
    - 1,500 bibliotecas teológicas europeas de todas las denominaciones
    - Catálogo IxTheo: 3M+ títulos en OA
    - Bibliotecas adventistas europeas ya participan (Friedensau, Collonges, Newbold)
    - **Lección:** la cooperación ecuménica-denominacional es viable a gran escala

=== "ASDAL (red humana existente)"
    - Association of SDA Librarians — organización global activa
    - 4to Congreso Europeo de Bibliotecas Adventistas: Friedensau, junio 2024
    - 7 instituciones europeas participantes
    - Publica *ASDAL Action* y *Journal of Adventist Libraries and Archives*
    - **Oportunidad:** ASDAL ya tiene la red humana. ARIEL le da la infraestructura técnica.

---

## Impacto en rankings universitarios

Las universidades adventistas están en desventaja documentada en rankings que miden visibilidad digital:

- **Webometrics Transparent Ranking** mide repositorios por ítems en Google Scholar
- Universidades con repositorios robustos ascienden directamente en este ranking
- Esto impacta QS, THE y Scimago indirectamente
- Ninguna universidad adventista aparece en posiciones relevantes del Transparent Ranking

*Fuente: [repositories.webometrics.info/en/transparent](https://repositories.webometrics.info/en/transparent)*

---

## Referencias principales

- [adventist.education/education-statistics](https://www.adventist.education/education-statistics/)
- [digitalcommons.andrews.edu](https://digitalcommons.andrews.edu/)
- [lareferencia.info](https://www.lareferencia.info/)
- [openaire.eu/openaire-graph-2024-year-in-review](https://www.openaire.eu/openaire-graph-2024-year-in-review)
- [atla.com/learning-engagement/crra](https://www.atla.com/learning-engagement/crra/)
- [beth.eu](https://beth.eu/)
- [asdal.org](https://www.asdal.org/)
- [investinopen.org](https://investinopen.org/)
- [repositories.webometrics.info/en/transparent](https://repositories.webometrics.info/en/transparent)
