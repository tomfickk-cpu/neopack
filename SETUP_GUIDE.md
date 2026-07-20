# OpenCode Configuration Pack

Pacote portátil de configuração do OpenCode com todos os agentes, MCPs, LSPs e formatters.

## Pré-requisitos

Antes de começar, instale no computador destino:

1. **Node.js** (v18+) — https://nodejs.org
2. **Python** (v3.10+) — https://python.org
3. **Go** (v1.21+) — https://go.dev
4. **Git** — https://git-scm.com

## Instalação Rápida

Execute o PowerShell como Administrador e rode:

```powershell
.\setup.ps1
```

O script instala automaticamente:
- OpenCode CLI (npm global)
- Pacotes npm globais (LSPs HTML, CSS, JSON, Markdown)
- Pacotes Python (ruff, pandas, numpy, openpyxl)
- Cria as pastas de configuração
- Copia os arquivos de agente e config

## Instalação Manual - Passo a Passo

### 1. Instalar OpenCode CLI

```powershell
npm install -g opencode-ai
```

### 2. Instalar LSPs Globais

```powershell
npm install -g vscode-langservers-extracted
```

### 3. Instalar Pacotes Python

```powershell
pip install ruff pandas numpy openpyxl
```

### 4. Configurar Pastas

```powershell
# Config global
New-Item -ItemType Directory -Path "$env:LOCALAPPDATA\opencode" -Force
Copy-Item configs\opencode.global.jsonc "$env:USERPROFILE\.config\opencode\opencode.jsonc" -Force

# Config projeto (ajuste o caminho)
Copy-Item configs\opencode.project.json ".\projeto\.opencode\opencode.json" -Force
Copy-Item agents\* ".\projeto\.opencode\agents\" -Force
```

### 5. Autenticar Provedores

```powershell
opencode auth login --provider opencode --method api
opencode auth login --provider opencode-go --method api
```

### 6. Instalar MCP Servers

```powershell
opencode mcp add puppeteer -- npx @anthropic/mcp-server-puppeteer --headless
opencode mcp add playwright -- npx @anthropic/mcp-server-playwright
opencode mcp add github -- npx @anthropic/mcp-server-github
opencode mcp add brave-search -- npx @anthropic/mcp-server-brave-search
opencode mcp add sequential-thinking -- npx @modelcontextprotocol/server-sequential-thinking
opencode mcp add sqlite -- npx @modelcontextprotocol/server-sqlite "C:\caminho\projeto\data.db"
opencode mcp add memory -- npx @modelcontextprotocol/server-memory
opencode mcp add filesystem -- npx @modelcontextprotocol/server-filesystem "C:\caminho\projeto"
```

## Estrutura de Pastas Esperada

```
projeto/
├── .opencode/
│   ├── opencode.json
│   ├── agents/
│   │   ├── build-assistant.md
│   │   ├── code-review.md
│   │   ├── content-mapper.md
│   │   ├── data-pipeline.md
│   │   ├── db-agent.md
│   │   ├── go-dev.md
│   │   ├── image-processor.md
│   │   ├── pdf-processor.md
│   │   ├── script-automation.md
│   │   ├── seo-qa.md
│   │   └── web-dev.md
│   └── node_modules/
└── data.db
```

## Arquivos de Configuração

| Arquivo | Destino | Descrição |
|---------|---------|-----------|
| `configs/opencode.global.jsonc` | `~\.config\opencode\opencode.jsonc` | Config global (LSPs, formatters, MCPs, modelo) |
| `configs/opencode.project.json` | `projeto\.opencode\opencode.json` | Config do projeto (agentes, plugins) |
| `agents/*.md` | `projeto\.opencode\agents\` | Definições dos agentes especialistas |

## Modelo Padrão

O modelo padrão configurado é `opencode/deepseek-v4-flash` (gratuito). 
Para usar modelos pagos Go, use `@opencode-go/qwen3.7-plus` na conversa ou `/model opencode-go/qwen3.7-max`.
