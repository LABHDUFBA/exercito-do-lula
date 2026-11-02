# EXÉRCITO DO LULA — Canal WhatsApp (2e tour, élections 2026)

[![README en français](https://img.shields.io/badge/README-fran%C3%A7ais-blueviolet)](README-fr.md)
[![README em português](https://img.shields.io/badge/README-portugu%C3%AAs-brightgreen)](README-ptbr.md)
[![English README](https://img.shields.io/badge/README-english-blue)](README-en.md)
[![README en español](https://img.shields.io/badge/README-espa%C3%B1ol-orange)](README-es.md)

Données et matériaux de recherche du rapport technico-scientifique **« Ativismo digital, coordenação de engajamento e imaginários algorítmicos no canal de WhatsApp EXÉRCITO DO LULA »** (*Militantisme numérique, coordination de l'engagement et imaginaires algorithmiques dans le canal WhatsApp EXÉRCITO DO LULA* ; Nascimento, Brasil, Sodré, Cesarino, Kalil & Belas, 2026), produit dans le cadre du [LABHDUFBA](https://labhdufba.github.io/) — le Laboratoire des humanités numériques de l'Université fédérale de Bahia (UFBA), Brésil.

## 📌 Sommaire

- [Contexte de la recherche](#-contexte-de-la-recherche)
- [Contenu du dépôt](#-contenu-du-dépôt)
- [Dictionnaire des données](#-dictionnaire-des-données)
- [Rapports PDF (4 langues)](#-rapports-pdf-4-langues)
- [Considérations éthiques](#-considérations-éthiques)
- [Citation](#-citation)
- [Références](#-références)

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
├── README-ptbr.md · README-en.md · README-fr.md · README-es.md
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