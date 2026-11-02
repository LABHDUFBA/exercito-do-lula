# EXÉRCITO DO LULA — WhatsApp Channel (2026 runoff election)

[![English README](https://img.shields.io/badge/README-english-blue)](README-en.md)
[![README em português](https://img.shields.io/badge/README-portugu%C3%AAs-brightgreen)](README-ptbr.md)
[![README en français](https://img.shields.io/badge/README-fran%C3%A7ais-blueviolet)](README-fr.md)
[![README en español](https://img.shields.io/badge/README-espa%C3%B1ol-orange)](README-es.md)

Research data and materials for the technical-scientific report **"Ativismo digital, coordenação de engajamento e imaginários algorítmicos no canal de WhatsApp EXÉRCITO DO LULA"** (*Digital activism, engagement coordination and algorithmic imaginaries in the WhatsApp channel EXÉRCITO DO LULA*; Nascimento, Brasil, Sodré, Cesarino, Kalil & Belas, 2026), produced within [LABHDUFBA](https://labhdufba.github.io/) — the Digital Humanities Laboratory of the Federal University of Bahia (UFBA), Brazil.

## 📌 Contents

- [Research context](#-research-context)
- [Repository contents](#-repository-contents)
- [Data dictionary](#-data-dictionary)
- [PDF reports (4 languages)](#-pdf-reports-4-languages)
- [Ethical considerations](#-ethical-considerations)
- [Citation](#-citation)
- [References](#-references)

## 🧭 Research context

This repository contains the complete corpus for the observation window of **October 5–25, 2026** — from the pre-runoff debate to the aftermath of the second round of the Brazilian presidential election — of the public WhatsApp channel **EXÉRCITO DO LULA**. **1,278 posts** were captured (texts, images, videos, audio and stickers), of which **1,018 units** were fully coded according to a typology of coordination functions, with validation through blind double coding (105 units; κ=0.577 for the main function). The channel was suspended by the TSE (Superior Electoral Court) on Oct 11, 2026, later registered and formally disassociated from the campaign on Oct 17, 2026 (O Globo, Oct 17, 2026), reaching ~10.8 million followers at its peak (BBC News Brasil, Oct 26, 2026).

Full methodological details — collection, sampling, coding criteria, validation, limitations and empirical episodes E1–E11 — are available in the PDF reports in four languages, under [`relatorios/`](relatorios/).

## 📂 Repository contents

```
├── dados/                          ← structured textual data
│   ├── mensagens.jsonl             ← 1,278 posts with full metadata (Oct 5–25, 2026 window, UTC−3)
│   ├── indice_midias.jsonl         ← media index with hash, type and dimensions
│   ├── indice_miniaturas.jsonl     ← index of derived thumbnails
│   ├── registros_fonte.jsonl       ← source provenance records (Oct 29, 2026 snapshot)
│   └── exercito_lula_dados_textuais_completos.csv  ← complete tabular version of the textual data
├── snapshots/
│   └── 20261029T021046Z/           ← dated snapshot of the channel (Oct 29, 2026, 02:10 UTC)
│       ├── midias/originais/       ← original media: audio (.opus), images (.jpg/.webp), videos (.mp4)
│       ├── midias/miniaturas/      ← thumbnails (.jpg) of all media
│       └── auditoria/              ← reconciliation contract, provenance and summary (JSON)
├── relatorios/                     ← technical-scientific report in 4 languages (PDF)
│   ├── exercito_lula_relatorio_ptbr.pdf
│   ├── exercito_lula_report_en.pdf
│   ├── exercito_lula_rapport_fr.pdf
│   └── exercito_lula_informe_es.pdf
├── README-ptbr.md · README-en.md · README-fr.md · README-es.md
└── LICENSE                         ← CC BY 4.0
```

> **Size note:** the `snapshots/` directory contains videos of up to ~84MB. If `git clone` is slow, download subdirectories directly via the GitHub API or use *sparse checkout*.

## 📖 Data dictionary

### `snapshots/20261029T021046Z/dados/mensagens.jsonl`

One line per record of the channel's full database (N=1,382; Oct 5–25, 2026 BRT window = 1,278 posts). Main fields:

| Field | Description |
|---|---|
| `local_message_id` | Sequential internal post identifier |
| `key_id` / `server_message_id` | WhatsApp message identifiers |
| `timestamp` / `timestamp_utc` | Publication date/time (epoch ms / ISO 8601 UTC) |
| `message_type` | Type: 0=text, 1=image, 2=audio, 3=video, 7=reaction, 15=sticker, 20=video sticker, 81/99=other |
| `text_data` | Post text or media caption (when present) |
| `from_me` | 0=channel post; 1=observer's own record |
| `view_count` | View counter recorded in the snapshot |
| `comments_count` | Comments counter recorded in the snapshot |
| `forwards_count` | Forward counter recorded in the snapshot (see caveat below) |
| `media` | Media metadata (hash, file, dimensions) — key to `midias/` |
| `provenance` / `record_scope` | Snapshot provenance metadata |

> ⚠️ The `forwards_count` and `view_count` fields are presented only as **descriptive attributes of the dataset** — read from the Oct 29, 2026 snapshot, they accumulate interactions after the window and were not validated against WhatsApp's original metrics. They must not be interpreted as measures of circulation, audience or reach.

### `exercito_lula_dados_textuais_completos.csv`

Tabular (spreadsheet) version of the textual data for the Oct 5–25, 2026 window (N=1,048 rows), one row per post. Columns: identifiers (`id`, `local_message_id`), date/time (`data_brt`, `hora_brt`), `modalidade` (text/audio/image/video), `texto_completo` (transcription/OCR where applicable), media metadata (`arquivo`, `duracao_segundos`, `dimensoes`, `status_transcricao`, `ocr_quadros_video`) and the integral coding: `funcao_principal`, `acoes_solicitadas`, `plataformas_mencionadas` and the binary markers `imaginario_algoritmico`, `militarizacao`, `urgencia`, `prova_social`, plus `alvo`, `tom`, `confianca` and `evidencia_codificacao`.

### `snapshots/20261029T021046Z/auditoria/`

- `contrato_reconciliacao.json` — reconciliation rules between records and media
- `proveniencia.json` — provenance chain of the collection (decrypted backup snapshot)
- `resumo.json` — aggregate verification counts (messages, media, hashes)

## 📄 PDF reports (4 languages)

The full technical-scientific report is available under [`relatorios/`](relatorios/) in four languages: Brazilian Portuguese, English, French and Spanish. It contains: executive summary, methodology (collection, coding with blind double coding, kappa validation), results (typology of the 1,018 units, temporal rhythm, transversal markers, platforms mentioned), the empirical episodes E1–E11, theoretical discussion and full references.

## ⚖️ Ethical considerations

- The EXÉRCITO DO LULA channel is **public**; posts were captured through WhatsApp's own export feature, without access to private conversations.
- Content published by third parties (usernames, voices in audio files, faces in videos) is treated as research data following the [AoIR](https://aoir.org/reports/ethics3.pdf) internet research ethics guidelines.
- Identification of non-public individuals was avoided in the report; in the raw data, media files preserve the original content as publicly published in the channel.
- Ethical questions or removal requests: **labhdufba@gmail.com**.

## 📚 Citation

```bibtex
@techreport{nascimento2026exercito,
  title = {Ativismo digital, coordenação de engajamento e imaginários algorítmicos no canal de WhatsApp EXÉRCITO DO LULA},
  author = {Nascimento, Leonardo and Brasil, Eric and Sodr{\'e} Andrade, Ricardo and Cesarino, Let{\'i}cia and Kalil, Isabela and Belas, L{\'i}dia},
  year = {2026},
  institution = {LABHDUFBA — Digital Humanities Laboratory, Federal University of Bahia},
  address = {Salvador},
  url = {https://github.com/LABHDUFBA/exercito-do-lula}
}
```

**Contact:** LABHDUFBA · labhdufba@gmail.com · Salvador, BA, Brazil.

## 🔗 References

- BBC News Brasil. Luiz Fernando Toledo. *Como Janones montou um exército digital na campanha de Lula — e qual espaço pode ter no novo governo*. Oct 26, 2026.
- InternetLab; Aláfia Lab; Artigo 19; Conectas Direitos Humanos. *Coordenação não é inautenticidade: parâmetros técnicos para a análise de mobilizações digitais*. Joint technical opinion. São Paulo, Oct 2026.
- O Globo. Mariana Muniz. *Informação sobre recursos, elo com campanhas, direcionamento: veja as regras para canais no WhatsApp definidas pelo TSE*. Oct 17, 2026.
- Agência Brasil. André Richter. *TSE atende Flávio e manda suspender canal do WhatsApp Exército do Lula*. Oct 11, 2026.

---

<div align="center">

**LABHDUFBA** — Digital Humanities Laboratory · UFBA
Salvador · Bahia · Brazil · October 2026

</div>