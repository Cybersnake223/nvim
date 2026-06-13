# nvim

Personal Neovim config for data science, SQL, and everyday development.

## Highlights

- **Data Science** — Molten (Jupyter), Quarto, image.nvim, jupytext
- **SQL** — nvim-dbee client + dadbod completion via blink.cmp
- **LSP** — ruff, lua_ls, sqls, bashls, marksman via mason
- **Fast picker** — Snacks picker replaces telescope (files, grep, buffers, recent, help, keymaps)
- **Snacks ecosystem** — explorer, terminal, indent guides, words, notifier, session
- **Neogit** — Magit-like Git UI with diffview integration
- **Markdown rendering** — render-markdown.nvim in quarto/markdown files

## File Structure

```
~/.config/nvim/
├── init.lua                  # Bootstrap, autocommands
├── lazy-lock.json            # Plugin lockfile
├── .stylua.toml              # StyLua config
└── lua/
    ├── options.lua            # Editor options, providers, paths
    ├── mappings.lua           # All keymaps
    ├── commands.lua           # User commands + autocmds
    └── plugins/
        ├── init.lua           # Plugin specs (50+ plugins)
        └── configs/           # Per-plugin config
            ├── blink_conf.lua # Completion engine
            ├── conform.lua    # Format on save
            ├── dbee.lua       # SQL client
            ├── lspconfig.lua  # LSP attach, per-server settings
            ├── lualine.lua    # Statusline + tabline
            ├── nightfox.lua   # Colorscheme + highlights
            ├── snacks.lua     # Snacks modules
            └── treesitter.lua # Parsers + language setup
```

## Plugins

### LSP & Completion

| Plugin               | Role                                |
|----------------------|-------------------------------------|
| mason.nvim           | LSP/formatter/linter installer      |
| mason-lspconfig.nvim | Auto-install: lua_ls, ruff, sqls, bashls, marksman |
| nvim-lspconfig       | LSP client config + keymaps          |
| blink.cmp            | Completion engine (Rust fuzzy)       |
| LuaSnip              | Snippet engine                       |
| friendly-snippets    | Snippet collection                   |
| lazydev.nvim         | Lua LSP library annotations          |
| nvim-autopairs       | Auto-close brackets                  |

### Formatting & Linting

| Plugin      | Role                          |
|-------------|--------------------------------|
| conform.nvim| Format on save (StyLua, ruff, LSP) |
| nvim-lint   | Async linting (ruff, shellcheck, sqlfluff) |
| Auto-trim trailing whitespace on save |

### Data Science

| Plugin            | Role                                    |
|-------------------|-----------------------------------------|
| quarto-nvim       | Quarto notebook + multilevel LSP        |
| otter.nvim        | Inline language LSP in Quarto/markdown  |
| molten-nvim       | Jupyter kernel (run cells, show output) |
| image.nvim        | Image rendering in Kitty terminal       |
| jupytext.nvim     | Paired .ipynb ↔ markdown workflow       |
| `:NewNotebook`    | Scaffold a new .ipynb file              |

### Database

| Plugin                 | Role                           |
|------------------------|--------------------------------|
| nvim-dbee              | SQL client with connections     |
| vim-dadbod-completion  | DB-aware completion in blink.cmp|
| CSV/TSV export to `~/Sql/csv/` |                     |

### Git

| Plugin            | Role                              |
|-------------------|-----------------------------------|
| gitsigns.nvim     | Inline blame, hunk stage/diff     |
| neogit            | Magit-like Git UI                 |
| diffview.nvim     | Diff viewer (neogit integration)  |

### UI & Navigation

| Plugin               | Role                               |
|----------------------|------------------------------------|
| nightfox.nvim        | Colorscheme (transparent, custom hl)|
| lualine.nvim         | Statusline + buffer tabline         |
| which-key.nvim       | Popup keymap help                   |
| snacks.nvim          | Picker, explorer, terminal, indent, notifier, session, words |
| nvim-ufo             | LSP + treesitter folding            |
| flash.nvim           | Label-based cursor jump (`s`/`S`)   |
| render-markdown.nvim | Rendered markdown preview           |

### Editing

| Plugin            | Role                           |
|-------------------|--------------------------------|
| mini.surround     | `gsa`/`gsd`/`gsr` surround ops |
| mini.ai           | Treesitter-aware text objects   |
| mini.hipatterns   | Hex color highlighting          |
| nvim-treesitter   | Parsers, syntax highlighting    |
| nvim-ufo          | Code folding                    |

