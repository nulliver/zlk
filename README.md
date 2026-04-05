# Zed Leader Keymap

A custom keymap for [Zed](https://zed.dev) built around a leader/chord-prefix design principle: **every action belongs to a named group, and every group has a single `⌘ letter` prefix**.

Many keymaps are inspired by **vi** and **Emacs**, and this one is not the exception, but it's also inspired by the excellent work done by Dmitry Matveev creating and maintaining the [Mnemonic key map for IntelliJ](https://github.com/dmimat/intellij-mnemonic-keymap), which I used during a time I had to frequently switch between Windows and macOS for IntelliJ IDEA.

This keymap can also be an starting point for anybody looking for an alternative keymap. It can be specially useful for users with non-English layout keybords, where non-alphanumeric characters are in less accessible positions when using the default keymap.

---

## How It Works

Each group is activated with **⌘ + a prefix letter** (group), followed by a **second letter** for the action:

```
⌘ J  →  then  D   =  Go to Definition
⌘ R  →  then  R   =  Rename symbol
⌘ W  →  then  T   =  Toggle Terminal panel
```

Every binding has **two forms** so you can type at your own pace:

| Form          | How to type             |
| ------------- | ----------------------- |
| `⌘ X` · `Y`   | Release ⌘, then press Y |
| `⌘ X` · `⌘ Y` | Keep ⌘ held throughout  |

**Platform note:**

In the `keymap.json` file, `super` maps to:

- `⌘` on macOS
- `Win` on Windows
- `Super` on Linux.

The keymap uses Zed's `super` and `secondary` modifier keys throughout for portability.

---

## Installation

Copy `keymap.json` to your Zed config directory:

```bash
# macOS / Linux
cp keymap.json ~/.config/zed/keymap.json
```

Then in `settings.json`, make sure VSCode is the base key map, since this keymap is designed on top of it:

```json
{
  "base_keymap": "VSCode"
}
```

Restart Zed.

---

## Command Reference

### Group Summary

| Prefix | Group        | Purpose                                             |
| ------ | ------------ | --------------------------------------------------- |
| `⌘ J`  | **J**ump     | Go to definition, references, bracket, back/forward |
| `⌘ N`  | **N**avigate | File finder, project symbols, search                |
| `⌘ R`  | **R**efactor | Rename, format, imports, code actions, completions  |
| `⌘ L`  | **L**ine     | Duplicate, delete, join, comment, new line          |
| `⌘ B`  | **B**lock    | Selection expansion, multi-cursor, folding          |
| `⌘ F`  | **F**ind     | Buffer search, project search, match navigation     |
| `⌘ E`  | **E**ditor   | Splits, pane focus, pane swap, tabs, preview        |
| `⌘ W`  | **W**indow   | Panel and dock toggles, recent/remote projects      |

---

### Debugging — F-key Layout

No prefix.

| Key    | Action                            | Notes                                                        |
| ------ | --------------------------------- | ------------------------------------------------------------ |
| `F4`   | Spawn Task                        | Choose from a list                                           |
| `⇧F4`  | Rerun Last Task                   |                                                              |
| `F5`   | Start / Rerun / Continue          | Starts when idle, reruns when running, continues when paused |
| `⇧F5`  | Stop                              |                                                              |
| `F6`   | Step Over                         |                                                              |
| `F7`   | Step Into                         |                                                              |
| `⇧F7`  | Step Out                          |                                                              |
| `F8`   | Toggle Breakpoint                 |                                                              |
| `⇧F8`  | Edit Log / Conditional Breakpoint |                                                              |
| `⌘ F8` | Clear All Breakpoints             |                                                              |
| `F9`   | Next Diagnostic                   |                                                              |
| `⇧F9`  | Previous Diagnostic               |                                                              |

---

### ⌘ J — Jump

Single-destination navigation.

| Keys        | Action                                  |
| ----------- | --------------------------------------- |
| `⌘ J` · `D` | Go to Definition                        |
| `⌘ J` · `T` | Go to Type Definition                   |
| `⌘ J` · `I` | Go to Implementation                    |
| `⌘ J` · `R` | Find All References                     |
| `⌘ J` · `J` | Move to Matching / Enclosing Bracket    |
| `⌘ J` · `S` | Move to Start of Paragraph              |
| `⌘ J` · `E` | Move to End of Paragraph                |
| `⌘ J` · `H` | Hover / Show Documentation              |
| `⌘ J` · `B` | Go Back (history)                       |
| `⌘ J` · `F` | Go Forward (history)                    |
| `⌘ J` · `L` | Go to Line                              |
| `⌘ J` · `P` | Reveal File in Project Panel            |
| `⌘ J` · `O` | Outline Picker (jump to symbol in file) |

> **Context note:** Symbol jumps (`D`, `T`, `I`, `R`, `J`, `S`, `E`, `H`) require editor focus. History and workspace jumps (`B`, `F`, `L`, `P`, `O`) work from anywhere.

---

### ⌘ N — Navigate

Multi-destination navigation.

| Keys        | Action                         |
| ----------- | ------------------------------ |
| `⌘ N` · `F` | File Finder                    |
| `⌘ N` · `S` | Project Symbols                |
| `⌘ N` · `P` | Project Search (find in files) |
| `⌘ N` · `C` | Command Palette                |
| `⌘ N` · `D` | Diagnostics Panel              |

---

### ⌘ R — Refactor

Code transformations.

| Keys          | Action                        | Context |
| ------------- | ----------------------------- | ------- |
| `⌘ R` · `R`   | Rename Symbol                 | Editor  |
| `⌘ R` · `F`   | Format Document               | Editor  |
| `⌘ R` · `I`   | Organize Imports              | Editor  |
| `⌘ R` · `A`   | Code Actions (quick fix menu) | Editor  |
| `⌘ R` · `C`   | Show Completions              | Editor  |
| `⌘ R` · `⌘ C` | Show Word Completions         | Editor  |
| `⌘ R` · `H`   | Show Signature Help           | Editor  |

---

### ⌘ L — Line

Line and selection manipulation.

| Keys        | Action              | Notes                         |
| ----------- | ------------------- | ----------------------------- |
| `⌥ ↑`       | Move Line Up        | Direct alias, same as default |
| `⌥ ↓`       | Move Line Down      | Direct alias, same as default |
| `⌘ L` · `D` | Duplicate Line Down |                               |
| `⌘ L` · `X` | Delete Line         |                               |
| `⌘ L` · `J` | Join Lines          |                               |
| `⌘ L` · `C` | Toggle Line Comment |                               |
| `⌘ L` · `A` | New Line Above      | Stays in current line         |
| `⌘ L` · `B` | New Line Below      | Stays in current line         |

> `⌥` is `Alt` on Windows and Linux.

---

### ⌘ B — Block / Selection

Syntax-aware selection, multi-cursor, and folding.

**Selection & Multi-cursor**

| Keys        | Action                                 |
| ----------- | -------------------------------------- |
| `⌘ B` · `E` | Expand Selection (larger syntax node)  |
| `⌘ B` · `S` | Shrink Selection (smaller syntax node) |
| `⌘ B` · `J` | Move Cursor to Matching Bracket        |
| `⌘ B` · `N` | Select Next Occurrence (add)           |
| `⌘ B` · `P` | Skip Occurrence, Select Next           |
| `⌘ B` · `A` | Select All Occurrences                 |
| `⌘ B` · `C` | Add Cursor Above                       |
| `⌘ B` · `V` | Add Cursor Below                       |

**Folding**

| Keys                | Action           |
| ------------------- | ---------------- |
| `⌘ B` · `F`         | Toggle Fold      |
| `⌘ B` · `[`         | Fold Recursive   |
| `⌘ B` · `]`         | Unfold Recursive |
| `⌘ B` · `⌘ F` · `A` | Fold All         |
| `⌘ B` · `⌘ F` · `U` | Unfold All       |
| `⌘ B` · `⌘ F` · `1` | Fold to Level 1  |
| `⌘ B` · `⌘ F` · `2` | Fold to Level 2  |
| `⌘ B` · `⌘ F` · `3` | Fold to Level 3  |
| `⌘ B` · `⌘ F` · `4` | Fold to Level 4  |
| `⌘ B` · `⌘ F` · `5` | Fold to Level 5  |
| `⌘ B` · `⌘ F` · `6` | Fold to Level 6  |
| `⌘ B` · `⌘ F` · `7` | Fold to Level 7  |
| `⌘ B` · `⌘ F` · `8` | Fold to Level 8  |
| `⌘ B` · `⌘ F` · `9` | Fold to Level 9  |

---

### ⌘ F — Find

Buffer search, match navigation, and project search.

**Buffer Search**

| Keys        | Action                          |
| ----------- | ------------------------------- |
| `⌘ F` · `F` | Open Search Bar (focused)       |
| `⌘ F` · `R` | Open Replace Bar                |
| `⌘ F` · `N` | Next Match                      |
| `⌘ F` · `P` | Previous Match                  |
| `⌘ F` · `A` | Select All Matches              |
| `⌘ F` · `T` | Toggle Replace                  |
| `⌘ F` · `S` | Toggle Search Within Selection  |
| `⌘ F` · `O` | Outline Picker (symbol in file) |

**Search Modifiers**

| Keys        | Action                |
| ----------- | --------------------- |
| `⌘ F` · `C` | Toggle Case Sensitive |
| `⌘ F` · `W` | Toggle Whole Word     |
| `⌘ F` · `X` | Toggle Regex          |

**Project Search**

| Keys        | Action                         |
| ----------- | ------------------------------ |
| `⌘ F` · `/` | Project Search (find in files) |
| `⌘ F` · `I` | Toggle Project Search Filters  |

---

### ⌘ E — Editor

Pane splits, pane swapping, pane focus, tab navigation, and preview.

**Splits** (arrow key = split in that direction)

| Keys        | Action      |
| ----------- | ----------- |
| `⌘ E` · `→` | Split Right |
| `⌘ E` · `↓` | Split Down  |
| `⌘ E` · `←` | Split Left  |
| `⌘ E` · `↑` | Split Up    |

**Pane Focus** (⌘ + arrow = focus in that direction)

| Keys          | Action           |
| ------------- | ---------------- |
| `⌘ E` · `⌘ →` | Focus Pane Right |
| `⌘ E` · `⌘ ↓` | Focus Pane Below |
| `⌘ E` · `⌘ ←` | Focus Pane Left  |
| `⌘ E` · `⌘ ↑` | Focus Pane Above |

**Pane Swap** (vim-style hjkl)

| Keys        | Action          |
| ----------- | --------------- |
| `⌘ E` · `L` | Swap Pane Right |
| `⌘ E` · `J` | Swap Pane Down  |
| `⌘ E` · `H` | Swap Pane Left  |
| `⌘ E` · `K` | Swap Pane Up    |

**Tabs**

| Keys        | Action          |
| ----------- | --------------- |
| `⌘ E` · `N` | Next Tab        |
| `⌘ E` · `B` | Previous Tab    |
| `⌘ E` · `P` | Pin / Unpin Tab |

**Markdown Preview** (editor must contain a Markdown file)

| Keys          | Action                        |
| ------------- | ----------------------------- |
| `⌘ E` · `M`   | Markdown Preview (inline)     |
| `⌘ E` · `⌘ M` | Markdown Preview (to the side)|

---

### ⌘ W — Window

Panel and dock toggles, recent and remote projects.

**Panels**

| Keys        | Action                   |
| ----------- | ------------------------ |
| `⌘ W` · `E` | Project Panel (Explorer) |
| `⌘ W` · `O` | Outline Panel            |
| `⌘ W` · `G` | Git Panel                |
| `⌘ W` · `D` | Debug Panel              |
| `⌘ W` · `T` | Terminal                 |
| `⌘ W` · `A` | AI Agent Panel           |
| `⌘ W` · `M` | Diagnostics (Messages)   |

**Docks** (vim-style hjkl)

| Keys        | Action             |
| ----------- | ------------------ |
| `⌘ W` · `H` | Toggle Left Dock   |
| `⌘ W` · `J` | Toggle Bottom Dock |
| `⌘ W` · `L` | Toggle Right Dock  |
| `⌘ W` · `0` | Toggle All Docks   |

**Projects**

| Keys          | Action                                     |
| ------------- | ------------------------------------------ |
| `⌘ W` · `R`   | Open Recent Project (current window)       |
| `⌘ W` · `⌘ R` | Open Recent Project (new window)           |
| `⌘ W` · `C`   | Connect to Remote Project (current window) |
| `⌘ W` · `⌘ C` | Connect to Remote Project (new window)     |

**Close**

| Keys        | Action                                           | Notes                                                                                   |
| ----------- | ------------------------------------------------ | --------------------------------------------------------------------------------------- |
| `⌘ W` · `X` | Close Active Tab (unpinned) or Close Active Dock | Closes tab when a pane is focused, closes dock otherwise. Pinned tabs are not affected. |

---

## Disabled Defaults

These built-in shortcuts have been intentionally removed to prevent accidental use. Their replacements are listed.

| Disabled Key | Was                              | Replacement |
| ------------ | -------------------------------- | ----------- |
| `⌘ B`        | Toggles Left Dock                | `⌘ W` · `H` |
| `⌘ F`        | Open search bar / project search | `⌘ F` · `F` |
| `⌘ R`        | Toggle Right Dock                | `⌘ W` · `L` |
| `⌘ W`        | Close tab / close dock           | `⌘ W` · `X` |
