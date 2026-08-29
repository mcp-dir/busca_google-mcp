# Buscador Google

### Buscador Google para Claude, ChatGPT e agentes de IA

Busque no Google direto do seu agente de IA. Resultados da web, imagens, vídeos, notícias, produtos, artigos acadêmicos e patentes, mais a busca de estabelecimentos com telefone, endereço e nota, e a leitura do texto de qualquer página. Aceita até 100 consultas numa chamada só. Hospedado pela plataforma, sem credenciais, você paga por consulta.

- 📊 **11 ferramentas**
- 🔒 **Somente leitura**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `Buscador Google` e **URL** `https://api.mcp.ai/p_busca_google`.

### Cursor

[➕ Instalar Buscador Google no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=busca_google&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9idXNjYV9nb29nbGUifQ==)

### VS Code (Copilot Chat)

[➕ Instalar Buscador Google no VS Code](vscode:mcp/install?name=busca_google&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_busca_google%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_busca_google
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Ache clínicas odontológicas em Campinas com telefone e nota, e monte uma lista de prospecção
Busque as notícias da última semana sobre open finance e resuma
Busque "melhores CRMs 2026", abra os 3 primeiros resultados e compare
```

---

## 11 ferramentas disponíveis

| Tool | Descrição |
|---|---|
| `busca_google_web` | Busca na web pelo Google e devolve os resultados orgânicos com título, link e trecho, mais a resposta direta e o painel de conhecimento quando existem. |
| `busca_google_lugares` | Busca estabelecimentos no Google com endereço, telefone, site, nota e número de avaliações. |
| `busca_google_mapas` | Busca no Google Maps e devolve o dobro de estabelecimentos por consulta, com coordenadas de latitude e longitude. |
| `busca_google_noticias` | Busca notícias no Google News com título, fonte, data e link. |
| `busca_google_imagens` | Busca imagens no Google e devolve a URL da imagem, a miniatura, as dimensões e a página de origem. |
| `busca_google_videos` | Busca vídeos no Google com título, canal, duração e link. |
| `busca_google_shopping` | Busca produtos no Google Shopping com preço, loja, nota e imagem. |
| `busca_google_academico` | Busca artigos no Google Acadêmico com título, autores, publicação, ano e número de citações. |
| `busca_google_patentes` | Busca patentes no Google Patents com título, número, depositante e data. |
| `busca_google_sugestoes` | Devolve as sugestões de autocompletar do Google para um termo. |
| `busca_google_pagina` | Lê uma página da web e devolve o texto limpo mais os metadados dela. |

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Pré-pago (carteira de créditos), paga por uso. Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Somente leitura**, nenhuma ferramenta altera dados na origem.
- **Sub-processadores**: Serper, o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_busca_google`.


---

## Suporte

- 📧 [busca_google@mcp.ai](mailto:busca_google@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/busca_google-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_busca_google` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
