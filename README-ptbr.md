# EXÉRCITO DO LULA — Canal de WhatsApp (2º turno, eleições 2026)

[![README em português](https://img.shields.io/badge/README-portugu%C3%AAs-brightgreen)](README-ptbr.md)
[![English README](https://img.shields.io/badge/README-english-blue)](README-en.md)
[![README en français](https://img.shields.io/badge/README-fran%C3%A7ais-blueviolet)](README-fr.md)
[![README en español](https://img.shields.io/badge/README-espa%C3%B1ol-orange)](README-es.md)

Dados e materiais de pesquisa do relatório técnico-científico **"Ativismo digital, coordenação de engajamento e imaginários algorítmicos no canal de WhatsApp EXÉRCITO DO LULA"** (Nascimento, Brasil, Sodré, Cesarino, Kalil & Belas, 2026), produzido no âmbito do [LABHDUFBA](https://labhdufba.github.io/) — Laboratório de Humanidades Digitais da Universidade Federal da Bahia (UFBA).

## 📌 Sumário

- [Contexto da pesquisa](#-contexto-da-pesquisa)
- [Conteúdo do repositório](#-conteúdo-do-repositório)
- [Dicionário de dados](#-dicionário-de-dados)
- [Relatórios em PDF (4 idiomas)](#-relatórios-em-pdf-4-idiomas)
- [Considerações éticas](#-considerações-éticas)
- [Citação](#-citação)
- [Referências](#-referências)

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
├── README-ptbr.md                  ← este arquivo
├── README-en.md · README-fr.md · README-es.md
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