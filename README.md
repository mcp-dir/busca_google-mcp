# Buscador Google

### Buscador Google for Claude, ChatGPT and AI agents

Search Google straight from your AI agent. Web results, images, videos, news, products, scholarly articles and patents, plus local business lookup with phone, address and rating, and full text extraction from any page. Accepts up to 100 queries in a single call. Hosted by the platform, no credentials, you pay per query.

- 📊 **11 tools**
- 🔒 **Read-only**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Versão em português](README.pt.md) · [Full docs (PT-BR)](docs/) · [Agent skill](skills/)

---

## One-click install

### Claude (Web and Desktop)

Anthropic unified MCP installation at `claude.ai/customize/connectors`. **The same link works for Claude Web and Claude Desktop** (just be logged in):

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (if the deeplink does not open): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → paste **Name** `Buscador Google` and **URL** `https://api.mcp.ai/p_busca_google`.

### Cursor

[➕ Install Buscador Google in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=busca_google&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9idXNjYV9nb29nbGUifQ==)

### VS Code (Copilot Chat)

[➕ Install Buscador Google in VS Code](vscode:mcp/install?name=busca_google&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_busca_google%22%7D)

### ChatGPT, Manus, OpenClaw and 40+ other clients

Works with any MCP client that speaks **MCP over HTTP**. The server URL is always:

```
https://api.mcp.ai/p_busca_google
```

Per-client details: [INSTALL.md](INSTALL.md).

---

## Example prompts

```
Find dental clinics in Campinas with phone and rating, and build a prospecting list
Search last week's news about open finance and summarize it
Search "best CRMs 2026", open the top 3 results and compare them
```

---

## 11 tools available

| Tool | Description |
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

Details for each tool: [docs/ferramentas.md](docs/ferramentas.md) (PT-BR)

---

## Pricing

Prepaid credit wallet, pay per use. See [docs/precos.md](docs/precos.md) (PT-BR).

---

## Privacy & data protection

- **Read-only**, no tool changes data at the source.
- **Sub-processors**: Serper, the LLM host you choose (Claude, ChatGPT, Cursor, your own agent). Full list in [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Data returned by the tools is sent to **the LLM host you choose**, a sub-processor outside our control. We recommend plans with training opt-out.

---

## FAQ

**Is the server open source?**
The server is proprietary (hosted). This repository is the public wrapper with manifests, docs and skills, all MIT.

**Can I use it with my own agent (not Claude/Cursor)?**
Yes, any client that speaks MCP over HTTP. URL: `https://api.mcp.ai/p_busca_google`.


---

## Support

- 📧 [busca_google@mcp.ai](mailto:busca_google@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/busca_google-mcp/issues)
- 📄 [docs/](docs/)

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_busca_google` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
