# Neovim Plugin Guide

## which-key

Does nothing until you press a prefix key and pause. Then a popup shows all available continuations.

- Press `\` and wait 300ms — see all your leader bindings grouped by category
- Press `g` and wait — see all `g`-prefixed motions (gd, gq, etc.)
- Press `z` and wait — see folds, spelling, etc.

Groups defined: `\f` = find, `\x` = diagnostics, `\c` = code/citations, `\n` = notes, `\t` = terminal, `\j` = julia. These labels appear in the popup so you can orient yourself.

---

## nvim-surround

( { { [ (  ) ] } } operations, all work with any bracket/quote/tag/LaTeX command: )

| Action | Key | Example |
|---|---|---|
| **Add** | `ys{motion}{char}` | `ysiw)` → surround word with `()` |
| **Change** | `cs{old}{new}` | `cs"'` → change `"hello"` to `'hello'` |
| **Delete** | `ds{char}` | `ds)` → remove surrounding `()` |

**LaTeX-specific usage:**
- `ysiw}` on `word` → `{word}` (no spaces; use `{` for spaces: `{ word }`)
- `ysiwf` then type `textbf` → `\textbf{word}` (the `f` surrounds with a function call)
- `ysiwf` then type `emph` → `\emph{word}`
- `yss}` — surround entire line in `{}`
- Works in visual mode too: select text, `S)` to wrap selection

---

## todo-comments

Write these keywords in comments and they'll be highlighted automatically:

```
% TODO: finish derivation of eq. 3.12
% FIXME: wrong sign in exponent
% NOTE: reviewer asked about this assumption
% HACK: temporary workaround for texlab bug
```

| Key | What |
|---|---|
| `]t` / `[t` | Jump to next/prev TODO in buffer |
| `\xt` | List all TODOs in Trouble (persistent split) |
| `\ft` | List all TODOs in Telescope (fuzzy search) |

Works in any filetype — `.tex`, `.py`, `.lua`, etc.

---

## undotree

| Key | What |
|---|---|
| `\u` | Toggle the undo tree panel |

Once open:
- `j`/`k` — navigate undo history
- `<CR>` — select a state (buffer updates live as you move)
- The right pane shows a diff of what changed
- `q` — close

The killer feature: nvim's undo is a **tree**, not a line. If you undo 5 times then type something new, the old branch isn't lost — undotree lets you see and recover it. This persists across sessions as long as you have `undofile` set (check with `:set undofile?`).

---

## Telescope & Trouble

### When to use which

**Telescope** = "I want to find and jump to one thing quickly"
- Fuzzy search, preview pane, one-shot navigation
- Pick an item → press `<CR>` → you're there

**Trouble** = "I want to see everything and work through a list"
- Persistent split that stays open as you fix things
- Auto-updates as diagnostics change — great for fixing errors one by one

### Keybinds

| Key    | Tool      | What it shows              |
|--------|-----------|----------------------------|
| `\fd`  | Telescope | All diagnostics (fuzzy searchable) |
| `\fq`  | Telescope | Quickfix list              |
| `\fl`  | Telescope | Location list              |
| `\ff`  | Telescope | Find files                 |
| `\fg`  | Telescope | Live grep                  |
| `\fb`  | Telescope | Buffers                    |
| `\fh`  | Telescope | Help tags                  |
| `\ft`  | Telescope | TODOs                      |
| `\xx`  | Trouble   | All diagnostics (persistent split) |
| `\xX`  | Trouble   | Buffer diagnostics only    |
| `\xQ`  | Trouble   | Quickfix list              |
| `\xL`  | Trouble   | Location list              |
| `\xt`  | Trouble   | TODOs                      |
| `\cs`  | Trouble   | Document symbols           |
| `\cl`  | Trouble   | LSP definitions/references |

### Typical workflows

**Fixing compile/lint errors across files:**
Open `\xx` (Trouble) — it lists all workspace diagnostics grouped by file. Jump between them with `j`/`k` and `<CR>`. The list updates live as you fix things. Close with `q`.

**"I know roughly what the error says":**
Use `\fd` (Telescope) — type part of the message or filename to filter, hit `<CR>` to jump.

**After `:make`, `:grep`, or vimtex build errors:**
These populate the quickfix list. Use `\fq` (Telescope) to fuzzy-pick one entry, or `\xQ` (Trouble) to see the full list in a persistent split.

**Exploring a symbol's usage:**
`\cl` (Trouble) — shows definitions, references, implementations in a side panel. Good for understanding how something is used without losing your place.

**Quick Trouble tips:**
- `o` — jump to item without closing Trouble
- `<CR>` — jump and close
- `q` — close the Trouble window
- Trouble remembers its position — reopen with the same bind to resume
