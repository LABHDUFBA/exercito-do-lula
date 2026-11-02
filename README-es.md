# EXÉRCITO DO LULA — Canal de WhatsApp (2ª vuelta, elecciones 2026)

[![README en español](https://img.shields.io/badge/README-espa%C3%B1ol-orange)](README-es.md)
[![README em português](https://img.shields.io/badge/README-portugu%C3%AAs-brightgreen)](README-ptbr.md)
[![English README](https://img.shields.io/badge/README-english-blue)](README-en.md)
[![README en français](https://img.shields.io/badge/README-fran%C3%A7ais-blueviolet)](README-fr.md)

Datos y materiales de investigación del informe técnico-científico **"Ativismo digital, coordenação de engajamento e imaginários algorítmicos no canal de WhatsApp EXÉRCITO DO LULA"** (*Activismo digital, coordinación del compromiso e imaginarios algorítmicos en el canal de WhatsApp EXÉRCITO DO LULA*; Nascimento, Brasil, Sodré, Cesarino, Kalil & Belas, 2026), producido en el marco del [LABHDUFBA](https://labhdufba.github.io/) — el Laboratorio de Humanidades Digitales de la Universidad Federal de Bahía (UFBA), Brasil.

## 📌 Índice

- [Contexto de la investigación](#-contexto-de-la-investigación)
- [Contenido del repositorio](#-contenido-del-repositorio)
- [Diccionario de datos](#-diccionario-de-datos)
- [Informes en PDF (4 idiomas)](#-informes-en-pdf-4-idiomas)
- [Consideraciones éticas](#-consideraciones-éticas)
- [Citación](#-citación)
- [Referencias](#-referencias)

## 🧭 Contexto de la investigación

Este repositorio reúne el corpus completo de la ventana de observación del **5 al 25 de octubre de 2026** — del debate previo al rescaldo de la segunda vuelta de la elección presidencial brasileña — del canal público de WhatsApp **EXÉRCITO DO LULA**. Se capturaron **1.278 publicaciones** (textos, imágenes, vídeos, audios y stickers), de las cuales **1.018 unidades** fueron íntegramente codificadas según una tipología de funciones de coordinación, con validación por doble codificación a ciegas (105 unidades; κ=0,577 para la función principal). El canal fue suspendido por el TSE (Tribunal Superior Electoral) el 11/10/2026, posteriormente registrado y formalmente desvinculado de la campaña el 17/10/2026 (O Globo, 17/10/2026), alcanzando ~10,8 millones de seguidores en su apogeo (BBC News Brasil, 26/10/2026).

Los detalles metodológicos completos — recolección, muestreo, criterios de codificación, validación, limitaciones y episodios empíricos E1–E11 — están disponibles en los informes en PDF en cuatro idiomas, en [`relatorios/`](relatorios/).

## 📂 Contenido del repositorio

```
├── dados/                          ← datos textuales estructurados
│   ├── mensagens.jsonl             ← 1.278 publicaciones con metadatos completos (ventana 5–25/10/2026, UTC−3)
│   ├── indice_midias.jsonl         ← índice de los medios con hash, tipo y dimensiones
│   ├── indice_miniaturas.jsonl     ← índice de las miniaturas derivadas
│   ├── registros_fonte.jsonl       ← registros de procedencia de la fuente (instantánea del 29/10/2026)
│   └── exercito_lula_dados_textuais_completos.csv  ← versión tabular completa de los datos textuales
├── snapshots/
│   └── 20261029T021046Z/           ← instantánea fechada del canal (29 oct 2026, 02:10 UTC)
│       ├── midias/originais/       ← medios originales: audios (.opus), imágenes (.jpg/.webp), vídeos (.mp4)
│       ├── midias/miniaturas/      ← miniaturas (.jpg) de todos los medios
│       └── auditoria/              ← contrato de reconciliación, procedencia y resumen (JSON)
├── relatorios/                     ← informe técnico-científico en 4 idiomas (PDF)
│   ├── exercito_lula_relatorio_ptbr.pdf
│   ├── exercito_lula_report_en.pdf
│   ├── exercito_lula_rapport_fr.pdf
│   └── exercito_lula_informe_es.pdf
├── README-ptbr.md · README-en.md · README-fr.md · README-es.md
└── LICENSE                         ← CC BY 4.0
```

> **Nota de volumen:** el directorio `snapshots/` contiene vídeos de hasta ~84MB. Si el `git clone` resulta lento, descargue los subdirectorios directamente vía la API de GitHub o utilice *sparse checkout*.

## 📖 Diccionario de datos

### `snapshots/20261029T021046Z/dados/mensagens.jsonl`

Una línea por registro de la base completa del canal (N=1.382; ventana 5–25/10/2026 BRT = 1.278 publicaciones). Campos principales:

| Campo | Descripción |
|---|---|
| `local_message_id` | Identificador secuencial interno de la publicación |
| `key_id` / `server_message_id` | Identificadores del mensaje en WhatsApp |
| `timestamp` / `timestamp_utc` | Fecha/hora de publicación (epoch ms / ISO 8601 UTC) |
| `message_type` | Tipo: 0=texto, 1=imagen, 2=audio, 3=vídeo, 7=reacción, 15=sticker, 20=sticker de vídeo, 81/99=otros |
| `text_data` | Texto de la publicación o leyenda del medio (cuando exista) |
| `from_me` | 0=publicación del canal; 1=registro del propio observador |
| `view_count` | Contador de visualizaciones registrado en la instantánea |
| `comments_count` | Contador de comentarios registrado en la instantánea |
| `forwards_count` | Contador de reenvíos registrado en la instantánea (ver salvedad abajo) |
| `media` | Metadatos del medio (hash, archivo, dimensiones) — clave hacia `midias/` |
| `provenance` / `record_scope` | Metadatos de procedencia de la instantánea |

> ⚠️ Los campos `forwards_count` y `view_count` se presentan únicamente como **atributos descriptivos de la base** — leídos en la instantánea del 29/10/2026, acumulan interacciones posteriores a la ventana y no fueron validados contra las métricas originales de WhatsApp. No deben interpretarse como medidas de circulación, audiencia o alcance.

### `exercito_lula_dados_textuais_completos.csv`

Versión tabular (hoja de cálculo) de los datos textuales de la ventana 5–25/10/2026 (N=1.048 líneas), con una línea por publicación. Columnas: identificadores (`id`, `local_message_id`), fecha/hora (`data_brt`, `hora_brt`), `modalidade` (texto/audio/imagen/vídeo), `texto_completo` (transcripción/OCR cuando aplica), metadatos de medios (`arquivo`, `duracao_segundos`, `dimensoes`, `status_transcricao`, `ocr_quadros_video`) y la codificación integral: `funcao_principal`, `acoes_solicitadas`, `plataformas_mencionadas` y los marcadores binarios `imaginario_algoritmico`, `militarizacao`, `urgencia`, `prova_social`, además de `alvo`, `tom`, `confianca` y `evidencia_codificacao`.

### `snapshots/20261029T021046Z/auditoria/`

- `contrato_reconciliacao.json` — reglas de reconciliación entre registros y medios
- `proveniencia.json` — cadena de procedencia de la recolección (instantánea del respaldo descifrado)
- `resumo.json` — recuentos agregados de verificación (mensajes, medios, hashes)

## 📄 Informes en PDF (4 idiomas)

El informe técnico-científico completo está disponible en [`relatorios/`](relatorios/) en cuatro idiomas: portugués de Brasil, inglés, francés y español. Contiene: resumen ejecutivo, metodología (recolección, codificación con doble codificación a ciegas, validación kappa), resultados (tipología de las 1.018 unidades, ritmo temporal, marcadores transversales, plataformas mencionadas), los episodios empíricos E1–E11, discusión teórica y referencias completas.

## ⚖️ Consideraciones éticas

- El canal EXÉRCITO DO LULA es **público**; las publicaciones fueron capturadas mediante la función de exportación del propio WhatsApp, sin acceso a conversaciones privadas.
- El contenido publicado por terceros (nombres de usuario, voces en audios, rostros en vídeos) se trata como dato de investigación según las directrices [AoIR](https://aoir.org/reports/ethics3.pdf) para la investigación en internet.
- La identificación de individuos no públicos fue evitada en el informe; en los datos brutos, los archivos multimedia preservan el contenido original tal como fue publicado públicamente en el canal.
- Dudas éticas o solicitudes de eliminación: **labhdufba@gmail.com**.

## 📚 Citación

```bibtex
@techreport{nascimento2026exercito,
  title = {Ativismo digital, coordenação de engajamento e imaginários algorítmicos no canal de WhatsApp EXÉRCITO DO LULA},
  author = {Nascimento, Leonardo and Brasil, Eric and Sodr{\'e} Andrade, Ricardo and Cesarino, Let{\'i}cia and Kalil, Isabela and Belas, L{\'i}dia},
  year = {2026},
  institution = {LABHDUFBA — Laboratorio de Humanidades Digitales, Universidad Federal de Bahía},
  address = {Salvador},
  url = {https://github.com/LABHDUFBA/whatsapp-2turno-2026}
}
```

**Contacto:** LABHDUFBA · labhdufba@gmail.com · Salvador, BA, Brasil.

## 🔗 Referencias

- BBC News Brasil. Luiz Fernando Toledo. *Como Janones montou um exército digital na campanha de Lula — e qual espaço pode ter no novo governo*. 26 oct. 2026.
- InternetLab; Aláfia Lab; Artigo 19; Conectas Direitos Humanos. *Coordenação não é inautenticidade: parâmetros técnicos para a análise de mobilizações digitais*. Parecer técnico conjunto. São Paulo, oct. 2026.
- O Globo. Mariana Muniz. *Informação sobre recursos, elo com campanhas, direcionamento: veja as regras para canais no WhatsApp definidas pelo TSE*. 17 oct. 2026.
- Agência Brasil. André Richter. *TSE atende Flávio e manda suspender canal do WhatsApp Exército do Lula*. 11 oct. 2026.

---

<div align="center">

**LABHDUFBA** — Laboratorio de Humanidades Digitales · UFBA
Salvador · Bahía · Brasil · Octubre de 2026

</div>