# nvim

Personal Neovim configuration powered by [lazy.nvim](https://github.com/folke/lazy.nvim).

## Structure

```
~/.config/nvim/
├── init.lua              # Entry point: bootstrap, autocommands
├── lazy-lock.json        # Plugin version lockfile
├── .stylua.toml          # StyLua formatter settings
└── lua/
    ├── options.lua        # Core options (leader, UI, indent, providers)
    ├── mappings.lua       # Keymaps (editing, windows, git, LSP, data science)
    ├── commands.lua       # User commands & autocommands
    └── plugins/
        ├── init.lua       # Plugin specs & setup
        └── configs/       # Per-plugin configuration modules
            ├── blink_conf.lua
            ├── conform.lua
            ├── dbee.lua
            ├── lspconfig.lua
            ├── lualine.lua
            ├── nightfox.lua
            ├── snacks.lua
            └── treesitter.lua
```

## Features

### LSP & Completion
- **mason.nvim** — manage LSP servers, formatters, and linters
- **nvim-lspconfig** — configured: `lua_ls`, `ruff`, `sqls`, `bashls`, `marksman`
- **blink.cmp** — fast completion with LSP, snippets, buffer, path, and dadbod sources
- **luasnip** + **friendly-snippets** — snippet engine and collection

### Formatting & Linting
- **conform.nvim** — format on save (StyLua, ruff, LSP formatters)
- **nvim-lint** — async linting with ruff, shellcheck, sqlfluff
- Auto-trim trailing whitespace on save

### Data Science
- **quarto-nvim** + **otter.nvim** — Quarto notebook support with inline Python execution
- **molten-nvim** — Jupyter kernel integration for markdown/quarto/ipynb
- **image.nvim** — image rendering (Kitty terminal) inside notebooks
- **jupytext.nvim** — paired `.ipynb` ↔ markdown workflow
- `:NewNotebook <name>` — scaffold a new `.ipynb`

### Database
- **nvim-dbee** — SQL client with connection management and CSV export
- **vim-dadbod-completion** — database-aware completion via blink.cmp

### Git
- **gitsigns.nvim** — inline blame, hunk staging, diff preview
- **neogit** — Magit-like Git UI (status, commit, log, pull, push)

### UI & Navigation
- **nightfox.nvim** — colorscheme (transparent, custom highlights)
- **lualine.nvim** — statusline + tabline with buffers
- **which-key.nvim** — keymap popup help
- **snacks.nvim** — picker (files, grep, buffers, recent, etc.), file explorer, terminal, indent guides, notifier, session management
- **nvim-ufo** — LSP + treesitter folding, peek folded lines
- **flash.nvim** — fast cursor motion (`s` / `S`)
- **render-markdown.nvim** — rendered markdown preview

### Editing
- **mini.surround** — `gsa`/`gsd`/`gsr` for surround operations
- **mini.ai** — treesitter-aware text objects (blocks, functions, classes)
- **mini.hipatterns** — hex color highlighting
- **nvim-autopairs** — auto-close brackets
- **zen-mode.nvim** — distraction-free writing

## Getting Started

```bash
# Backup existing config
mv ~/.config/nvim ~/.config/nvim.bak

# Clone
git clone https://github.com/cybersnake223/nvim ~/.config/nvim

# Start Neovim — plugins install automatically
nvim

# (Optional) Install all LSP servers, formatters, and linters
:MasonInstallAll
```

## Keymaps

| Prefix    | Group       |
|-----------|-------------|
| `<leader>b` | buffer      |
| `<leader>d` | database    |
| `<leader>e` | explorer    |
| `<leader>f` | find        |
| `<leader>g` | git         |
| `<leader>l` | lsp         |
| `<leader>m` | molten      |
| `<leader>r` | run         |
| `<leader>S` | session     |
| `<leader>t` | terminal    |
| `<leader>w` | workspace   |

Press `<leader>?` to see buffer-local keymaps via which-key.

## Requirements

- Neovim >= 0.11
- Nerd Font (for icons)
- Python 3 with `pynvim` (for Molten)
- Kitty terminal (recommended for image rendering)