## Keymaps

### Navigation

| Key         | Action              |
|-------------|---------------------|
| `<Tab>`     | Next buffer         |
| `<S-Tab>`   | Previous buffer     |
| `<leader>bd`| Close buffer        |
| `<A-h/j/k/l>`| Window movement    |
| `<C-Arrows>`| Resize windows      |

### Find (Snacks picker)

| Key          | Action            |
|--------------|-------------------|
| `<leader>e`  | Explorer          |
| `<leader>ff` | Files             |
| `<leader>fg` | Grep              |
| `<leader>fb` | Buffers           |
| `<leader>fr` | Recent files      |
| `<leader>fh` | Help              |
| `<leader>fk` | Keymaps           |
| `<leader>fc` | Commands          |
| `<leader>fw` | Word under cursor |

### LSP

| Key          | Action                |
|--------------|-----------------------|
| `gd`         | Go to definition      |
| `gD`         | Go to declaration     |
| `gr`         | Find references       |
| `gi`         | Go to implementation  |
| `K`          | Hover documentation   |
| `<C-k>`      | Signature help        |
| `<leader>lr` | Rename                |
| `<leader>la` | Code action           |
| `<leader>lf` | Format                |
| `<leader>ls` | Buffer symbols        |
| `<leader>ld` | Hover diagnostic      |
| `]d` / `[d`  | Next/prev diagnostic  |

### Git

| Key           | Action          |
|---------------|-----------------|
| `<leader>gg`  | Neogit status   |
| `<leader>gc`  | Neogit commit   |
| `<leader>gl`  | Neogit log      |
| `<leader>gb`  | Git blame line  |
| `<leader>gh`  | Preview hunk    |
| `<leader>gs`  | Stage hunk      |
| `<leader>gr`  | Reset hunk      |
| `<leader>gd`  | Diff this       |
| `]h` / `[h`   | Next/prev hunk  |

### Data Science (Molten)

| Key           | Action              |
|---------------|---------------------|
| `<leader>mi`  | Init Python kernel  |
| `<leader>ms`  | Shared kernel       |
| `<leader>mR`  | Restart kernel      |
| `<leader>mI`  | Interrupt kernel    |
| `<leader>mO`  | Show output window  |
| `<leader>mc`  | Re-run cell         |

### Quarto / Markdown

| Key           | Action              |
|---------------|---------------------|
| `<leader>qa`  | Quarto activate     |
| `<leader>mr`  | Toggle markdown rendering |
| `<leader>r`   | Run cell            |
| `<leader>ra`  | Run all cells       |
| `<leader>rl`  | Run line            |
| `<leader>n`   | New Python chunk    |

### Database

| Key           | Action              |
|---------------|---------------------|
| `<leader>db`  | Open dbee           |
| `<leader>dc`  | Export result as CSV|

### Misc

| Key           | Action              |
|---------------|---------------------|
| `<C-s>`       | Save file           |
| `jk`          | Exit insert mode    |
| `<leader>/`   | Toggle comment line |
| `<leader>Y`   | Copy entire file    |
| `<leader>tt`  | Toggle terminal     |
| `<leader>P`   | Lazy plugin menu    |
| `<leader>M`   | Mason menu          |
| `s` / `S`     | Flash jump fwd/bwd  |

## Getting Started

```bash
# Prerequisites
#   - Neovim >= 0.11
#   - A Nerd Font (terminal)
#   - Python 3 + pynvim (for Molten)
#   - Kitty terminal (for image rendering)

# Backup existing config
mv ~/.config/nvim ~/.config/nvim.bak

# Clone
git clone https://github.com/cybersnake223/nvim ~/.config/nvim

# Start Neovim — lazy.nvim installs all plugins automatically
nvim

# Install LSP servers, formatters, and linters
:MasonInstallAll
```

## Requirements

- **Neovim** >= 0.11 (uses `vim.lsp.config`, `vim.treesitter.language.register`)
- **Nerd Font** — for icons in statusline, picker, which-key, etc.
- **Python 3** with `pynvim` (`pip install pynvim`) — required by Molten
- **Kitty terminal** — recommended for inline image rendering in notebooks
- **Optional**: `VIRTUAL_ENV` or `~/.venv` — auto-detected for `python3_host_prog`
