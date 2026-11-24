<div align="center">

# Codex Cheat Sheet

<a href="https://openai.com/codex/"><img width="763" height="341" alt="Codex cheat sheet" src="assets/image.png" /></a>

> **Seu guia completo para dominar o OpenAI Codex â€” do zero ao produtivo em minutos.**

Uma referÃªncia prÃ¡tica para usar o OpenAI Codex CLI com eficiÃªncia. O foco sÃ£o padrÃµes que ajudam vocÃª a pensar criticamente sobre o que delegar e o que fazer vocÃª mesmo.

**Baseado na documentaÃ§Ã£o oficial do OpenAI Codex** â€” todos os comandos e exemplos vÃªm da [documentaÃ§Ã£o oficial do Codex](https://developers.openai.com/codex). Para informaÃ§Ã£o sempre atualizada, consulte a doc oficial.

ðŸ‡ºðŸ‡¸ [English version](README.md)

</div>

## ðŸ“– Guia de uso

Guia completo (landing + passo a passo): **https://linnoff88-dev.github.io/

## InÃ­cio rÃ¡pido

```bash
# Instalar com o instalador oficial (recomendado)
curl -fsSL https://chatgpt.com/codex/install.sh | sh

# Ou com npm
npm install -g @openai/codex

# Ou com Homebrew
brew install --cask codex

# Ou com pnpm (gerenciador oficial do monorepo)
pnpm install -g @openai/codex

# Windows: script oficial de instalaÃ§Ã£o
powershell -ExecutionPolicy ByPass -c "irm https://chatgpt.com/codex/install.ps1 | iex"

# Auto-atualizaÃ§Ã£o (instalaÃ§Ãµes feitas pelo instalador)
codex update

# Abrir o Codex
codex

# Ver a versÃ£o
codex --version
```

## Ãndice

- **[NÃ­vel 1: Primeiros passos](#nÃ­vel-1-primeiros-passos)**
- **[NÃ­vel 2: Comandos bÃ¡sicos](#nÃ­vel-2-comandos-bÃ¡sicos)**
- **[NÃ­vel 3: Uso intermediÃ¡rio](#nÃ­vel-3-uso-intermediÃ¡rio)**
- **[NÃ­vel 4: Recursos avanÃ§ados](#nÃ­vel-4-recursos-avanÃ§ados)**
- **[Skills](#skills)** â€” capacidades nativas e reutilizÃ¡veis
- **[NÃ­vel 5: Workflows de especialista](#nÃ­vel-5-workflows-de-especialista)**

## NÃ­vel 1: Primeiros passos

Comandos essenciais para comeÃ§ar com o Codex.

<details>
<summary><strong>InstalaÃ§Ã£o</strong></summary>

```bash
# Instalar globalmente com npm
npm install -g @openai/codex

# Instalar com Homebrew (macOS)
brew install --cask codex

# Instalar com pnpm (gerenciador oficial do monorepo)
pnpm install -g @openai/codex

# Instalador oficial standalone (macOS/Linux)
curl -fsSL https://chatgpt.com/codex/install.sh | sh

# Windows: script oficial de instalaÃ§Ã£o
powershell -ExecutionPolicy ByPass -c "irm https://chatgpt.com/codex/install.ps1 | iex"

# Atualizar com npm
npm install -g @openai/codex

# Atualizar com Homebrew
brew upgrade --cask codex

# Auto-atualizaÃ§Ã£o (quando a release instalada suportar)
codex update

# Baixar o binÃ¡rio das releases do GitHub
# Acesse: https://github.com/openai/codex/releases/latest
```

</details>

<details>
<summary><strong>Primeiros comandos</strong></summary>

```bash
# Iniciar o modo interativo
codex

# Rodar com um prompt especÃ­fico
codex "explain this project"

# ExecuÃ§Ã£o nÃ£o interativa
codex exec "explain utils.ts"
```

</details>

<details>
<summary><strong>AutenticaÃ§Ã£o</strong></summary>

```bash
# Entrar com a conta ChatGPT (recomendado)
codex
# Depois escolha "Sign in with ChatGPT"

# Usar chave de API (alternativa â€” cobranÃ§a por uso)
printenv OPENAI_API_KEY | codex login --with-api-key
# Ou a partir de um arquivo:
codex login --with-api-key < my_key.txt

# Usar um access token
printenv CODEX_ACCESS_TOKEN | codex login --with-access-token

# AutenticaÃ§Ã£o por dispositivo
codex login --device-auth

# Conferir o status do login (saÃ­da 0 = credenciais presentes)
codex login status
```

</details>

<details>
<summary><strong>NavegaÃ§Ã£o bÃ¡sica</strong></summary>

```bash
# Atalhos de teclado
Ctrl+C                    # Cancela a operaÃ§Ã£o atual (ou use /exit para fechar a sessÃ£o)
Tab                       # Enfileira o prÃ³ximo prompt, slash command ou comando de shell enquanto o Codex trabalha
â†‘/â†“                       # Recupera o histÃ³rico de rascunhos
Esc Esc                   # Edita a mensagem anterior (composer vazio; bifurca a conversa daquele ponto)
Ctrl+R                    # Busca no histÃ³rico de prompts
Ctrl+O                    # Copia a Ãºltima saÃ­da concluÃ­da
Enter                     # Injeta novas instruÃ§Ãµes no turno atual
!comando                  # Roda um comando local de shell sob a polÃ­tica de aprovaÃ§Ã£o/sandbox atual

# Entrada especial
@                         # Dispara a busca de arquivos (fuzzy find)
```

</details>

## NÃ­vel 2: Comandos bÃ¡sicos

Comandos centrais para o dia a dia.

<details>
<summary><strong>Slash commands â€” essenciais</strong></summary>

```bash
/model                    # Escolhe o modelo e o esforÃ§o de raciocÃ­nio
/permissions              # Configura o que o Codex pode fazer sem aprovaÃ§Ã£o
/fast                     # Liga/desliga o modo Fast nos modelos suportados
/personality              # Escolhe um estilo de comunicaÃ§Ã£o
/review                   # Revisa as mudanÃ§as atuais e aponta problemas
/new                      # ComeÃ§a um novo chat durante a conversa
/init                     # Cria um arquivo AGENTS.md com instruÃ§Ãµes
/compact                  # Resume a conversa para nÃ£o estourar o contexto
/diff                     # Mostra o git diff (inclusive arquivos nÃ£o rastreados)
/mention                  # Menciona um arquivo
/status                   # Mostra a config da sessÃ£o e o uso de tokens
/mcp                      # Lista as ferramentas MCP configuradas
/side                     # Abre uma conversa lateral efÃªmera (/btw)
/fork                     # Bifurca a conversa atual em uma nova thread
/ps                       # Mostra os terminais em segundo plano e suas saÃ­das
/stop                     # Para todos os terminais em segundo plano
/logout                   # Sai da conta do Codex
/quit                     # Fecha o Codex
/exit                     # Fecha o Codex
/feedback                 # Envia logs para os mantenedores
/goal                     # Define ou mostra um objetivo persistente da tarefa
/plan                     # Entra no modo de plano, para planejamento multi-etapas
/approve                  # Aprova uma nova tentativa apÃ³s negativa da revisÃ£o automÃ¡tica
/copy                     # Copia a Ãºltima saÃ­da concluÃ­da (ou Ctrl+O)
/clear                    # Limpa o terminal e comeÃ§a um novo chat
/rename                   # Renomeia o chat atual
/archive                  # Arquiva a sessÃ£o atual e fecha o Codex
/delete                   # Apaga a sessÃ£o atual em definitivo e fecha
/resume                   # Retoma um chat salvo da sua lista de sessÃµes
/app                      # Continua a sessÃ£o no app desktop do ChatGPT
/agent                    # Troca a thread de agente ativa (tambÃ©m /subagents)
/apps                     # Navega pelos apps (conectores) e insere no prompt
/plugins                  # Navega pelos plugins instalados e disponÃ­veis
/hooks                    # VÃª e gerencia os hooks de ciclo de vida
/memories                 # Configura o uso e a geraÃ§Ã£o de memÃ³ria
/import                   # Importa a configuraÃ§Ã£o do Claude Code ou do Cursor
/experimental             # Liga/desliga recursos experimentais
/usage                    # Mostra o uso de tokens da conta
/debug-config             # Imprime o diagnÃ³stico das camadas de config
/statusline               # Configura os itens do rodapÃ© da TUI
/title                    # Configura os itens do tÃ­tulo do terminal
/theme                    # Escolhe um tema de sintaxe
/pets                     # Escolhe ou esconde um bichinho de terminal (/pet)
/keymap                   # Remapeia os atalhos de teclado da TUI
/vim                      # Liga/desliga o modo Vim no composer
/ide                      # Inclui os arquivos abertos e o contexto da IDE
/raw                      # Liga/desliga o modo de scrollback bruto
/skills                   # Navega e usa as skills

# /debug nÃ£o Ã© mais documentado; use /debug-config para diagnÃ³stico de config
```

</details>

<details>
<summary><strong>OperaÃ§Ãµes com arquivos e diretÃ³rios</strong></summary>

```bash
# O Codex lÃª, escreve e edita arquivos
"Leia o conteÃºdo de src/app.js"
"Crie um arquivo novo chamado utils.js"
"Edite a funÃ§Ã£o em main.py para adicionar tratamento de erro"

# Ver a estrutura do projeto
"Explique a estrutura deste projeto"
"Que arquivos existem no diretÃ³rio src?"
```

</details>

<details>
<summary><strong>Trabalhando com cÃ³digo</strong></summary>

```bash
# AnÃ¡lise de cÃ³digo
"Explique o que este cÃ³digo faz"
"Revise esta funÃ§Ã£o procurando bugs"
"Sugira melhorias para este arquivo"

# GeraÃ§Ã£o de cÃ³digo
"Escreva uma funÃ§Ã£o para fazer parse de JSON"
"Crie testes unitÃ¡rios para este mÃ³dulo"
"Adicione tratamento de erro a este cÃ³digo"
```

</details>

<details>
<summary><strong>Gerenciamento de sessÃµes</strong></summary>

```bash
# Retomar sessÃµes
codex resume                          # Abre o seletor de sessÃµes
codex resume --last                   # Retoma a sessÃ£o mais recente
codex resume <SESSION_ID>             # Retoma uma sessÃ£o especÃ­fica pelo ID

# Retomada de sessÃ£o nÃ£o interativa
codex exec resume <SESSION_ID>        # Retoma uma sessÃ£o nÃ£o interativa
codex exec resume --last              # Retoma a Ãºltima sessÃ£o nÃ£o interativa
```

</details>

<details>
<summary><strong>ReferÃªncia de subcomandos (0.147.0)</strong></summary>

| Comando | Para que serve |
|---|---|
| `codex exec` | Roda de forma nÃ£o interativa (apelido: `e`) |
| `codex review` | RevisÃ£o de cÃ³digo nÃ£o interativa (veja a [seÃ§Ã£o abaixo](#nÃ­vel-4-recursos-avanÃ§ados)) |
| `codex login` / `codex logout` | Gerencia a autenticaÃ§Ã£o; `codex login status` confere as credenciais |
| `codex resume` | Retoma uma sessÃ£o salva (seletor; `--last` para a mais recente) |
| `codex fork` | Bifurca uma sessÃ£o em um novo chat |
| `codex archive` / `codex unarchive` | Arquiva / restaura sessÃµes salvas |
| `codex delete` | Apaga uma sessÃ£o em definitivo |
| `codex apply` | Aplica um diff de chat do Codex Cloud na Ã¡rvore local (apelido: `a`) |
| `codex cloud` | Navega ou executa tarefas do Codex Cloud (experimental) |
| `codex plugin` | Instala, lista e remove plugins; `codex plugin marketplace` gerencia as fontes |
| `codex mcp` | Gerencia servidores MCP (listar, adicionar, remover, autenticar) |
| `codex mcp-server` | Descontinuado; use o app server |
| `codex doctor` | Diagnostica instalaÃ§Ã£o, config, auth e saÃºde de execuÃ§Ã£o |
| `codex features` | Inspeciona feature flags (listar / ligar / desligar) |
| `codex sandbox` | Roda comandos dentro de um sandbox fornecido pelo Codex |
| `codex update` | Auto-atualiza para a versÃ£o mais recente |
| `codex completion` | Gera completions de shell (bash, zsh, fish, powershell) |
| `codex app-server` | Roda o app server (experimental) |
| `codex exec-server` | Roda o serviÃ§o exec-server standalone (experimental) |
| `codex remote-control` | Gerencia o daemon do app server por controle remoto (experimental) |
| `codex debug` | Ferramentas de depuraÃ§Ã£o (subcomandos experimentais) |

</details>

<details>
<summary><strong>Flags Ãºteis da CLI</strong></summary>

```bash
# Escolha de modelo
codex --model gpt-5 "seu prompt"
codex -m gpt-5.6-terra "tarefa complexa"

# DiretÃ³rio de trabalho
codex --cd /caminho/do/projeto        # Muda o diretÃ³rio de trabalho
codex -C ../outro-projeto             # Forma curta

# VÃ¡rios diretÃ³rios
codex --add-dir ../backend --add-dir ../shared "analise tudo"

# AprovaÃ§Ãµes
codex --ask-for-approval untrusted    # Pergunta em comandos nÃ£o confiÃ¡veis
codex -a on-request                   # O modelo decide quando perguntar (interativo)
codex exec -a never "tarefa"          # Nunca pergunta (execuÃ§Ãµes nÃ£o interativas)

# Sandbox
codex --sandbox read-only             # Sandbox somente leitura (padrÃ£o)
codex --sandbox workspace-write       # Permite escrita no workspace
codex --sandbox danger-full-access    # Desliga o sandbox (perigoso!)

# Entrada de imagem
codex -i screenshot.png "explique este erro"
codex --image img1.png,img2.jpg "resuma estes diagramas"

# Busca na web ao vivo
codex --search "qual Ã© a versÃ£o mais recente de X"

# AutomaÃ§Ã£o de aprovaÃ§Ãµes
codex --approve-for-me "refatore isto"                     # AprovaÃ§Ãµes por revisÃ£o automÃ¡tica
codex --dangerously-bypass-approvals-and-sandbox "tarefa"  # Sem aprovaÃ§Ã£o e sem sandbox (apelido: --yolo)
codex --yolo "tarefa"                                      # Apelido curto do anterior

# Config estrita
codex --strict-config                                      # Erra em campos desconhecidos do config.toml

# Provedores open-source locais
codex --oss                                                # Usa provedor open-source local
codex --oss --local-provider ollama                        # Escolhe o provedor (lmstudio | ollama)

# Perfis de configuraÃ§Ã£o
codex -p work "seu prompt"                                 # SobrepÃµe ~/.codex/work.config.toml

# App server remoto
codex --remote ws://host:porta                             # Conecta a TUI a um app server remoto
codex --remote wss://host:porta --remote-auth-token-env TOKEN_ENV  # Bearer token vindo de variÃ¡vel de ambiente

# Completions de shell
codex completion bash                 # Gera completions do bash
codex completion zsh                  # Gera completions do zsh
codex completion fish                 # Gera completions do fish
```

</details>

## NÃ­vel 3: Uso intermediÃ¡rio

ConfiguraÃ§Ã£o e personalizaÃ§Ã£o.

<details>
<summary><strong>ConfiguraÃ§Ã£o</strong></summary>

```bash
# Local do arquivo de config: ~/.codex/config.toml
# Sobrescritas por projeto: .codex/config.toml (carregado sÃ³ em projetos confiÃ¡veis;
# chaves de provider/auth/notificaÃ§Ã£o/telemetria sÃ£o ignoradas nos arquivos por projeto)

# Edite a config Ã  mÃ£o ou use flags da CLI
codex --model gpt-5.6-terra "seu prompt"
codex --config model="gpt-5.6-terra"

# ConfiguraÃ§Ãµes comuns no config.toml:
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
model = "gpt-6-astra"               # Novo carro-chefe: trabalho ponta a ponta mais difÃ­cil em cÃ³digo, apps e pesquisa (em liberaÃ§Ã£o gradual)
model = "gpt-5.6-sol"              # Carro-chefe: cÃ³digo complexo, uso de computador, pesquisa (recomendado, setembro de 2026)
model = "gpt-5.6-terra"            # Equilibrado: cÃ³digo e trabalho de conhecimento do dia a dia
model = "gpt-5.6-luna"             # RÃ¡pido: tarefas leves, menor custo

# Para modelos de raciocÃ­nio (gpt-6-astra, gpt-5.6-sol, gpt-5.6-terra):
model_reasoning_effort = "medium"  # minimal, low, medium, high, xhigh
model_reasoning_summary = "auto"   # auto, concise, detailed, none

# Para a famÃ­lia GPT-5:
model_verbosity = "medium"         # low, medium, high

# Modelos disponÃ­veis (em setembro de 2026):
# - gpt-6-astra - novo carro-chefe para trabalho complexo em cÃ³digo, apps e pesquisa (em liberaÃ§Ã£o)
# - gpt-5.6-sol (recomendado) - carro-chefe para cÃ³digo complexo, uso de computador, pesquisa e seguranÃ§a
# - gpt-5.6-terra - equilibra capacidade e custo no cÃ³digo e no trabalho do dia a dia
# - gpt-5.6-luna - opÃ§Ã£o mais rÃ¡pida e barata para tarefas leves
# - gpt-5.3-codex-spark - preview de pesquisa, sÃ³ texto, para iteraÃ§Ã£o quase instantÃ¢nea (ChatGPT Pro)
# - gpt-5.5 - carro-chefe da geraÃ§Ã£o anterior
# - gpt-5.4 / gpt-5.4-mini - aposentados do Codex com login ChatGPT em 31/08/2026
# - gpt-5.2 / gpt-5.3-codex - descontinuados no Codex com login ChatGPT
# - Outros modelos da OpenAI via provedores customizados
```

### Novidades de modelo (setembro de 2026)

**GPT-6 Astra** Ã© o novo carro-chefe, chegando aos poucos a todos os clientes:
- Feito para o trabalho ponta a ponta mais difÃ­cil em cÃ³digo, apps e pesquisa
- Combina raciocÃ­nio avanÃ§ado, uso de computador e melhor julgamento
- Use quando a tarefa exigir raciocÃ­nio sustentado por vÃ¡rias etapas e ferramentas

**GPT-5.6 Sol** continua sendo o carro-chefe da linha 5.6:
- Feito para cÃ³digo complexo, uso de computador, pesquisa e trabalho de seguranÃ§a
- Segue instruÃ§Ãµes melhor e tem mais precisÃ£o tÃ©cnica

**GPT-5.6 Terra** equilibra capacidade e custo:
- Otimizado para cÃ³digo e trabalho de conhecimento do dia a dia
- RaciocÃ­nio forte com uso eficiente de tokens

**GPT-5.6 Luna** Ã© o mais rÃ¡pido e barato:
- Ideal para tarefas leves e iteraÃ§Ãµes rÃ¡pidas
- MantÃ©m a qualidade minimizando a latÃªncia

**Aposentadorias:** gpt-5.4 e gpt-5.4-mini saÃ­ram do Codex com login ChatGPT em 31 de agosto de 2026 (troque por gpt-5.6-terra e gpt-5.6-luna); gpt-5.2 e gpt-5.3-codex estÃ£o descontinuados. A API da OpenAI e o login por chave de API nÃ£o sÃ£o afetados.

Veja a [pÃ¡gina oficial de modelos](https://developers.openai.com/codex/models) para detalhes.

</details>

<details>
<summary><strong>Prompts customizados</strong></summary>

```bash
# Crie prompts customizados em ~/.codex/prompts/

# Exemplo: crie ~/.codex/prompts/review.md
# Depois use assim:
"Use o prompt review neste cÃ³digo"
```

</details>

<details>
<summary><strong>MemÃ³ria com AGENTS.md</strong></summary>

```bash
# Crie um AGENTS.md na raiz do projeto
# O Codex passa a lembrar o contexto especÃ­fico do projeto

# Exemplo de conteÃºdo do AGENTS.md:
"""
Este projeto usa:
- Node.js com Express
- Banco PostgreSQL
- Jest para testes

PadrÃµes de cÃ³digo:
- Usar TypeScript
- Seguir as regras do ESLint
- Escrever testes para toda funcionalidade nova
"""
```

</details>

## NÃ­vel 4: Recursos avanÃ§ados

Recursos poderosos para workflows avanÃ§ados.

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

# Faz a inicializaÃ§Ã£o falhar se um servidor nÃ£o subir:
[mcp_servers.figma]
url = "https://mcp.figma.com/mcp"
required = true

# Plugins sÃ£o a superfÃ­cie estÃ¡vel para integraÃ§Ãµes empacotadas
codex plugin list                     # Lista plugins dos marketplaces configurados
codex plugin add <plugin>             # Instala um plugin (ou PLUGIN@MARKETPLACE)
codex plugin marketplace list         # Gerencia os marketplaces de plugins

# Nota: codex mcp-server estÃ¡ descontinuado; use o app server

# Servidores MCP populares:
# - Context7 (documentaÃ§Ã£o para desenvolvedores)
# - Figma (acesso a design)
# - Playwright (controle de navegador)
# - GitHub (acesso Ã  API do GitHub)
# - Sentry (acesso a logs)
```

Veja a [documentaÃ§Ã£o de MCP](https://developers.openai.com/codex/configuration) para detalhes.

</details>

<details>
<summary><strong>Sandbox e permissÃµes</strong></summary>

```bash
# Configure o modo de sandbox no config.toml
sandbox_mode = "read-only"              # PadrÃ£o: somente leitura
sandbox_mode = "workspace-write"        # Permite escrita no workspace
sandbox_mode = "danger-full-access"     # Desliga o sandbox (perigoso!)

# Configure a polÃ­tica de aprovaÃ§Ã£o (vÃ¡lidos: untrusted | on-request | never; "on-failure" foi descontinuado)
approval_policy = "untrusted"           # Pergunta em comandos nÃ£o confiÃ¡veis
approval_policy = "on-request"          # O modelo decide quando perguntar (interativo)
approval_policy = "never"               # Nunca pergunta (execuÃ§Ãµes nÃ£o interativas)

# OpÃ§Ãµes do workspace-write
[sandbox_workspace_write]
writable_roots = ["/caminho/extra"]
network_access = false
exclude_tmpdir_env_var = false
exclude_slash_tmp = false
```

Veja [Sandbox e aprovaÃ§Ãµes](https://developers.openai.com/codex/sandboxing) para detalhes.

</details>

<details>
<summary><strong>Modo nÃ£o interativo</strong></summary>

```bash
# Executa e sai, com codex exec
codex exec "resuma todos os comentÃ¡rios TODO deste projeto"

# AprovaÃ§Ãµes por revisÃ£o automÃ¡tica (sandbox workspace-write)
codex exec --approve-for-me "refatore este cÃ³digo"

# Totalmente desassistido (perigoso â€” pula todas as aprovaÃ§Ãµes e o sandbox)
codex exec --dangerously-bypass-approvals-and-sandbox "refatore este cÃ³digo"

# Acesso total (perigoso!)
codex exec --sandbox danger-full-access "sua tarefa"

# SaÃ­da em JSON para automaÃ§Ã£o
codex exec --json "analise este projeto"

# SaÃ­da estruturada com JSON schema
codex exec --output-schema schema.json "extraia os detalhes do projeto"

# Salvar a saÃ­da em arquivo (grava sÃ³ a Ãºltima mensagem do agente, nÃ£o a execuÃ§Ã£o inteira)
codex exec -o output.txt "gere a documentaÃ§Ã£o"

# Combine com --json em CI: eventos JSONL no stdout + resumo final no arquivo
codex exec --json -o output.txt "gere a documentaÃ§Ã£o"
```

Veja [Modo nÃ£o interativo (exec)](https://developers.openai.com/codex/non-interactive-mode) para detalhes.

</details>

<details>
<summary><strong>RevisÃ£o de cÃ³digo nÃ£o interativa</strong></summary>

Roda uma revisÃ£o dedicada sem abrir a TUI. Relata achados priorizados sem modificar a Ã¡rvore de trabalho.

```bash
codex review --uncommitted                    # Revisa mudanÃ§as staged, unstaged e nÃ£o rastreadas
codex review --base main                      # Revisa as mudanÃ§as contra uma branch base
codex review --commit <SHA>                   # Revisa as mudanÃ§as introduzidas por um commit
codex review --uncommitted --title "wip: auth"  # TÃ­tulo opcional no resumo da revisÃ£o
codex review "foque em problemas de seguranÃ§a"  # InstruÃ§Ãµes customizadas de revisÃ£o
```

Veja [Code Review](https://developers.openai.com/codex/code-review) para detalhes.

</details>

<details>
<summary><strong>Pipes e scripts</strong></summary>

```bash
# Mande conteÃºdo para o Codex por pipe
cat logs.txt | codex exec "encontre o erro"

# Use em scripts
git diff | codex exec "crie uma mensagem de commit no padrÃ£o conventional"

# Combine comandos
codex exec "explique este arquivo" < app.js > explicacao.md
```

</details>

<details>
<summary><strong>Skills</strong></summary>

<a id="skills"></a>

- **O que sÃ£o:** capacidades nativas, reutilizÃ¡veis e em disco, que o Codex descobre sozinho. Cada skill Ã© um pacote com `name`, `description` e um corpo opcional mantido em disco. JÃ¡ estÃ£o disponÃ­veis para todos â€” nÃ£o precisa de feature flag.
- **Onde ficam:** `~/.codex/skills/**/SKILL.md` (recursivo). SÃ³ valem arquivos chamados exatamente `SKILL.md`; entradas ocultas e symlinks sÃ£o ignoradas.
- **Formato do arquivo (frontmatter YAML + corpo):**
  ```markdown
  ---
  name: nome-da-sua-skill        # obrigatÃ³rio, â‰¤ 100 caracteres, uma linha
  description: quando/por que usar  # obrigatÃ³rio, â‰¤ 500 caracteres, uma linha
  ---

  # Corpo opcional (fica em disco)
  Coloque aqui referÃªncias, fluxos de trabalho ou exemplos.
  ```
- **Como usar:** mencione com `$<nome-da-skill>` no chat, ou navegue/insira pelo `/skills` na TUI. O Codex injeta apenas `name`, `description` e o caminho absoluto do arquivo.
- **ValidaÃ§Ã£o:** frontmatter invÃ¡lido gera um aviso dispensÃ¡vel na inicializaÃ§Ã£o e entradas de log; skills invÃ¡lidas sÃ£o ignoradas atÃ© serem corrigidas.
- **Skills de exemplo neste repositÃ³rio:** copie ou crie um symlink de qualquer uma delas em `~/.codex/skills/<nome>/SKILL.md` e reinicie o Codex:
  - `skills/pdf-processing/SKILL.md`
  - `skills/log-review/SKILL.md`
  - `skills/form-filling/SKILL.md`
  - `skills/project-management/SKILL.md`

</details>

## Novidades 2025â€“2026

AdiÃ§Ãµes recentes ao Codex que vale conhecer:

<details>
<summary><strong>Objetivos de tarefa (/goal)</strong></summary>

O comando `/goal` define um objetivo persistente para uma tarefa longa. Ele repete planejar â†’ agir â†’ testar â†’ revisar atÃ© bater a sua condiÃ§Ã£o de parada.

**Uso:**

```bash
/goal Termine a migraÃ§Ã£o mantendo os testes verdes   # Define o objetivo
/goal                                                 # Mostra o objetivo atual
/goal pause                                           # Pausa a execuÃ§Ã£o
/goal resume                                          # Retoma uma execuÃ§Ã£o pausada
/goal clear                                           # Limpa o objetivo atual
```

**Quando usar:** trabalho de vÃ¡rias horas, validÃ¡vel, com uma definiÃ§Ã£o clara de "pronto".
**Quando nÃ£o usar:** quando vocÃª ainda estÃ¡ explorando ou tomando decisÃµes de julgamento.

> **Nota:** defina uma condiÃ§Ã£o de parada mensurÃ¡vel. Use `/goal pause` ou `/goal clear` se ele comeÃ§ar a derivar. Rode em uma branch descartÃ¡vel.

Veja a [documentaÃ§Ã£o de follow-a-goal](https://developers.openai.com/codex/developer-commands#set-or-view-a-task-goal-with-goal).

</details>

<details>
<summary><strong>Skill babysit-pr</strong></summary>

A skill `babysit-pr` automatiza a manutenÃ§Ã£o de PRs:
- Corrige falhas de CI sozinha
- Trata comentÃ¡rios de revisÃ£o
- Fica de olho em conflitos de merge
- MantÃ©m seus PRs andando no pipeline

```bash
# Use com a integraÃ§Ã£o MCP do GitHub
codex "babysit this PR with $github"
```

</details>

<details>
<summary><strong>REPL de JavaScript (js_repl)</strong></summary>

REPL de JavaScript persistente para execuÃ§Ã£o incremental de cÃ³digo:
- Testa trechos de cÃ³digo em tempo real
- Itera a lÃ³gica sem re-executar tudo
- Depura expressÃµes complexas

```bash
# Ative no config.toml
[mcp_servers.js_repl]
command = "node"
args = ["-e", "process.stdin.on('data', d => eval(d.toString()))"]
```

</details>

<details>
<summary><strong>App server em processo</strong></summary>

Nova arquitetura para o modo `exec` nÃ£o interativo:
- InicializaÃ§Ã£o mais rÃ¡pida
- Melhor para integraÃ§Ã£o com CI/CD
- Menos sobrecarga em scripts de automaÃ§Ã£o

</details>

## GestÃ£o de projetos com o Codex

O Codex nÃ£o serve sÃ³ para cÃ³digo â€” Ã© um bom assistente de gestÃ£o de projetos. Como usÃ¡-lo para tocar projetos, sprints e tarefas:

<details>
<summary><strong>Planejamento e quebra de escopo</strong></summary>

```bash
# Quebrar um pedido grande de feature
codex "Quebre este pedido de feature em tarefas acionÃ¡veis:
- Sistema de autenticaÃ§Ã£o de usuÃ¡rio
- Precisa suportar OAuth e e-mail
- Incluir fluxo de recuperaÃ§Ã£o de senha
- Adicionar opÃ§Ã£o de 2FA"

# Gerar backlog de sprint
codex exec "Analise este projeto e crie um backlog de sprint:
- Priorize por complexidade
- Estime o esforÃ§o em horas
- Identifique dependÃªncias"

# Criar histÃ³rias de usuÃ¡rio
codex "Converta estes requisitos em histÃ³rias de usuÃ¡rio com critÃ©rios de aceite"
```

</details>

<details>
<summary><strong>IntegraÃ§Ã£o com o GitHub</strong></summary>

```bash
# Gerar descriÃ§Ãµes de PR automaticamente
git diff | codex exec "Crie uma descriÃ§Ã£o detalhada de PR com:
- Resumo das mudanÃ§as
- Testes realizados
- Breaking changes (se houver)"

# Criar issues a partir de comentÃ¡rios TODO
codex exec "Varra o projeto atrÃ¡s de TODO/FIXME e crie issues no GitHub"

# Gerar notas de release
codex exec "Crie notas de release a partir dos commits recentes"
```

</details>

<details>
<summary><strong>Acompanhamento e status</strong></summary>

```bash
# Gerar relatÃ³rio de status
codex "Revise os commits recentes e gere um relatÃ³rio de status para os stakeholders"

# Acompanhar progresso
codex "Que porcentagem das tarefas do sprint estÃ¡ concluÃ­da, com base nos PRs mergeados?"

# Identificar riscos
codex "Analise este projeto e identifique possÃ­veis bloqueios ou riscos"
```

</details>

<details>
<summary><strong>PadrÃµes de colaboraÃ§Ã£o em time</strong></summary>

```bash
# AutomaÃ§Ã£o de revisÃ£o de cÃ³digo
codex "Revise este PR quanto a:
- Vulnerabilidades de seguranÃ§a
- Problemas de performance
- PadrÃµes de qualidade de cÃ³digo
- Lacunas de cobertura de testes"

# Sincronizar documentaÃ§Ã£o
codex "Atualize o README com base nas features adicionadas recentemente"

# Ajuda no onboarding
codex "Crie um guia de onboarding de desenvolvedor para este projeto"
```

</details>

<details>
<summary><strong>Criando skills de gestÃ£o de projeto</strong></summary>

VocÃª pode criar skills sob medida para o fluxo do seu time:

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
- Formato de retrospectiva: ComeÃ§ar/Parar/Continuar
```

</details>

## NÃ­vel 5: Workflows de especialista

PadrÃµes avanÃ§ados e automaÃ§Ã£o.

<details>
<summary><strong>IntegraÃ§Ã£o com GitHub Actions</strong></summary>

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
<summary><strong>RevisÃ£o de cÃ³digo automatizada</strong></summary>

```bash
# Revisar o PR inteiro
codex "Revise este PR quanto a seguranÃ§a, performance e manutenibilidade"

# Gerar mensagens de commit no padrÃ£o conventional
git diff HEAD~1 | codex exec "Crie uma mensagem de commit no padrÃ£o conventional"

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
<summary><strong>MigraÃ§Ã£o de cÃ³digo legado</strong></summary>

```bash
# Converter entre linguagens
codex "Converta este utilitÃ¡rio Python para TypeScript"

# Atualizar APIs descontinuadas
codex "Converta todos os componentes de classe React em componentes funcionais com hooks"

# Adicionar seguranÃ§a de tipos
codex "Adicione tipos TypeScript a este projeto JavaScript"
```

</details>

<details>
<summary><strong>OtimizaÃ§Ã£o de performance</strong></summary>

```bash
# Analisar gargalos
codex "FaÃ§a o profiling deste cÃ³digo e identifique gargalos de performance"

# Otimizar consultas ao banco
codex "Refatore estas consultas N+1 para usar carregamento em lote"

# Otimizar o bundle
codex "Sugira otimizaÃ§Ãµes de webpack para reduzir o tamanho do bundle"
```

</details>

<details>
<summary><strong>Auditoria de seguranÃ§a</strong></summary>

```bash
# Encontrar vulnerabilidades
codex "Audite este cÃ³digo em busca de vulnerabilidades de seguranÃ§a"

# Checar dependÃªncias
codex "Revise o package.json procurando dependÃªncias desatualizadas ou vulnerÃ¡veis"

# Checar conformidade
codex "Verifique se este cÃ³digo segue as diretrizes de seguranÃ§a da OWASP"
```

</details>

<details>
<summary><strong>DiagnÃ³stico e depuraÃ§Ã£o</strong></summary>

```bash
# Analisar logs de erro
cat error.log | codex exec "encontre a causa raiz"

# Depurar uma funÃ§Ã£o especÃ­fica
codex "Descubra por que a funÃ§Ã£o de login estÃ¡ falhando"

# Reproduzir e corrigir
codex "Crie um caso de teste que reproduza este bug e depois corrija"
```

</details>

<details>
<summary><strong>DocumentaÃ§Ã£o</strong></summary>

```bash
# Gerar README
codex exec "Crie um README completo para este projeto"

# DocumentaÃ§Ã£o de API
codex exec "Gere a documentaÃ§Ã£o de API a partir dos comentÃ¡rios JSDoc"

# ComentÃ¡rios de cÃ³digo
codex "Adicione comentÃ¡rios detalhados a esta funÃ§Ã£o complexa"
```

</details>

<details>
<summary><strong>Testes</strong></summary>

```bash
# Gerar testes
codex "Crie testes unitÃ¡rios para todas as funÃ§Ãµes de utils.js"

# Cobertura de testes
codex "Analise a cobertura de testes e sugira os testes que faltam"

# Testes E2E
codex "Crie testes E2E com Playwright para o fluxo do usuÃ¡rio"
```

</details>

<details>
<summary><strong>RefatoraÃ§Ã£o</strong></summary>

```bash
codex "Refatore este cÃ³digo para:
1. Melhorar a legibilidade
2. Adicionar tratamento de erro
3. Seguir as boas prÃ¡ticas de TypeScript
4. Adicionar definiÃ§Ãµes de tipo"
```

</details>

## Recursos adicionais

**DocumentaÃ§Ã£o oficial do OpenAI Codex:**
- [RepositÃ³rio oficial](https://github.com/openai/codex) â€” repositÃ³rio principal e central de documentaÃ§Ã£o
- [Guia de inÃ­cio](https://developers.openai.com/codex/quickstart) â€” guia completo para comeÃ§ar
- [ReferÃªncia de configuraÃ§Ã£o](https://developers.openai.com/codex/configuration) â€” referÃªncia completa do config.toml
- [Comandos de desenvolvedor](https://developers.openai.com/codex/developer-commands) â€” comandos, flags e slash commands
- [Modo nÃ£o interativo (exec)](https://developers.openai.com/codex/non-interactive-mode) â€” automaÃ§Ã£o com codex exec
- [AutenticaÃ§Ã£o](https://developers.openai.com/codex/auth) â€” mÃ©todos de autenticaÃ§Ã£o
- [Sandbox e aprovaÃ§Ãµes](https://developers.openai.com/codex/sandboxing) â€” seguranÃ§a e sandbox
- [DocumentaÃ§Ã£o do AGENTS.md](https://developers.openai.com/codex/agent-configuration/agents-md) â€” instruÃ§Ãµes por projeto
- [IntegraÃ§Ã£o MCP](https://developers.openai.com/codex/configuration) â€” configuraÃ§Ã£o e uso de MCP
- [Prompts customizados](https://developers.openai.com/codex/prompting) â€” como criar prompts prÃ³prios
- [FAQ](https://developers.openai.com/codex/reference/troubleshooting) â€” perguntas frequentes
- [Skills](https://developers.openai.com/codex/skills-and-plugins) â€” guia oficial

**ExtensÃµes e integraÃ§Ãµes:**
- [GitHub Action](https://github.com/openai/codex-action) â€” integraÃ§Ã£o com CI/CD
- [SDK TypeScript](https://developers.openai.com/codex/codex-sdk) â€” uso programÃ¡tico
- [ExtensÃ£o do VS Code](https://developers.openai.com/codex/ide) â€” integraÃ§Ã£o com a IDE

**Model Context Protocol:**
- [EspecificaÃ§Ã£o do MCP](https://modelcontextprotocol.io/) â€” documentaÃ§Ã£o oficial do protocolo
- [Exemplos de servidores MCP](https://github.com/modelcontextprotocol/servers) â€” servidores da comunidade

> **Dica:** confira sempre a [documentaÃ§Ã£o oficial do Codex](https://github.com/openai/codex) para os recursos e atualizaÃ§Ãµes mais recentes. Esta folha de consulta Ã© uma referÃªncia rÃ¡pida; a doc oficial Ã© a fonte mais completa e atual.

## Contribuindo

Achou um problema ou tem uma sugestÃ£o? ContribuiÃ§Ãµes sÃ£o bem-vindas!

- Reporte bugs ou problemas
- Sugira novos exemplos
- Melhore a documentaÃ§Ã£o
- Compartilhe seus workflows

## LicenÃ§a

LicenÃ§a MIT â€” livre para usar e modificar.
