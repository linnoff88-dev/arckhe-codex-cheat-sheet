ï»¿<div align="center">

# Codex Cheat Sheet

<a href="https://openai.com/codex/"><img width="763" height="341" alt="Codex cheat sheet" src="assets/image.png" /></a>

> **Seu guia completo para dominar o OpenAI Codex ê¢â¬â do zero ao produtivo em minutos.**

Uma referêÂªncia prêÂ¡tica para usar o OpenAI Codex CLI com eficiêÂªncia. O foco sêÂ£o padrêÂµes que ajudam vocêÂª a pensar criticamente sobre o que delegar e o que fazer vocêÂª mesmo.

**Baseado na documentaêÂ§êÂ£o oficial do OpenAI Codex** ê¢â¬â todos os comandos e exemplos vêÂªm da [documentaêÂ§êÂ£o oficial do Codex](https://developers.openai.com/codex). Para informaêÂ§êÂ£o sempre atualizada, consulte a doc oficial.

ê°Å¸â¡Âºê°Å¸â¡Â¸ [English version](README.md)

</div>

## ê°Å¸ââ Guia de uso

Guia completo (landing + passo a passo): **https://linnoff88-dev.github.io/

## InêÂ­cio rêÂ¡pido

```bash
# Instalar com o instalador oficial (recomendado)
curl -fsSL https://chatgpt.com/codex/install.sh | sh

# Ou com npm
npm install -g @openai/codex

# Ou com Homebrew
brew install --cask codex

# Ou com pnpm (gerenciador oficial do monorepo)
pnpm install -g @openai/codex

# Windows: script oficial de instalaêÂ§êÂ£o
powershell -ExecutionPolicy ByPass -c "irm https://chatgpt.com/codex/install.ps1 | iex"

# Auto-atualizaêÂ§êÂ£o (instalaêÂ§êÂµes feitas pelo instalador)
codex update

# Abrir o Codex
codex

# Ver a versêÂ£o
codex --version
```

## êÂndice

- **[NêÂ­vel 1: Primeiros passos](#nêÂ­vel-1-primeiros-passos)**
- **[NêÂ­vel 2: Comandos bêÂ¡sicos](#nêÂ­vel-2-comandos-bêÂ¡sicos)**
- **[NêÂ­vel 3: Uso intermediêÂ¡rio](#nêÂ­vel-3-uso-intermediêÂ¡rio)**
- **[NêÂ­vel 4: Recursos avanêÂ§ados](#nêÂ­vel-4-recursos-avanêÂ§ados)**
- **[Skills](#skills)** ê¢â¬â capacidades nativas e reutilizêÂ¡veis
- **[NêÂ­vel 5: Workflows de especialista](#nêÂ­vel-5-workflows-de-especialista)**

## NêÂ­vel 1: Primeiros passos

Comandos essenciais para comeêÂ§ar com o Codex.

<details>
<summary><strong>InstalaêÂ§êÂ£o</strong></summary>

```bash
# Instalar globalmente com npm
npm install -g @openai/codex

# Instalar com Homebrew (macOS)
brew install --cask codex

# Instalar com pnpm (gerenciador oficial do monorepo)
pnpm install -g @openai/codex

# Instalador oficial standalone (macOS/Linux)
curl -fsSL https://chatgpt.com/codex/install.sh | sh

# Windows: script oficial de instalaêÂ§êÂ£o
powershell -ExecutionPolicy ByPass -c "irm https://chatgpt.com/codex/install.ps1 | iex"

# Atualizar com npm
npm install -g @openai/codex

# Atualizar com Homebrew
brew upgrade --cask codex

# Auto-atualizaêÂ§êÂ£o (quando a release instalada suportar)
codex update

# Baixar o binêÂ¡rio das releases do GitHub
# Acesse: https://github.com/openai/codex/releases/latest
```

</details>

<details>
<summary><strong>Primeiros comandos</strong></summary>

```bash
# Iniciar o modo interativo
codex

# Rodar com um prompt especêÂ­fico
codex "explain this project"

# ExecuêÂ§êÂ£o nêÂ£o interativa
codex exec "explain utils.ts"
```

</details>

<details>
<summary><strong>AutenticaêÂ§êÂ£o</strong></summary>

```bash
# Entrar com a conta ChatGPT (recomendado)
codex
# Depois escolha "Sign in with ChatGPT"

# Usar chave de API (alternativa ê¢â¬â cobranêÂ§a por uso)
printenv OPENAI_API_KEY | codex login --with-api-key
# Ou a partir de um arquivo:
codex login --with-api-key < my_key.txt

# Usar um access token
printenv CODEX_ACCESS_TOKEN | codex login --with-access-token

# AutenticaêÂ§êÂ£o por dispositivo
codex login --device-auth

# Conferir o status do login (saêÂ­da 0 = credenciais presentes)
codex login status
```

</details>

<details>
<summary><strong>NavegaêÂ§êÂ£o bêÂ¡sica</strong></summary>

```bash
# Atalhos de teclado
Ctrl+C                    # Cancela a operaêÂ§êÂ£o atual (ou use /exit para fechar a sessêÂ£o)
Tab                       # Enfileira o prêÂ³ximo prompt, slash command ou comando de shell enquanto o Codex trabalha
ê¢â â/ê¢â â                       # Recupera o histêÂ³rico de rascunhos
Esc Esc                   # Edita a mensagem anterior (composer vazio; bifurca a conversa daquele ponto)
Ctrl+R                    # Busca no histêÂ³rico de prompts
Ctrl+O                    # Copia a êÂºltima saêÂ­da concluêÂ­da
Enter                     # Injeta novas instruêÂ§êÂµes no turno atual
!comando                  # Roda um comando local de shell sob a polêÂ­tica de aprovaêÂ§êÂ£o/sandbox atual

# Entrada especial
@                         # Dispara a busca de arquivos (fuzzy find)
```

</details>

## NêÂ­vel 2: Comandos bêÂ¡sicos

Comandos centrais para o dia a dia.

<details>
<summary><strong>Slash commands ê¢â¬â essenciais</strong></summary>

```bash
/model                    # Escolhe o modelo e o esforêÂ§o de raciocêÂ­nio
/permissions              # Configura o que o Codex pode fazer sem aprovaêÂ§êÂ£o
/fast                     # Liga/desliga o modo Fast nos modelos suportados
/personality              # Escolhe um estilo de comunicaêÂ§êÂ£o
/review                   # Revisa as mudanêÂ§as atuais e aponta problemas
/new                      # ComeêÂ§a um novo chat durante a conversa
/init                     # Cria um arquivo AGENTS.md com instruêÂ§êÂµes
/compact                  # Resume a conversa para nêÂ£o estourar o contexto
/diff                     # Mostra o git diff (inclusive arquivos nêÂ£o rastreados)
/mention                  # Menciona um arquivo
/status                   # Mostra a config da sessêÂ£o e o uso de tokens
/mcp                      # Lista as ferramentas MCP configuradas
/side                     # Abre uma conversa lateral efêÂªmera (/btw)
/fork                     # Bifurca a conversa atual em uma nova thread
/ps                       # Mostra os terminais em segundo plano e suas saêÂ­das
/stop                     # Para todos os terminais em segundo plano
/logout                   # Sai da conta do Codex
/quit                     # Fecha o Codex
/exit                     # Fecha o Codex
/feedback                 # Envia logs para os mantenedores
/goal                     # Define ou mostra um objetivo persistente da tarefa
/plan                     # Entra no modo de plano, para planejamento multi-etapas
/approve                  # Aprova uma nova tentativa apêÂ³s negativa da revisêÂ£o automêÂ¡tica
/copy                     # Copia a êÂºltima saêÂ­da concluêÂ­da (ou Ctrl+O)
/clear                    # Limpa o terminal e comeêÂ§a um novo chat
/rename                   # Renomeia o chat atual
/archive                  # Arquiva a sessêÂ£o atual e fecha o Codex
/delete                   # Apaga a sessêÂ£o atual em definitivo e fecha
/resume                   # Retoma um chat salvo da sua lista de sessêÂµes
/app                      # Continua a sessêÂ£o no app desktop do ChatGPT
/agent                    # Troca a thread de agente ativa (tambêÂ©m /subagents)
/apps                     # Navega pelos apps (conectores) e insere no prompt
/plugins                  # Navega pelos plugins instalados e disponêÂ­veis
/hooks                    # VêÂª e gerencia os hooks de ciclo de vida
/memories                 # Configura o uso e a geraêÂ§êÂ£o de memêÂ³ria
/import                   # Importa a configuraêÂ§êÂ£o do Claude Code ou do Cursor
/experimental             # Liga/desliga recursos experimentais
/usage                    # Mostra o uso de tokens da conta
/debug-config             # Imprime o diagnêÂ³stico das camadas de config
/statusline               # Configura os itens do rodapêÂ© da TUI
/title                    # Configura os itens do têÂ­tulo do terminal
/theme                    # Escolhe um tema de sintaxe
/pets                     # Escolhe ou esconde um bichinho de terminal (/pet)
/keymap                   # Remapeia os atalhos de teclado da TUI
/vim                      # Liga/desliga o modo Vim no composer
/ide                      # Inclui os arquivos abertos e o contexto da IDE
/raw                      # Liga/desliga o modo de scrollback bruto
/skills                   # Navega e usa as skills

# /debug nêÂ£o êÂ© mais documentado; use /debug-config para diagnêÂ³stico de config
```

</details>

<details>
<summary><strong>OperaêÂ§êÂµes com arquivos e diretêÂ³rios</strong></summary>

```bash
# O Codex lêÂª, escreve e edita arquivos
"Leia o conteêÂºdo de src/app.js"
"Crie um arquivo novo chamado utils.js"
"Edite a funêÂ§êÂ£o em main.py para adicionar tratamento de erro"

# Ver a estrutura do projeto
"Explique a estrutura deste projeto"
"Que arquivos existem no diretêÂ³rio src?"
```

</details>

<details>
<summary><strong>Trabalhando com cêÂ³digo</strong></summary>

```bash
# AnêÂ¡lise de cêÂ³digo
"Explique o que este cêÂ³digo faz"
"Revise esta funêÂ§êÂ£o procurando bugs"
"Sugira melhorias para este arquivo"

# GeraêÂ§êÂ£o de cêÂ³digo
"Escreva uma funêÂ§êÂ£o para fazer parse de JSON"
"Crie testes unitêÂ¡rios para este mêÂ³dulo"
"Adicione tratamento de erro a este cêÂ³digo"
```

</details>

<details>
<summary><strong>Gerenciamento de sessêÂµes</strong></summary>

```bash
# Retomar sessêÂµes
codex resume                          # Abre o seletor de sessêÂµes
codex resume --last                   # Retoma a sessêÂ£o mais recente
codex resume <SESSION_ID>             # Retoma uma sessêÂ£o especêÂ­fica pelo ID

# Retomada de sessêÂ£o nêÂ£o interativa
codex exec resume <SESSION_ID>        # Retoma uma sessêÂ£o nêÂ£o interativa
codex exec resume --last              # Retoma a êÂºltima sessêÂ£o nêÂ£o interativa
```

</details>

<details>
<summary><strong>ReferêÂªncia de subcomandos (0.147.0)</strong></summary>

| Comando | Para que serve |
|---|---|
| `codex exec` | Roda de forma nêÂ£o interativa (apelido: `e`) |
| `codex review` | RevisêÂ£o de cêÂ³digo nêÂ£o interativa (veja a [seêÂ§êÂ£o abaixo](#nêÂ­vel-4-recursos-avanêÂ§ados)) |
| `codex login` / `codex logout` | Gerencia a autenticaêÂ§êÂ£o; `codex login status` confere as credenciais |
| `codex resume` | Retoma uma sessêÂ£o salva (seletor; `--last` para a mais recente) |
| `codex fork` | Bifurca uma sessêÂ£o em um novo chat |
| `codex archive` / `codex unarchive` | Arquiva / restaura sessêÂµes salvas |
| `codex delete` | Apaga uma sessêÂ£o em definitivo |
| `codex apply` | Aplica um diff de chat do Codex Cloud na êÂ¡rvore local (apelido: `a`) |
| `codex cloud` | Navega ou executa tarefas do Codex Cloud (experimental) |
| `codex plugin` | Instala, lista e remove plugins; `codex plugin marketplace` gerencia as fontes |
| `codex mcp` | Gerencia servidores MCP (listar, adicionar, remover, autenticar) |
| `codex mcp-server` | Descontinuado; use o app server |
| `codex doctor` | Diagnostica instalaêÂ§êÂ£o, config, auth e saêÂºde de execuêÂ§êÂ£o |
| `codex features` | Inspeciona feature flags (listar / ligar / desligar) |
| `codex sandbox` | Roda comandos dentro de um sandbox fornecido pelo Codex |
| `codex update` | Auto-atualiza para a versêÂ£o mais recente |
| `codex completion` | Gera completions de shell (bash, zsh, fish, powershell) |
| `codex app-server` | Roda o app server (experimental) |
| `codex exec-server` | Roda o serviêÂ§o exec-server standalone (experimental) |
| `codex remote-control` | Gerencia o daemon do app server por controle remoto (experimental) |
| `codex debug` | Ferramentas de depuraêÂ§êÂ£o (subcomandos experimentais) |

</details>

<details>
<summary><strong>Flags êÂºteis da CLI</strong></summary>

```bash
# Escolha de modelo
codex --model gpt-5 "seu prompt"
codex -m gpt-5.6-terra "tarefa complexa"

# DiretêÂ³rio de trabalho
codex --cd /caminho/do/projeto        # Muda o diretêÂ³rio de trabalho
codex -C ../outro-projeto             # Forma curta

# VêÂ¡rios diretêÂ³rios
codex --add-dir ../backend --add-dir ../shared "analise tudo"

# AprovaêÂ§êÂµes
codex --ask-for-approval untrusted    # Pergunta em comandos nêÂ£o confiêÂ¡veis
codex -a on-request                   # O modelo decide quando perguntar (interativo)
codex exec -a never "tarefa"          # Nunca pergunta (execuêÂ§êÂµes nêÂ£o interativas)

# Sandbox
codex --sandbox read-only             # Sandbox somente leitura (padrêÂ£o)
codex --sandbox workspace-write       # Permite escrita no workspace
codex --sandbox danger-full-access    # Desliga o sandbox (perigoso!)

# Entrada de imagem
codex -i screenshot.png "explique este erro"
codex --image img1.png,img2.jpg "resuma estes diagramas"

# Busca na web ao vivo
codex --search "qual êÂ© a versêÂ£o mais recente de X"

# AutomaêÂ§êÂ£o de aprovaêÂ§êÂµes
codex --approve-for-me "refatore isto"                     # AprovaêÂ§êÂµes por revisêÂ£o automêÂ¡tica
codex --dangerously-bypass-approvals-and-sandbox "tarefa"  # Sem aprovaêÂ§êÂ£o e sem sandbox (apelido: --yolo)
codex --yolo "tarefa"                                      # Apelido curto do anterior

# Config estrita
codex --strict-config                                      # Erra em campos desconhecidos do config.toml

# Provedores open-source locais
codex --oss                                                # Usa provedor open-source local
codex --oss --local-provider ollama                        # Escolhe o provedor (lmstudio | ollama)

# Perfis de configuraêÂ§êÂ£o
codex -p work "seu prompt"                                 # SobrepêÂµe ~/.codex/work.config.toml

# App server remoto
codex --remote ws://host:porta                             # Conecta a TUI a um app server remoto
codex --remote wss://host:porta --remote-auth-token-env TOKEN_ENV  # Bearer token vindo de variêÂ¡vel de ambiente

# Completions de shell
codex completion bash                 # Gera completions do bash
codex completion zsh                  # Gera completions do zsh
codex completion fish                 # Gera completions do fish
```

</details>

## NêÂ­vel 3: Uso intermediêÂ¡rio

ConfiguraêÂ§êÂ£o e personalizaêÂ§êÂ£o.

<details>
<summary><strong>ConfiguraêÂ§êÂ£o</strong></summary>

```bash
# Local do arquivo de config: ~/.codex/config.toml
# Sobrescritas por projeto: .codex/config.toml (carregado sêÂ³ em projetos confiêÂ¡veis;
# chaves de provider/auth/notificaêÂ§êÂ£o/telemetria sêÂ£o ignoradas nos arquivos por projeto)

# Edite a config êÂ  mêÂ£o ou use flags da CLI
codex --model gpt-5.6-terra "seu prompt"
codex --config model="gpt-5.6-terra"

# ConfiguraêÂ§êÂµes comuns no config.toml:
# - escolha de modelo
# - approval_policy
# - sandbox_mode
# - mcp_servers
# - profiles
```

</details>

<details>
<summary><strong>Escolha de modelo</strong></summary>

```bash
# Defina o modelo no config.toml
model = "gpt-6-astra"               # Novo carro-chefe: trabalho ponta a ponta mais difêÂ­cil em cêÂ³digo, apps e pesquisa (em liberaêÂ§êÂ£o gradual)
model = "gpt-5.6-sol"              # Carro-chefe: cêÂ³digo complexo, uso de computador, pesquisa (recomendado, setembro de 2026)
model = "gpt-5.6-terra"            # Equilibrado: cêÂ³digo e trabalho de conhecimento do dia a dia
model = "gpt-5.6-luna"             # RêÂ¡pido: tarefas leves, menor custo

# Para modelos de raciocêÂ­nio (gpt-6-astra, gpt-5.6-sol, gpt-5.6-terra):
model_reasoning_effort = "medium"  # minimal, low, medium, high, xhigh
model_reasoning_summary = "auto"   # auto, concise, detailed, none

# Para a famêÂ­lia GPT-5:
model_verbosity = "medium"         # low, medium, high

# Modelos disponêÂ­veis (em setembro de 2026):
# - gpt-6-astra - novo carro-chefe para trabalho complexo em cêÂ³digo, apps e pesquisa (em liberaêÂ§êÂ£o)
# - gpt-5.6-sol (recomendado) - carro-chefe para cêÂ³digo complexo, uso de computador, pesquisa e seguranêÂ§a
# - gpt-5.6-terra - equilibra capacidade e custo no cêÂ³digo e no trabalho do dia a dia
# - gpt-5.6-luna - opêÂ§êÂ£o mais rêÂ¡pida e barata para tarefas leves
# - gpt-5.3-codex-spark - preview de pesquisa, sêÂ³ texto, para iteraêÂ§êÂ£o quase instantêÂ¢nea (ChatGPT Pro)
# - gpt-5.5 - carro-chefe da geraêÂ§êÂ£o anterior
# - gpt-5.4 / gpt-5.4-mini - aposentados do Codex com login ChatGPT em 31/08/2026
# - gpt-5.2 / gpt-5.3-codex - descontinuados no Codex com login ChatGPT
# - Outros modelos da OpenAI via provedores customizados
```

### Novidades de modelo (setembro de 2026)

**GPT-6 Astra** êÂ© o novo carro-chefe, chegando aos poucos a todos os clientes:
- Feito para o trabalho ponta a ponta mais difêÂ­cil em cêÂ³digo, apps e pesquisa
- Combina raciocêÂ­nio avanêÂ§ado, uso de computador e melhor julgamento
- Use quando a tarefa exigir raciocêÂ­nio sustentado por vêÂ¡rias etapas e ferramentas

**GPT-5.6 Sol** continua sendo o carro-chefe da linha 5.6:
- Feito para cêÂ³digo complexo, uso de computador, pesquisa e trabalho de seguranêÂ§a
- Segue instruêÂ§êÂµes melhor e tem mais precisêÂ£o têÂ©cnica

**GPT-5.6 Terra** equilibra capacidade e custo:
- Otimizado para cêÂ³digo e trabalho de conhecimento do dia a dia
- RaciocêÂ­nio forte com uso eficiente de tokens

**GPT-5.6 Luna** êÂ© o mais rêÂ¡pido e barato:
- Ideal para tarefas leves e iteraêÂ§êÂµes rêÂ¡pidas
- MantêÂ©m a qualidade minimizando a latêÂªncia

**Aposentadorias:** gpt-5.4 e gpt-5.4-mini saêÂ­ram do Codex com login ChatGPT em 31 de agosto de 2026 (troque por gpt-5.6-terra e gpt-5.6-luna); gpt-5.2 e gpt-5.3-codex estêÂ£o descontinuados. A API da OpenAI e o login por chave de API nêÂ£o sêÂ£o afetados.

Veja a [pêÂ¡gina oficial de modelos](https://developers.openai.com/codex/models) para detalhes.

</details>

<details>
<summary><strong>Prompts customizados</strong></summary>

```bash
# Crie prompts customizados em ~/.codex/prompts/

# Exemplo: crie ~/.codex/prompts/review.md
# Depois use assim:
"Use o prompt review neste cêÂ³digo"
```

</details>

<details>
<summary><strong>MemêÂ³ria com AGENTS.md</strong></summary>

```bash
# Crie um AGENTS.md na raiz do projeto
# O Codex passa a lembrar o contexto especêÂ­fico do projeto

# Exemplo de conteêÂºdo do AGENTS.md:
"""
Este projeto usa:
- Node.js com Express
- Banco PostgreSQL
- Jest para testes

PadrêÂµes de cêÂ³digo:
- Usar TypeScript
- Seguir as regras do ESLint
- Escrever testes para toda funcionalidade nova
"""
```

</details>

## NêÂ­vel 4: Recursos avanêÂ§ados

Recursos poderosos para workflows avanêÂ§ados.

<details>
<summary><strong>Model Context Protocol (MCP)</strong></summary>

```bash
# Configure servidores MCP em ~/.codex/config.toml

# Exemplo de servidor STDIO
[mcp_servers.filesystem]
command = "npx"
args = ["-y", "@modelcontextprotocol/server-filesystem", "/caminho/permitido"]
env = { API_KEY = "valor" }

# Exemplo de servidor HTTP streamable
[mcp_servers.figma]
url = "https://mcp.figma.com/mcp"
bearer_token_env_var = "FIGMA_TOKEN"

# Comandos MCP da CLI
codex mcp list                        # Lista os servidores configurados
codex mcp add <nome> -- <comando>     # Adiciona um servidor stdio
codex mcp add <nome> --url <URL>      # Adiciona um servidor HTTP streamable
codex mcp get <nome>                  # Mostra os detalhes do servidor
codex mcp remove <nome>               # Remove um servidor
codex mcp login <nome>                # Login OAuth (HTTP streamable)
codex mcp logout <nome>               # Logout OAuth

# Faz a inicializaêÂ§êÂ£o falhar se um servidor nêÂ£o subir:
[mcp_servers.figma]
url = "https://mcp.figma.com/mcp"
required = true

# Plugins sêÂ£o a superfêÂ­cie estêÂ¡vel para integraêÂ§êÂµes empacotadas
codex plugin list                     # Lista plugins dos marketplaces configurados
codex plugin add <plugin>             # Instala um plugin (ou PLUGIN@MARKETPLACE)
codex plugin marketplace list         # Gerencia os marketplaces de plugins

# Nota: codex mcp-server estêÂ¡ descontinuado; use o app server

# Servidores MCP populares:
# - Context7 (documentaêÂ§êÂ£o para desenvolvedores)
# - Figma (acesso a design)
# - Playwright (controle de navegador)
# - GitHub (acesso êÂ  API do GitHub)
# - Sentry (acesso a logs)
```

Veja a [documentaêÂ§êÂ£o de MCP](https://developers.openai.com/codex/configuration) para detalhes.

</details>

<details>
<summary><strong>Sandbox e permissêÂµes</strong></summary>

```bash
# Configure o modo de sandbox no config.toml
sandbox_mode = "read-only"              # PadrêÂ£o: somente leitura
sandbox_mode = "workspace-write"        # Permite escrita no workspace
sandbox_mode = "danger-full-access"     # Desliga o sandbox (perigoso!)

# Configure a polêÂ­tica de aprovaêÂ§êÂ£o (vêÂ¡lidos: untrusted | on-request | never; "on-failure" foi descontinuado)
approval_policy = "untrusted"           # Pergunta em comandos nêÂ£o confiêÂ¡veis
approval_policy = "on-request"          # O modelo decide quando perguntar (interativo)
approval_policy = "never"               # Nunca pergunta (execuêÂ§êÂµes nêÂ£o interativas)

# OpêÂ§êÂµes do workspace-write
[sandbox_workspace_write]
writable_roots = ["/caminho/extra"]
network_access = false
exclude_tmpdir_env_var = false
exclude_slash_tmp = false
```

Veja [Sandbox e aprovaêÂ§êÂµes](https://developers.openai.com/codex/sandboxing) para detalhes.

</details>

<details>
<summary><strong>Modo nêÂ£o interativo</strong></summary>

```bash
# Executa e sai, com codex exec
codex exec "resuma todos os comentêÂ¡rios TODO deste projeto"

# AprovaêÂ§êÂµes por revisêÂ£o automêÂ¡tica (sandbox workspace-write)
codex exec --approve-for-me "refatore este cêÂ³digo"

# Totalmente desassistido (perigoso ê¢â¬â pula todas as aprovaêÂ§êÂµes e o sandbox)
codex exec --dangerously-bypass-approvals-and-sandbox "refatore este cêÂ³digo"

# Acesso total (perigoso!)
codex exec --sandbox danger-full-access "sua tarefa"

# SaêÂ­da em JSON para automaêÂ§êÂ£o
codex exec --json "analise este projeto"

# SaêÂ­da estruturada com JSON schema
codex exec --output-schema schema.json "extraia os detalhes do projeto"

# Salvar a saêÂ­da em arquivo (grava sêÂ³ a êÂºltima mensagem do agente, nêÂ£o a execuêÂ§êÂ£o inteira)
codex exec -o output.txt "gere a documentaêÂ§êÂ£o"

# Combine com --json em CI: eventos JSONL no stdout + resumo final no arquivo
codex exec --json -o output.txt "gere a documentaêÂ§êÂ£o"
```

Veja [Modo nêÂ£o interativo (exec)](https://developers.openai.com/codex/non-interactive-mode) para detalhes.

</details>

<details>
<summary><strong>RevisêÂ£o de cêÂ³digo nêÂ£o interativa</strong></summary>

Roda uma revisêÂ£o dedicada sem abrir a TUI. Relata achados priorizados sem modificar a êÂ¡rvore de trabalho.

```bash
codex review --uncommitted                    # Revisa mudanêÂ§as staged, unstaged e nêÂ£o rastreadas
codex review --base main                      # Revisa as mudanêÂ§as contra uma branch base
codex review --commit <SHA>                   # Revisa as mudanêÂ§as introduzidas por um commit
codex review --uncommitted --title "wip: auth"  # TêÂ­tulo opcional no resumo da revisêÂ£o
codex review "foque em problemas de seguranêÂ§a"  # InstruêÂ§êÂµes customizadas de revisêÂ£o
```

Veja [Code Review](https://developers.openai.com/codex/code-review) para detalhes.

</details>

<details>
<summary><strong>Pipes e scripts</strong></summary>

```bash
# Mande conteêÂºdo para o Codex por pipe
cat logs.txt | codex exec "encontre o erro"

# Use em scripts
git diff | codex exec "crie uma mensagem de commit no padrêÂ£o conventional"

# Combine comandos
codex exec "explique este arquivo" < app.js > explicacao.md
```

</details>

<details>
<summary><strong>Skills</strong></summary>

<a id="skills"></a>

- **O que sêÂ£o:** capacidades nativas, reutilizêÂ¡veis e em disco, que o Codex descobre sozinho. Cada skill êÂ© um pacote com `name`, `description` e um corpo opcional mantido em disco. JêÂ¡ estêÂ£o disponêÂ­veis para todos ê¢â¬â nêÂ£o precisa de feature flag.
- **Onde ficam:** `~/.codex/skills/**/SKILL.md` (recursivo). SêÂ³ valem arquivos chamados exatamente `SKILL.md`; entradas ocultas e symlinks sêÂ£o ignoradas.
- **Formato do arquivo (frontmatter YAML + corpo):**
  ```markdown
  ---
  name: nome-da-sua-skill        # obrigatêÂ³rio, ê¢â°Â¤ 100 caracteres, uma linha
  description: quando/por que usar  # obrigatêÂ³rio, ê¢â°Â¤ 500 caracteres, uma linha
  ---

  # Corpo opcional (fica em disco)
  Coloque aqui referêÂªncias, fluxos de trabalho ou exemplos.
  ```
- **Como usar:** mencione com `$<nome-da-skill>` no chat, ou navegue/insira pelo `/skills` na TUI. O Codex injeta apenas `name`, `description` e o caminho absoluto do arquivo.
- **ValidaêÂ§êÂ£o:** frontmatter invêÂ¡lido gera um aviso dispensêÂ¡vel na inicializaêÂ§êÂ£o e entradas de log; skills invêÂ¡lidas sêÂ£o ignoradas atêÂ© serem corrigidas.
- **Skills de exemplo neste repositêÂ³rio:** copie ou crie um symlink de qualquer uma delas em `~/.codex/skills/<nome>/SKILL.md` e reinicie o Codex:
  - `skills/pdf-processing/SKILL.md`
  - `skills/log-review/SKILL.md`
  - `skills/form-filling/SKILL.md`
  - `skills/project-management/SKILL.md`

</details>

## Novidades 2025ê¢â¬â2026

AdiêÂ§êÂµes recentes ao Codex que vale conhecer:

<details>
<summary><strong>Objetivos de tarefa (/goal)</strong></summary>

O comando `/goal` define um objetivo persistente para uma tarefa longa. Ele repete planejar ê¢â â agir ê¢â â testar ê¢â â revisar atêÂ© bater a sua condiêÂ§êÂ£o de parada.

**Uso:**

```bash
/goal Termine a migraêÂ§êÂ£o mantendo os testes verdes   # Define o objetivo
/goal                                                 # Mostra o objetivo atual
/goal pause                                           # Pausa a execuêÂ§êÂ£o
/goal resume                                          # Retoma uma execuêÂ§êÂ£o pausada
/goal clear                                           # Limpa o objetivo atual
```

**Quando usar:** trabalho de vêÂ¡rias horas, validêÂ¡vel, com uma definiêÂ§êÂ£o clara de "pronto".
**Quando nêÂ£o usar:** quando vocêÂª ainda estêÂ¡ explorando ou tomando decisêÂµes de julgamento.

> **Nota:** defina uma condiêÂ§êÂ£o de parada mensurêÂ¡vel. Use `/goal pause` ou `/goal clear` se ele comeêÂ§ar a derivar. Rode em uma branch descartêÂ¡vel.

Veja a [documentaêÂ§êÂ£o de follow-a-goal](https://developers.openai.com/codex/developer-commands#set-or-view-a-task-goal-with-goal).

</details>

<details>
<summary><strong>Skill babysit-pr</strong></summary>

A skill `babysit-pr` automatiza a manutenêÂ§êÂ£o de PRs:
- Corrige falhas de CI sozinha
- Trata comentêÂ¡rios de revisêÂ£o
- Fica de olho em conflitos de merge
- MantêÂ©m seus PRs andando no pipeline

```bash
# Use com a integraêÂ§êÂ£o MCP do GitHub
codex "babysit this PR with $github"
```

</details>

<details>
<summary><strong>REPL de JavaScript (js_repl)</strong></summary>

REPL de JavaScript persistente para execuêÂ§êÂ£o incremental de cêÂ³digo:
- Testa trechos de cêÂ³digo em tempo real
- Itera a lêÂ³gica sem re-executar tudo
- Depura expressêÂµes complexas

```bash
# Ative no config.toml
[mcp_servers.js_repl]
command = "node"
args = ["-e", "process.stdin.on('data', d => eval(d.toString()))"]
```

</details>

<details>
<summary><strong>App server em processo</strong></summary>

Nova arquitetura para o modo `exec` nêÂ£o interativo:
- InicializaêÂ§êÂ£o mais rêÂ¡pida
- Melhor para integraêÂ§êÂ£o com CI/CD
- Menos sobrecarga em scripts de automaêÂ§êÂ£o

</details>

## GestêÂ£o de projetos com o Codex

O Codex nêÂ£o serve sêÂ³ para cêÂ³digo ê¢â¬â êÂ© um bom assistente de gestêÂ£o de projetos. Como usêÂ¡-lo para tocar projetos, sprints e tarefas:

<details>
<summary><strong>Planejamento e quebra de escopo</strong></summary>

```bash
# Quebrar um pedido grande de feature
codex "Quebre este pedido de feature em tarefas acionêÂ¡veis:
- Sistema de autenticaêÂ§êÂ£o de usuêÂ¡rio
- Precisa suportar OAuth e e-mail
- Incluir fluxo de recuperaêÂ§êÂ£o de senha
- Adicionar opêÂ§êÂ£o de 2FA"

# Gerar backlog de sprint
codex exec "Analise este projeto e crie um backlog de sprint:
- Priorize por complexidade
- Estime o esforêÂ§o em horas
- Identifique dependêÂªncias"

# Criar histêÂ³rias de usuêÂ¡rio
codex "Converta estes requisitos em histêÂ³rias de usuêÂ¡rio com critêÂ©rios de aceite"
```

</details>

<details>
<summary><strong>IntegraêÂ§êÂ£o com o GitHub</strong></summary>

```bash
# Gerar descriêÂ§êÂµes de PR automaticamente
git diff | codex exec "Crie uma descriêÂ§êÂ£o detalhada de PR com:
- Resumo das mudanêÂ§as
- Testes realizados
- Breaking changes (se houver)"

# Criar issues a partir de comentêÂ¡rios TODO
codex exec "Varra o projeto atrêÂ¡s de TODO/FIXME e crie issues no GitHub"

# Gerar notas de release
codex exec "Crie notas de release a partir dos commits recentes"
```

</details>

<details>
<summary><strong>Acompanhamento e status</strong></summary>

```bash
# Gerar relatêÂ³rio de status
codex "Revise os commits recentes e gere um relatêÂ³rio de status para os stakeholders"

# Acompanhar progresso
codex "Que porcentagem das tarefas do sprint estêÂ¡ concluêÂ­da, com base nos PRs mergeados?"

# Identificar riscos
codex "Analise este projeto e identifique possêÂ­veis bloqueios ou riscos"
```

</details>

<details>
<summary><strong>PadrêÂµes de colaboraêÂ§êÂ£o em time</strong></summary>

```bash
# AutomaêÂ§êÂ£o de revisêÂ£o de cêÂ³digo
codex "Revise este PR quanto a:
- Vulnerabilidades de seguranêÂ§a
- Problemas de performance
- PadrêÂµes de qualidade de cêÂ³digo
- Lacunas de cobertura de testes"

# Sincronizar documentaêÂ§êÂ£o
codex "Atualize o README com base nas features adicionadas recentemente"

# Ajuda no onboarding
codex "Crie um guia de onboarding de desenvolvedor para este projeto"
```

</details>

<details>
<summary><strong>Criando skills de gestêÂ£o de projeto</strong></summary>

VocêÂª pode criar skills sob medida para o fluxo do seu time:

```markdown
# ~/.codex/skills/team-sprint/SKILL.md
---
name: team-sprint
description: Gerencia o planejamento e o acompanhamento de sprint do nosso time
---

# Fluxo do sprint
1. Use `/standup` para gerar resumos de daily
2. Use `/retro` para coletar feedback de retrospectiva
3. Use `/velocity` para calcular a velocidade do time

# Templates
- Template de planejamento de sprint em docs/sprint-template.md
- Formato de retrospectiva: ComeêÂ§ar/Parar/Continuar
```

</details>

## NêÂ­vel 5: Workflows de especialista

PadrêÂµes avanêÂ§ados e automaêÂ§êÂ£o.

<details>
<summary><strong>IntegraêÂ§êÂ£o com GitHub Actions</strong></summary>

```yaml
# Use a codex-action no CI/CD
name: Code Review
on: [pull_request]
jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - uses: openai/codex-action@v1
        with:
          task: "Review this PR for security issues"
```

Veja a [GitHub Action](https://github.com/openai/codex-action) para detalhes.

</details>

<details>
<summary><strong>RevisêÂ£o de cêÂ³digo automatizada</strong></summary>

```bash
# Revisar o PR inteiro
codex "Revise este PR quanto a seguranêÂ§a, performance e manutenibilidade"

# Gerar mensagens de commit no padrêÂ£o conventional
git diff HEAD~1 | codex exec "Crie uma mensagem de commit no padrêÂ£o conventional"

# Corrigir problemas comuns automaticamente
codex "Corrija todos os erros de ESLint deste projeto"
```

</details>

<details>
<summary><strong>Apoio ao pipeline de CI/CD</strong></summary>

```bash
# Gerar config de CI
codex "Crie um workflow do GitHub Actions para:
- Projeto TypeScript
- Rodar testes no PR
- Fazer deploy na Vercel na main"

# Depurar falhas de CI
cat .github/workflows/build.log | codex exec "Encontre a causa raiz"
```

</details>

<details>
<summary><strong>MigraêÂ§êÂ£o de cêÂ³digo legado</strong></summary>

```bash
# Converter entre linguagens
codex "Converta este utilitêÂ¡rio Python para TypeScript"

# Atualizar APIs descontinuadas
codex "Converta todos os componentes de classe React em componentes funcionais com hooks"

# Adicionar seguranêÂ§a de tipos
codex "Adicione tipos TypeScript a este projeto JavaScript"
```

</details>

<details>
<summary><strong>OtimizaêÂ§êÂ£o de performance</strong></summary>

```bash
# Analisar gargalos
codex "FaêÂ§a o profiling deste cêÂ³digo e identifique gargalos de performance"

# Otimizar consultas ao banco
codex "Refatore estas consultas N+1 para usar carregamento em lote"

# Otimizar o bundle
codex "Sugira otimizaêÂ§êÂµes de webpack para reduzir o tamanho do bundle"
```

</details>

<details>
<summary><strong>Auditoria de seguranêÂ§a</strong></summary>

```bash
# Encontrar vulnerabilidades
codex "Audite este cêÂ³digo em busca de vulnerabilidades de seguranêÂ§a"

# Checar dependêÂªncias
codex "Revise o package.json procurando dependêÂªncias desatualizadas ou vulnerêÂ¡veis"

# Checar conformidade
codex "Verifique se este cêÂ³digo segue as diretrizes de seguranêÂ§a da OWASP"
```

</details>

<details>
<summary><strong>DiagnêÂ³stico e depuraêÂ§êÂ£o</strong></summary>

```bash
# Analisar logs de erro
cat error.log | codex exec "encontre a causa raiz"

# Depurar uma funêÂ§êÂ£o especêÂ­fica
codex "Descubra por que a funêÂ§êÂ£o de login estêÂ¡ falhando"

# Reproduzir e corrigir
codex "Crie um caso de teste que reproduza este bug e depois corrija"
```

</details>

<details>
<summary><strong>DocumentaêÂ§êÂ£o</strong></summary>

```bash
# Gerar README
codex exec "Crie um README completo para este projeto"

# DocumentaêÂ§êÂ£o de API
codex exec "Gere a documentaêÂ§êÂ£o de API a partir dos comentêÂ¡rios JSDoc"

# ComentêÂ¡rios de cêÂ³digo
codex "Adicione comentêÂ¡rios detalhados a esta funêÂ§êÂ£o complexa"
```

</details>

<details>
<summary><strong>Testes</strong></summary>

```bash
# Gerar testes
codex "Crie testes unitêÂ¡rios para todas as funêÂ§êÂµes de utils.js"

# Cobertura de testes
codex "Analise a cobertura de testes e sugira os testes que faltam"

# Testes E2E
codex "Crie testes E2E com Playwright para o fluxo do usuêÂ¡rio"
```

</details>

<details>
<summary><strong>RefatoraêÂ§êÂ£o</strong></summary>

```bash
codex "Refatore este cêÂ³digo para:
1. Melhorar a legibilidade
2. Adicionar tratamento de erro
3. Seguir as boas prêÂ¡ticas de TypeScript
4. Adicionar definiêÂ§êÂµes de tipo"
```

</details>

## Recursos adicionais

**DocumentaêÂ§êÂ£o oficial do OpenAI Codex:**
- [RepositêÂ³rio oficial](https://github.com/openai/codex) ê¢â¬â repositêÂ³rio principal e central de documentaêÂ§êÂ£o
- [Guia de inêÂ­cio](https://developers.openai.com/codex/quickstart) ê¢â¬â guia completo para comeêÂ§ar
- [ReferêÂªncia de configuraêÂ§êÂ£o](https://developers.openai.com/codex/configuration) ê¢â¬â referêÂªncia completa do config.toml
- [Comandos de desenvolvedor](https://developers.openai.com/codex/developer-commands) ê¢â¬â comandos, flags e slash commands
- [Modo nêÂ£o interativo (exec)](https://developers.openai.com/codex/non-interactive-mode) ê¢â¬â automaêÂ§êÂ£o com codex exec
- [AutenticaêÂ§êÂ£o](https://developers.openai.com/codex/auth) ê¢â¬â mêÂ©todos de autenticaêÂ§êÂ£o
- [Sandbox e aprovaêÂ§êÂµes](https://developers.openai.com/codex/sandboxing) ê¢â¬â seguranêÂ§a e sandbox
- [DocumentaêÂ§êÂ£o do AGENTS.md](https://developers.openai.com/codex/agent-configuration/agents-md) ê¢â¬â instruêÂ§êÂµes por projeto
- [IntegraêÂ§êÂ£o MCP](https://developers.openai.com/codex/configuration) ê¢â¬â configuraêÂ§êÂ£o e uso de MCP
- [Prompts customizados](https://developers.openai.com/codex/prompting) ê¢â¬â como criar prompts prêÂ³prios
- [FAQ](https://developers.openai.com/codex/reference/troubleshooting) ê¢â¬â perguntas frequentes
- [Skills](https://developers.openai.com/codex/skills-and-plugins) ê¢â¬â guia oficial

**ExtensêÂµes e integraêÂ§êÂµes:**
- [GitHub Action](https://github.com/openai/codex-action) ê¢â¬â integraêÂ§êÂ£o com CI/CD
- [SDK TypeScript](https://developers.openai.com/codex/codex-sdk) ê¢â¬â uso programêÂ¡tico
- [ExtensêÂ£o do VS Code](https://developers.openai.com/codex/ide) ê¢â¬â integraêÂ§êÂ£o com a IDE

**Model Context Protocol:**
- [EspecificaêÂ§êÂ£o do MCP](https://modelcontextprotocol.io/) ê¢â¬â documentaêÂ§êÂ£o oficial do protocolo
- [Exemplos de servidores MCP](https://github.com/modelcontextprotocol/servers) ê¢â¬â servidores da comunidade

> **Dica:** confira sempre a [documentaêÂ§êÂ£o oficial do Codex](https://github.com/openai/codex) para os recursos e atualizaêÂ§êÂµes mais recentes. Esta folha de consulta êÂ© uma referêÂªncia rêÂ¡pida; a doc oficial êÂ© a fonte mais completa e atual.

## Contribuindo

Achou um problema ou tem uma sugestêÂ£o? ContribuiêÂ§êÂµes sêÂ£o bem-vindas!

- Reporte bugs ou problemas
- Sugira novos exemplos
- Melhore a documentaêÂ§êÂ£o
- Compartilhe seus workflows

## LicenêÂ§a

LicenêÂ§a MIT ê¢â¬â livre para usar e modificar.
