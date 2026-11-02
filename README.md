# EXÉRCITO DO LULA — Canal de WhatsApp (eleições 2026, 2º turno)

Dados e materiais de pesquisa do relatório técnico-científico produzido no âmbito do [LABHDUFBA](https://labhdufba.github.io/) — Laboratório de Humanidades Digitais da Universidade Federal da Bahia (UFBA).

<p align="center"><strong>[🇧🇷 Português (Brasil)](#portugues) · [🇬🇧 English](#english) · [🇫🇷 Français](#francais) · [🇪🇸 Español](#espanol)</strong></p>

---

<h2 id="portugues">🇧🇷 Português (Brasil)</h2>

Dados e materiais de pesquisa do relatório técnico-científico **"Ativismo digital, coordenação de engajamento e imaginários algorítmicos no canal de WhatsApp EXÉRCITO DO LULA"** (Nascimento, Brasil, Sodré, Cesarino, Kalil & Belas, 2026), produzido no âmbito do [LABHDUFBA](https://labhdufba.github.io/) — Laboratório de Humanidades Digitais da Universidade Federal da Bahia (UFBA).

## 🧭 Contexto da pesquisa

Este repositório reúne o corpus completo da janela de observação de **5 a 25 de outubro de 2026** — do debate pré-jogo ao rescaldo do 2º turno da eleição presidencial brasileira — do canal público de WhatsApp **EXÉRCITO DO LULA**. Foram capturados **1.278 posts** (textos, imagens, vídeos, áudios e figurinhas), dos quais **1.018 unidades** foram integralmente codificadas segundo tipologia de funções de coordenação, com validação por dupla codificação às cegas (105 unidades; κ=0,577 na função principal). O canal foi suspenso por decisão do TSE em 11/10/2026, posteriormente registrado e formalmente desvinculado da campanha em 17/10/2026 (O Globo, 17/10/2026), alcançando ~10,8 milhões de seguidores no pico (BBC News Brasil, 26/10/2026).

Os detalhes metodológicos completos — coleta, amostra, critérios de codificação, validação, limitações e episódios E1–E11 — estão nos relatórios em PDF nos quatro idiomas, no diretório [`relatorios/`](relatorios/).

## 📂 Conteúdo do repositório

```
├── exercito_lula_dados_textuais_completos.csv  ← versão tabular completa dos dados textuais codificados
├── snapshots/
│   └── 20261029T021046Z/           ← snapshot datado do canal (29 out 2026, 02:10 UTC)
│       ├── dados/                  ← dados textuais estruturados da base completa do canal
│       │   ├── mensagens.jsonl     ← 1.382 registros da base (janela 5–25/10/2026 BRT = 1.278 posts)
│       │   ├── indice_midias.jsonl ← índice das mídias originais
│       │   ├── indice_miniaturas.jsonl ← índice das miniaturas
│       │   └── registros_fonte.jsonl ← registros de proveniência da coleta
│       ├── midias/originais/       ← 232 mídias originais: 152 áudios (.opus), 48 imagens (.jpg), 8 (.webp), 24 vídeos (.mp4)
│       ├── midias/miniaturas/      ← 114 miniaturas (.jpg)
│       └── auditoria/              ← contrato de reconciliação, proveniência e resumo (JSON)
├── relatorios/                     ← relatório técnico-científico em 4 idiomas (PDF)
│   ├── exercito_lula_relatorio_ptbr.pdf
│   ├── exercito_lula_report_en.pdf
│   ├── exercito_lula_rapport_fr.pdf
│   └── exercito_lula_informe_es.pdf
├── README.md                       ← este arquivo (4 idiomas em seções)
└── LICENSE                         ← CC BY 4.0
```

> **Nota de volume:** o diretório `snapshots/` contém vídeos com até ~84MB. Se o `git clone` estiver lento, use download direto de subdiretórios via API do GitHub ou a opção *sparse checkout*.

## 📖 Dicionário de dados

### `snapshots/20261029T021046Z/dados/mensagens.jsonl`

Uma linha por registro da base completa do canal (N=1.382; janela 5–25/10/2026 BRT = 1.278 posts). Campos principais:

| Campo | Descrição |
|---|---|
| `local_message_id` | Identificador sequencial interno do post |
| `key_id` / `server_message_id` | Identificadores da mensagem no WhatsApp |
| `timestamp` / `timestamp_utc` | Data/hora de publicação (epoch ms / ISO 8601 UTC) |
| `message_type` | Tipo: 0=texto, 1=imagem, 2=áudio, 3=vídeo, 7=reaction, 15=figurinha, 20=figurinha de vídeo, 81/99=outros |
| `text_data` | Texto do post ou legenda da mídia (quando houver) |
| `from_me` | 0=post do canal; 1=registro do próprio observador |
| `view_count` | Contador de visualizações registrado no snapshot |
| `comments_count` | Contador de comentários registrado no snapshot |
| `forwards_count` | Contador de encaminhamentos registrado no snapshot (ver ressalva abaixo) |
| `media` | Metadados da mídia (hash, arquivo, dimensões) — chave para `midias/` |
| `provenance` / `record_scope` | Metadados de proveniência do snapshot |

> ⚠️ Os campos `forwards_count` e `view_count` são apresentados apenas como **atributos descritivos da base** — lidos no snapshot de 29/10/2026, acumulam interações posteriores à janela e não foram validados contra as métricas originais do WhatsApp. Não devem ser interpretados como medidas de circulação, audiência ou alcance.

### `exercito_lula_dados_textuais_completos.csv`

Versão tabular (planilha) dos dados textuais da janela 5–25/10/2026 (N=1.048 linhas), com uma linha por post. Colunas: identificadores (`id`, `local_message_id`), data/hora (`data_brt`, `hora_brt`), `modalidade` (texto/áudio/imagem/vídeo), `texto_completo` (transcrição/OCR quando aplicável), metadados de mídia (`arquivo`, `duracao_segundos`, `dimensoes`, `status_transcricao`, `ocr_quadros_video`) e a codificação integral: `funcao_principal`, `acoes_solicitadas`, `plataformas_mencionadas` e os marcadores binários `imaginario_algoritmico`, `militarizacao`, `urgencia`, `prova_social`, além de `alvo`, `tom`, `confianca` e `evidencia_codificacao`.

### `snapshots/20261029T021046Z/auditoria/`

- `contrato_reconciliacao.json` — regras de reconciliação entre registros e mídias
- `proveniencia.json` — cadeia de proveniência da coleta (snapshot do backup descriptografado)
- `resumo.json` — contagens agregadas de verificação (mensagens, mídias, hashes)

## 📄 Relatórios em PDF (4 idiomas)

O relatório técnico-científico completo está em [`relatorios/`](relatorios/) em quatro idiomas: português do Brasil, inglês, francês e espanhol. Contém: resumo executivo, metodologia (coleta, codificação com dupla verificação às cegas, validação kappa), resultados (tipologia das 1.018 unidades, ritmo temporal, marcadores transversais, plataformas mencionadas), os episódios empíricos E1–E11, discussão teórica e referências completas.

## ⚖️ Considerações éticas

- O canal EXÉRCITO DO LULA é **público**; os posts foram capturados por meio do recurso de exportação do próprio WhatsApp, sem acesso a conversas privadas.
- O conteúdo publicado por terceiros (nomes de usuário, vozes em áudios, rostos em vídeos) é tratado como dado de pesquisa segundo as diretrizes da [AOIR](https://aoir.org/reports/ethics3.pdf) para pesquisa em internet.
- A identificação de indivíduos não-figuras públicas foi evitada no relatório; nos dados brutos, os arquivos de mídia preservam o conteúdo original tal como publicado publicamente no canal.
- Dúvidas éticas ou pedidos de remoção: **labhdufba@gmail.com**.

## 📚 Citação

```bibtex
@techreport{nascimento2026exercito,
  title = {Ativismo digital, coordenação de engajamento e imaginários algorítmicos no canal de WhatsApp EXÉRCITO DO LULA},
  author = {Nascimento, Leonardo and Brasil, Eric and Sodr{\'e} Andrade, Ricardo and Cesarino, Let{\'i}cia and Kalil, Isabela and Belas, L{\'i}dia},
  year = {2026},
  institution = {LABHDUFBA — Laborat{\'o}rio de Humanidades Digitais, Universidade Federal da Bahia},
  address = {Salvador},
  url = {https://github.com/LABHDUFBA/exercito-do-lula}
}
```

**Contato:** LABHDUFBA · labhdufba@gmail.com · Salvador, BA, Brasil.

## 🔗 Referências

- BBC News Brasil. Luiz Fernando Toledo. *Como Janones montou um exército digital na campanha de Lula — e qual espaço pode ter no novo governo*. 26 out. 2026.
- InternetLab; Aláfia Lab; Artigo 19; Conectas Direitos Humanos. *Coordenação não é inautenticidade: parâmetros técnicos para a análise de mobilizações digitais*. Parecer técnico conjunto. São Paulo, out. 2026.
- O Globo. Mariana Muniz. *Informação sobre recursos, elo com campanhas, direcionamento: veja as regras para canais no WhatsApp definidas pelo TSE*. 17 out. 2026.
- Agência Brasil. André Richter. *TSE atende Flávio e manda suspender canal do WhatsApp Exército do Lula*. 11 out. 2026.

---

<div align="center">

**LABHDUFBA** — Laboratório de Humanidades Digitais · UFBA
Salvador · Bahia · Brasil · Outubro de 2026

</div>

---

<h2 id="english">🇬🇧 English</h2>

# EXÉRCITO DO LULA — WhatsApp Channel (2026 runoff election)

Research data and materials for the technical-scientific report **"Ativismo digital, coordenação de engajamento e imaginários algorítmicos no canal de WhatsApp EXÉRCITO DO LULA"** (*Digital activism, engagement coordination and algorithmic imaginaries in the WhatsApp channel EXÉRCITO DO LULA*; Nascimento, Brasil, Sodré, Cesarino, Kalil & Belas, 2026), produced within [LABHDUFBA](https://labhdufba.github.io/) — the Digital Humanities Laboratory of the Federal University of Bahia (UFBA), Brazil.

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
├── README.md                       ← este arquivo (4 idiomas em seções)
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

---

<h2 id="francais">🇫🇷 Français</h2>

# EXÉRCITO DO LULA — Canal WhatsApp (2e tour, élections 2026)

Données et matériaux de recherche du rapport technico-scientifique **« Ativismo digital, coordenação de engajamento e imaginários algorítmicos no canal de WhatsApp EXÉRCITO DO LULA »** (*Militantisme numérique, coordination de l'engagement et imaginaires algorithmiques dans le canal WhatsApp EXÉRCITO DO LULA* ; Nascimento, Brasil, Sodré, Cesarino, Kalil & Belas, 2026), produit dans le cadre du [LABHDUFBA](https://labhdufba.github.io/) — le Laboratoire des humanités numériques de l'Université fédérale de Bahia (UFBA), Brésil.

## 🧭 Contexte de la recherche

Ce dépôt contient le corpus complet de la fenêtre d'observation du **5 au 25 octobre 2026** — du débat pré-second tour à l'après-scrutin du second tour de l'élection présidentielle brésilienne — du canal WhatsApp public **EXÉRCITO DO LULA**. **1 278 publications** ont été capturées (textes, images, vidéos, audios et autocollants), dont **1 018 unités** ont été intégralement codées selon une typologie des fonctions de coordination, avec validation par double codage à l'aveugle (105 unités ; κ=0,577 pour la fonction principale). Le canal a été suspendu par le TSE (Tribunal électoral supérieur) le 11 oct. 2026, puis enregistré et formellement dissocié de la campagne le 17 oct. 2026 (O Globo, 17 oct. 2026), atteignant environ 10,8 millions d'abonnés à son apogée (BBC News Brasil, 26 oct. 2026).

Les détails méthodologiques complets — collecte, échantillonnage, critères de codage, validation, limites et épisodes empiriques E1–E11 — sont disponibles dans les rapports PDF en quatre langues, sous [`relatorios/`](relatorios/).

## 📂 Contenu du dépôt

```
├── dados/                          ← données textuelles structurées
│   ├── mensagens.jsonl             ← 1 278 publications avec métadonnées complètes (fenêtre 5–25 oct. 2026, UTC−3)
│   ├── indice_midias.jsonl         ← index des médias avec hachage, type et dimensions
│   ├── indice_miniaturas.jsonl     ← index des vignettes dérivées
│   ├── registros_fonte.jsonl       ← enregistrements de provenance de la source (instantané du 29 oct. 2026)
│   └── exercito_lula_dados_textuais_completos.csv  ← version tabulaire complète des données textuelles
├── snapshots/
│   └── 20261029T021046Z/           ← instantané daté du canal (29 oct. 2026, 02:10 UTC)
│       ├── midias/originais/       ← médias originaux : audios (.opus), images (.jpg/.webp), vidéos (.mp4)
│       ├── midias/miniaturas/      ← vignettes (.jpg) de tous les médias
│       └── auditoria/              ← contrat de réconciliation, provenance et résumé (JSON)
├── relatorios/                     ← rapport technico-scientifique en 4 langues (PDF)
│   ├── exercito_lula_relatorio_ptbr.pdf
│   ├── exercito_lula_report_en.pdf
│   ├── exercito_lula_rapport_fr.pdf
│   └── exercito_lula_informe_es.pdf
├── README.md                       ← este arquivo (4 idiomas em seções)
└── LICENSE                         ← CC BY 4.0
```

> **Note de volume :** le répertoire `snapshots/` contient des vidéos allant jusqu'à ~84 Mo. Si le `git clone` est lent, téléchargez directement les sous-répertoires via l'API GitHub ou utilisez le *sparse checkout*.

## 📖 Dictionnaire des données

### `snapshots/20261029T021046Z/dados/mensagens.jsonl`

Une ligne par enregistrement de la base complète du canal (N=1 382 ; fenêtre 5–25 oct. 2026 BRT = 1 278 publications). Champs principaux :

| Champ | Description |
|---|---|
| `local_message_id` | Identifiant séquentiel interne de la publication |
| `key_id` / `server_message_id` | Identifiants du message WhatsApp |
| `timestamp` / `timestamp_utc` | Date/heure de publication (epoch ms / ISO 8601 UTC) |
| `message_type` | Type : 0=texte, 1=image, 2=audio, 3=vidéo, 7=réaction, 15=autocollant, 20=autocollant vidéo, 81/99=autres |
| `text_data` | Texte de la publication ou légende du média (le cas échéant) |
| `from_me` | 0=publication du canal ; 1=enregistrement de l'observateur |
| `view_count` | Compteur de vues enregistré dans l'instantané |
| `comments_count` | Compteur de commentaires enregistré dans l'instantané |
| `forwards_count` | Compteur de transferts enregistré dans l'instantané (voir réserve ci-dessous) |
| `media` | Métadonnées du média (hachage, fichier, dimensions) — clé vers `midias/` |
| `provenance` / `record_scope` | Métadonnées de provenance de l'instantané |

> ⚠️ Les champs `forwards_count` et `view_count` sont présentés uniquement comme des **attributs descriptifs de la base** — lus dans l'instantané du 29 oct. 2026, ils accumulent des interactions postérieures à la fenêtre et n'ont pas été validés par rapport aux métriques originales de WhatsApp. Ils ne doivent pas être interprétés comme des mesures de circulation, d'audience ou de portée.

### `exercito_lula_dados_textuais_completos.csv`

Version tabulaire (tableur) des données textuelles de la fenêtre 5–25 oct. 2026 (N=1 048 lignes), une ligne par publication. Colonnes : identifiants (`id`, `local_message_id`), date/heure (`data_brt`, `hora_brt`), `modalidade` (texte/audio/image/vidéo), `texto_completo` (transcription/OCR le cas échéant), métadonnées des médias (`arquivo`, `duracao_segundos`, `dimensoes`, `status_transcricao`, `ocr_quadros_video`) et le codage intégral : `funcao_principal`, `acoes_solicitadas`, `plataformas_mencionadas` et les marqueurs binaires `imaginario_algoritmico`, `militarizacao`, `urgencia`, `prova_social`, plus `alvo`, `tom`, `confianca` et `evidencia_codificacao`.

### `snapshots/20261029T021046Z/auditoria/`

- `contrato_reconciliacao.json` — règles de réconciliation entre enregistrements et médias
- `proveniencia.json` — chaîne de provenance de la collecte (instantané de la sauvegarde déchiffrée)
- `resumo.json` — décomptes agrégés de vérification (messages, médias, hachages)

## 📄 Rapports PDF (4 langues)

Le rapport technico-scientifique complet est disponible sous [`relatorios/`](relatorios/) en quatre langues : portugais du Brésil, anglais, français et espagnol. Il contient : résumé exécutif, méthodologie (collecte, codage avec double codage à l'aveugle, validation kappa), résultats (typologie des 1 018 unités, rythme temporel, marqueurs transversaux, plateformes mentionnées), les épisodes empiriques E1–E11, discussion théorique et références complètes.

## ⚖️ Considérations éthiques

- Le canal EXÉRCITO DO LULA est **public** ; les publications ont été capturées via la fonction d'export de WhatsApp lui-même, sans accès à des conversations privées.
- Le contenu publié par des tiers (noms d'utilisateur, voix dans les audios, visages dans les vidéos) est traité comme donnée de recherche selon les lignes directrices [AoIR](https://aoir.org/reports/ethics3.pdf) pour la recherche sur Internet.
- L'identification d'individus non publics a été évitée dans le rapport ; dans les données brutes, les fichiers multimédias préservent le contenu original tel que publié publiquement dans le canal.
- Questions éthiques ou demandes de retrait : **labhdufba@gmail.com**.

## 📚 Citation

```bibtex
@techreport{nascimento2026exercito,
  title = {Ativismo digital, coordenação de engajamento e imaginários algorítmicos no canal de WhatsApp EXÉRCITO DO LULA},
  author = {Nascimento, Leonardo and Brasil, Eric and Sodr{\'e} Andrade, Ricardo and Cesarino, Let{\'i}cia and Kalil, Isabela and Belas, L{\'i}dia},
  year = {2026},
  institution = {LABHDUFBA — Laboratoire des humanités numériques, Université fédérale de Bahia},
  address = {Salvador},
  url = {https://github.com/LABHDUFBA/exercito-do-lula}
}
```

**Contact :** LABHDUFBA · labhdufba@gmail.com · Salvador, BA, Brésil.

## 🔗 Références

- BBC News Brasil. Luiz Fernando Toledo. *Como Janones montou um exército digital na campanha de Lula — e qual espaço pode ter no novo governo*. 26 oct. 2026.
- InternetLab ; Aláfia Lab ; Artigo 19 ; Conectas Direitos Humanos. *Coordenação não é inautenticidade: parâmetros técnicos para a análise de mobilizações digitais*. Avis technique conjoint. São Paulo, oct. 2026.
- O Globo. Mariana Muniz. *Informação sobre recursos, elo com campanhas, direcionamento: veja as regras para canais no WhatsApp definidas pelo TSE*. 17 oct. 2026.
- Agência Brasil. André Richter. *TSE atende Flávio e manda suspender canal do WhatsApp Exército do Lula*. 11 oct. 2026.

---

<div align="center">

**LABHDUFBA** — Laboratoire des humanités numériques · UFBA
Salvador · Bahia · Brésil · Octobre 2026

</div>

---

<h2 id="espanol">🇪🇸 Español</h2>

# EXÉRCITO DO LULA — Canal de WhatsApp (2ª vuelta, elecciones 2026)

Datos y materiales de investigación del informe técnico-científico **"Ativismo digital, coordenação de engajamento e imaginários algorítmicos no canal de WhatsApp EXÉRCITO DO LULA"** (*Activismo digital, coordinación del compromiso e imaginarios algorítmicos en el canal de WhatsApp EXÉRCITO DO LULA*; Nascimento, Brasil, Sodré, Cesarino, Kalil & Belas, 2026), producido en el marco del [LABHDUFBA](https://labhdufba.github.io/) — el Laboratorio de Humanidades Digitales de la Universidad Federal de Bahía (UFBA), Brasil.

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
├── README.md                       ← este arquivo (4 idiomas em seções)
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
  url = {https://github.com/LABHDUFBA/exercito-do-lula}
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
