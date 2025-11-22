# 🛠️ Tools Essentials

> Utilitários modernos multiplataforma para aumentar produtividade no terminal

![Tools Essentials](../img/tools-essentials.webp)

Estas ferramentas funcionam em **todos os sistemas operacionais** (Windows via WSL2, Linux e macOS) e complementam seu ambiente de desenvolvimento.

---

## 📋 Índice

1. **[Neovim](#neovim)** - Editor de texto moderno baseado no Vim
2. **[mise](#mise)** - Gerenciador de versões de linguagens e ferramentas
3. **[eza](#eza)** - Substituto moderno do `ls`
4. **[zoxide](#zoxide)** - Navegação inteligente entre diretórios
5. **[fzf](#fzf)** - Busca fuzzy interativa no terminal

---

## Neovim

Editor de texto moderno e extensível, evolução do Vim com foco em extensibilidade e performance.

**Por que usar?**
- ⚡ Extremamente rápido e leve
- 🔌 Suporte nativo a LSP (Language Server Protocol)
- 🎨 Ecossistema rico de plugins (Lua)
- 🚀 Ideal para edições rápidas via terminal
- 💡 Complementa o VSCode para tarefas no servidor

**Instalação:**
- **[neovim.io](https://neovim.io/)** - Instruções para cada plataforma

💡 **Dica:** Use Neovim para edições rápidas via SSH e VSCode para desenvolvimento local.

**Configurações avançadas (opcional):**

Para quem quiser uma experiência mais IDE-like com Neovim:
- [LazyVim](https://www.lazyvim.org/) - Distribuição moderna pré-configurada
- [NvChad](https://nvchad.com/) - Configuração rápida e elegante
- [AstroNvim](https://astronvim.com/) - IDE-like com ótimos padrões

---

## mise

Gerenciador universal de versões para linguagens de programação e ferramentas de desenvolvimento.

**O que faz?**
- 🔄 Gerencia versões de Node.js, Python, Ruby, Go, Rust, Java e dezenas de outras ferramentas
- 📁 Suporte a `.tool-versions` (compatível com asdf)
- ⚡ Escrito em Rust - extremamente rápido
- 🎯 Simples de usar - um comando para instalar qualquer ferramenta

**Substitui:**
- asdf (mais rápido e mais seguro)
- nvm, pyenv, rbenv, goenv, etc.

**Instalação:**
- **[mise.jdx.dev](https://mise.jdx.dev/)** - Guia de instalação completo

**Exemplos de uso:**
```bash
# Instalar Node.js
mise use -g node@20

# Instalar Python
mise use -g python@3.12

# Instalar múltiplas ferramentas
mise use -g node@20 python@3.12 go@1.21

# Listar ferramentas instaladas
mise list

# Ver versões disponíveis
mise ls-remote node
```

💡 **Dica:** Use `mise use` no seu projeto para fixar versões específicas de ferramentas.

---

## eza

Substituto moderno do comando `ls` com cores, ícones e recursos avançados.

**Por que usar?**
- 🎨 Cores e ícones por padrão
- 📊 Exibição em tree, grid e long format
- 🔍 Integração com Git (mostra status dos arquivos)
- ⚡ Escrito em Rust - rápido e confiável
- 🌳 Visualização de árvore de diretórios integrada

**Instalação:**
- **[github.com/eza-community/eza](https://github.com/eza-community/eza)** - Instruções de instalação

**Exemplos de uso:**
```bash
# Listar arquivos com ícones
eza

# Formato detalhado com git status
eza -l --git

# Visualizar como árvore
eza --tree

# Listar tudo, inclusive ocultos
eza -la
```

**Aliases recomendados:**
```bash
alias lz="eza --color=always --long --no-filesize --icons=always --no-time --no-user --no-permissions"
alias lsz="eza --color=always --long --no-filesize --icons=always --no-time --no-user -la"
alias lt="eza --tree --icons"
```

⚠️ **Importante:** Não substitua o comando `ls` padrão (ex: `alias ls="eza"`). Ferramentas de IA como GitHub Copilot e Claude precisam do output padrão do `ls` para entender a estrutura de diretórios. Crie aliases separados como `lz` e `lsz` para usar quando precisar da visualização com ícones.

💡 **Dica:** Combine com `--git-ignore` para ignorar arquivos do `.gitignore` ao listar.

---

## zoxide

Navegação inteligente entre diretórios baseada em frequência e recência de uso.

**O que faz?**
- 🧠 Aprende seus diretórios mais usados
- ⚡ Pule para qualquer diretório com poucas letras
- 📊 Ranqueia diretórios por frequência de acesso
- 🔍 Busca fuzzy integrada

**Instalação:**
- **[github.com/ajeetdsouza/zoxide](https://github.com/ajeetdsouza/zoxide)** - Guia completo

**Configuração:**

Para Fish:
```bash
# Adicione ao ~/.config/fish/config.fish
zoxide init fish | source
```

Para Zsh:
```bash
# Adicione ao ~/.zshrc
eval "$(zoxide init zsh)"
```

**Exemplos de uso:**
```bash
# Após visitar /home/user/projects/meu-app várias vezes
z meu    # Pula direto para /home/user/projects/meu-app

# Busca interativa com fzf
zi meu   # Abre lista de diretórios que contêm "meu"

# Ver histórico e scores
zoxide query --list
```

⚠️ **Importante:** Use o comando `z` ao invés de substituir o `cd` padrão (ex: `alias cd="z"`). Substituir o `cd` pode afetar ferramentas de IA e o autocompletar do shell. Quanto mais você usar o comando `z` para navegar, mais o histórico será atualizado, permitindo pular para pastas mais facilmente.

💡 **Dica:** Combine com `fzf` para busca interativa usando `zi` ao invés de `z`.

---

## fzf

Fuzzy finder interativo para linha de comando - busca qualquer coisa rapidamente.

**O que faz?**
- 🔍 Busca fuzzy em qualquer lista (arquivos, histórico, processos)
- ⚡ Extremamente rápido mesmo com milhões de entradas
- 🎨 Interface interativa e customizável
- 🔌 Integração com shell (Ctrl+R para histórico, Ctrl+T para arquivos)

**Instalação:**
- **[github.com/junegunn/fzf](https://github.com/junegunn/fzf)** - Instruções completas

**Atalhos padrão após instalação:**
- `Ctrl+R` - Buscar no histórico de comandos
- `Ctrl+T` - Buscar arquivos e diretórios
- `Alt+C` - Navegar para um diretório

**Configuração recomendada:**

Adicione ao seu `~/.config/fish/config.fish` (Fish) ou `~/.zshrc` (Zsh):

```bash
export FZF_CTRL_T_OPTS="
  --walker-skip .git,node_modules,target,.history
  --preview 'bat -n --color=always {}'
  --bind 'ctrl-/:change-preview-window(down|hidden|)'"

export FZF_CTRL_R_OPTS="
  --bind 'ctrl-y:execute-silent(echo -n {2..} | pbcopy)+abort'
  --color header:italic
  --header 'Press CTRL-Y to copy command into clipboard'"

export FZF_ALT_C_OPTS="
  --walker-skip .git,node_modules,target
  --preview 'tree -C {}'"
```

Essas configurações melhoram a experiência com os três atalhos:
- `Ctrl+T`: Ignora pastas comuns (node_modules, .git), mostra preview com `bat`, alterna preview com `Ctrl+/`
- `Ctrl+R`: Permite copiar comando para clipboard com `Ctrl+Y`
- `Alt+C`: Ignora pastas comuns, mostra estrutura de diretórios com `tree`

**Exemplos de uso:**
```bash
# Abrir arquivo no editor
vim $(fzf)

# Matar processo interativamente
kill -9 $(ps aux | fzf | awk '{print $2}')

# Buscar em commits do git
git log --oneline | fzf

# Navegar e entrar em diretório
cd $(find . -type d | fzf)

# Checkout em branch do git
git checkout $(git branch | fzf | sed 's/^[ *]*//')
```

💡 **Dica:** Configure `FZF_DEFAULT_OPTS` para personalizar cores e comportamento.

---

## 🎯 Instalação

Todas essas ferramentas estão disponíveis para **macOS, Linux e Windows**.

💡 **Nota para Windows:** As ferramentas podem ser instaladas tanto no ambiente Windows nativo (via Chocolatey, Scoop, Winget) quanto no WSL2 (usando os gerenciadores de pacotes do Linux).

Consulte a documentação oficial de cada ferramenta (links acima) para instruções específicas do seu sistema operacional.

---

[← Voltar ao README principal](../README.md)
