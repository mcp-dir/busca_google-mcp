---
name: busca_google-mcp
description: Skill da REST API do Buscador Google na MCP.AI: 11 endpoints em /api/busca_google. Busque no Google direto do seu agente de IA. Resultados da web, imagens, vídeos, notícias, produtos, artigos acadêmicos e patentes, mais a busca de estabelecimentos com telefone, endereço e nota, e a leitura do texto de qualquer página. Aceita até 100 consultas numa chamada só. Hospedado pela plataforma, sem credenciais, você paga por consulta. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Buscador Google — REST API skill

Você tem acesso à **Buscador Google** REST API na MCP.AI.

> Busque no Google direto do seu agente de IA. Resultados da web, imagens, vídeos, notícias, produtos, artigos acadêmicos e patentes, mais a busca de estabelecimentos com telefone, endereço e nota, e a leitura do texto de qualquer página. Aceita até 100 consultas numa chamada só. Hospedado pela plataforma, sem credenciais, você paga por consulta.

## Base URL

```
https://api.mcp.ai/api/busca_google
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/busca_google/academico \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"consultas":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/busca_google/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (11)

#### `busca_google_academico`

Busca artigos no Google Acadêmico com título, autores, publicação, ano e número de citações. _(POST /api/busca_google/academico)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `consultas` | string[] | Sim | Consultas a buscar, até 100 por chamada, resolvidas numa única ida ao provedor. Cada consulta é cobrada. Ex.: ["open banking regulation brazil"] |
| `pais` | string | Não | País dos resultados, código de 2 letras (br, us, pt). Padrão: br. |
| `idioma` | string | Não | Idioma dos resultados (pt, en, es). Padrão: pt. |
| `limite` | integer | Não | Quantos resultados pedir por consulta (padrão 10). Não muda o custo, mas o Google costuma devolver menos do que se pede. |
| `periodo` | string | Não | Recorta por recência: qdr:h última hora, qdr:d último dia, qdr:w última semana, qdr:m último mês, qdr:y último ano. Sem isso, sem recorte de data. (qdr:h, qdr:d, qdr:w, qdr:m, qdr:y) |
| `local` | string | Não | Cidade de origem da busca, no formato do Google (ex.: "Sao Paulo, State of Sao Paulo, Brazil"). Muda resultado local e ranking. |
| `pagina` | integer | Não | Página de resultados (padrão 1). Cada página é uma consulta cobrada. |

#### `busca_google_imagens`

Busca imagens no Google e devolve a URL da imagem, a miniatura, as dimensões e a página de origem. _(POST /api/busca_google/imagens)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `consultas` | string[] | Sim | Consultas a buscar, até 100 por chamada, resolvidas numa única ida ao provedor. Cada consulta é cobrada. Ex.: ["capivara", "logo do Pix"] |
| `pais` | string | Não | País dos resultados, código de 2 letras (br, us, pt). Padrão: br. |
| `idioma` | string | Não | Idioma dos resultados (pt, en, es). Padrão: pt. |
| `limite` | integer | Não | Quantos resultados pedir por consulta (padrão 10). Não muda o custo, mas o Google costuma devolver menos do que se pede. |
| `periodo` | string | Não | Recorta por recência: qdr:h última hora, qdr:d último dia, qdr:w última semana, qdr:m último mês, qdr:y último ano. Sem isso, sem recorte de data. (qdr:h, qdr:d, qdr:w, qdr:m, qdr:y) |
| `local` | string | Não | Cidade de origem da busca, no formato do Google (ex.: "Sao Paulo, State of Sao Paulo, Brazil"). Muda resultado local e ranking. |
| `pagina` | integer | Não | Página de resultados (padrão 1). Cada página é uma consulta cobrada. |

#### `busca_google_lugares`

Busca estabelecimentos no Google com endereço, telefone, site, nota e número de avaliações. _(POST /api/busca_google/lugares)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `consultas` | string[] | Sim | Consultas a buscar, até 100 por chamada, resolvidas numa única ida ao provedor. Cada consulta é cobrada. Ex.: ["clínica odontológica em Campinas", "contador em Sorocaba"] |
| `pais` | string | Não | País dos resultados, código de 2 letras (br, us, pt). Padrão: br. |
| `idioma` | string | Não | Idioma dos resultados (pt, en, es). Padrão: pt. |
| `limite` | integer | Não | Quantos resultados pedir por consulta (padrão 10). Não muda o custo, mas o Google costuma devolver menos do que se pede. |
| `periodo` | string | Não | Recorta por recência: qdr:h última hora, qdr:d último dia, qdr:w última semana, qdr:m último mês, qdr:y último ano. Sem isso, sem recorte de data. (qdr:h, qdr:d, qdr:w, qdr:m, qdr:y) |
| `local` | string | Não | Cidade de origem da busca, no formato do Google (ex.: "Sao Paulo, State of Sao Paulo, Brazil"). Muda resultado local e ranking. |
| `pagina` | integer | Não | Página de resultados (padrão 1). Cada página é uma consulta cobrada. |

#### `busca_google_mapas`

Busca no Google Maps e devolve o dobro de estabelecimentos por consulta, com coordenadas de latitude e longitude. _(POST /api/busca_google/mapas)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `consultas` | string[] | Sim | Consultas a buscar, até 100 por chamada, resolvidas numa única ida ao provedor. Cada consulta é cobrada. Ex.: ["restaurante japonês em Pinheiros"] |
| `pais` | string | Não | País dos resultados, código de 2 letras (br, us, pt). Padrão: br. |
| `idioma` | string | Não | Idioma dos resultados (pt, en, es). Padrão: pt. |
| `limite` | integer | Não | Quantos resultados pedir por consulta (padrão 10). Não muda o custo, mas o Google costuma devolver menos do que se pede. |
| `periodo` | string | Não | Recorta por recência: qdr:h última hora, qdr:d último dia, qdr:w última semana, qdr:m último mês, qdr:y último ano. Sem isso, sem recorte de data. (qdr:h, qdr:d, qdr:w, qdr:m, qdr:y) |
| `local` | string | Não | Cidade de origem da busca, no formato do Google (ex.: "Sao Paulo, State of Sao Paulo, Brazil"). Muda resultado local e ranking. |
| `pagina` | integer | Não | Página de resultados (padrão 1). Cada página é uma consulta cobrada. |

#### `busca_google_noticias`

Busca notícias no Google News com título, fonte, data e link. _(POST /api/busca_google/noticias)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `consultas` | string[] | Sim | Consultas a buscar, até 100 por chamada, resolvidas numa única ida ao provedor. Cada consulta é cobrada. Ex.: ["Banco Central Pix", "reforma tributária"] |
| `pais` | string | Não | País dos resultados, código de 2 letras (br, us, pt). Padrão: br. |
| `idioma` | string | Não | Idioma dos resultados (pt, en, es). Padrão: pt. |
| `limite` | integer | Não | Quantos resultados pedir por consulta (padrão 10). Não muda o custo, mas o Google costuma devolver menos do que se pede. |
| `periodo` | string | Não | Recorta por recência: qdr:h última hora, qdr:d último dia, qdr:w última semana, qdr:m último mês, qdr:y último ano. Sem isso, sem recorte de data. (qdr:h, qdr:d, qdr:w, qdr:m, qdr:y) |
| `local` | string | Não | Cidade de origem da busca, no formato do Google (ex.: "Sao Paulo, State of Sao Paulo, Brazil"). Muda resultado local e ranking. |
| `pagina` | integer | Não | Página de resultados (padrão 1). Cada página é uma consulta cobrada. |

#### `busca_google_pagina`

Lê uma página da web e devolve o texto limpo mais os metadados dela. _(POST /api/busca_google/pagina)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `urls` | string[] | Sim | URLs http(s) a ler, até 100 por chamada. Cada URL é cobrada. |
| `markdown` | boolean | Não | Também devolver o conteúdo em markdown, além do texto puro. Padrão: sim. |

#### `busca_google_patentes`

Busca patentes no Google Patents com título, número, depositante e data. _(POST /api/busca_google/patentes)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `consultas` | string[] | Sim | Consultas a buscar, até 100 por chamada, resolvidas numa única ida ao provedor. Cada consulta é cobrada. Ex.: ["painel solar bifacial"] |
| `pais` | string | Não | País dos resultados, código de 2 letras (br, us, pt). Padrão: br. |
| `idioma` | string | Não | Idioma dos resultados (pt, en, es). Padrão: pt. |
| `limite` | integer | Não | Quantos resultados pedir por consulta (padrão 10). Não muda o custo, mas o Google costuma devolver menos do que se pede. |
| `periodo` | string | Não | Recorta por recência: qdr:h última hora, qdr:d último dia, qdr:w última semana, qdr:m último mês, qdr:y último ano. Sem isso, sem recorte de data. (qdr:h, qdr:d, qdr:w, qdr:m, qdr:y) |
| `local` | string | Não | Cidade de origem da busca, no formato do Google (ex.: "Sao Paulo, State of Sao Paulo, Brazil"). Muda resultado local e ranking. |
| `pagina` | integer | Não | Página de resultados (padrão 1). Cada página é uma consulta cobrada. |

#### `busca_google_shopping`

Busca produtos no Google Shopping com preço, loja, nota e imagem. _(POST /api/busca_google/shopping)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `consultas` | string[] | Sim | Consultas a buscar, até 100 por chamada, resolvidas numa única ida ao provedor. Cada consulta é cobrada. Ex.: ["teclado mecânico 75%"] |
| `pais` | string | Não | País dos resultados, código de 2 letras (br, us, pt). Padrão: br. |
| `idioma` | string | Não | Idioma dos resultados (pt, en, es). Padrão: pt. |
| `limite` | integer | Não | Quantos resultados pedir por consulta (padrão 10). Não muda o custo, mas o Google costuma devolver menos do que se pede. |
| `periodo` | string | Não | Recorta por recência: qdr:h última hora, qdr:d último dia, qdr:w última semana, qdr:m último mês, qdr:y último ano. Sem isso, sem recorte de data. (qdr:h, qdr:d, qdr:w, qdr:m, qdr:y) |
| `local` | string | Não | Cidade de origem da busca, no formato do Google (ex.: "Sao Paulo, State of Sao Paulo, Brazil"). Muda resultado local e ranking. |
| `pagina` | integer | Não | Página de resultados (padrão 1). Cada página é uma consulta cobrada. |

#### `busca_google_sugestoes`

Devolve as sugestões de autocompletar do Google para um termo. _(POST /api/busca_google/sugestoes)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `consultas` | string[] | Sim | Consultas a buscar, até 100 por chamada, resolvidas numa única ida ao provedor. Cada consulta é cobrada. Ex.: ["open financ", "melhor crm"] |
| `pais` | string | Não | País dos resultados, código de 2 letras (br, us, pt). Padrão: br. |
| `idioma` | string | Não | Idioma dos resultados (pt, en, es). Padrão: pt. |

#### `busca_google_videos`

Busca vídeos no Google com título, canal, duração e link. _(POST /api/busca_google/videos)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `consultas` | string[] | Sim | Consultas a buscar, até 100 por chamada, resolvidas numa única ida ao provedor. Cada consulta é cobrada. Ex.: ["tutorial open finance"] |
| `pais` | string | Não | País dos resultados, código de 2 letras (br, us, pt). Padrão: br. |
| `idioma` | string | Não | Idioma dos resultados (pt, en, es). Padrão: pt. |
| `limite` | integer | Não | Quantos resultados pedir por consulta (padrão 10). Não muda o custo, mas o Google costuma devolver menos do que se pede. |
| `periodo` | string | Não | Recorta por recência: qdr:h última hora, qdr:d último dia, qdr:w última semana, qdr:m último mês, qdr:y último ano. Sem isso, sem recorte de data. (qdr:h, qdr:d, qdr:w, qdr:m, qdr:y) |
| `local` | string | Não | Cidade de origem da busca, no formato do Google (ex.: "Sao Paulo, State of Sao Paulo, Brazil"). Muda resultado local e ranking. |
| `pagina` | integer | Não | Página de resultados (padrão 1). Cada página é uma consulta cobrada. |

#### `busca_google_web`

Busca na web pelo Google e devolve os resultados orgânicos com título, link e trecho, mais a resposta direta e o painel de conhecimento quando existem. _(POST /api/busca_google/web)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `consultas` | string[] | Sim | Consultas a buscar, até 100 por chamada, resolvidas numa única ida ao provedor. Cada consulta é cobrada. Ex.: ["melhores CRMs 2026", "o que é open finance"] |
| `pais` | string | Não | País dos resultados, código de 2 letras (br, us, pt). Padrão: br. |
| `idioma` | string | Não | Idioma dos resultados (pt, en, es). Padrão: pt. |
| `limite` | integer | Não | Quantos resultados pedir por consulta (padrão 10). Não muda o custo, mas o Google costuma devolver menos do que se pede. |
| `periodo` | string | Não | Recorta por recência: qdr:h última hora, qdr:d último dia, qdr:w última semana, qdr:m último mês, qdr:y último ano. Sem isso, sem recorte de data. (qdr:h, qdr:d, qdr:w, qdr:m, qdr:y) |
| `local` | string | Não | Cidade de origem da busca, no formato do Google (ex.: "Sao Paulo, State of Sao Paulo, Brazil"). Muda resultado local e ranking. |
| `pagina` | integer | Não | Página de resultados (padrão 1). Cada página é uma consulta cobrada. |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_busca_google` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
