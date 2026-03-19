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
| `⌘ N`  | **N**avigate | File finder, project symbols, search, recent        |
| `⌘ R`  | **R**efactor | Rename, format, imports, code actions, tasks        |
| `⌘ L`  | **L**ine     | Move, duplicate, delete, join, comment              |
| `⌘ E`  | **E**ditor   | Splits, tabs, pane focus, search bar                |
| `⌘ W`  | **W**indow   | Panel and dock toggles, close tab/dock              |
| `⌘ F`  | **F**old     | Fold, unfold, fold by level                         |
| `⌘ B`  | **B**lock    | Selection expansion, multi-cursor                   |

---

### Debugging — F-key Layout

No prefix.

| Key    | Action                            | Notes                                                        |
| ------ | --------------------------------- | ------------------------------------------------------------ |
| `F4`   | Spawn Task                        | Choose from a list                                           |
| `⇧F4`  | Rerun last task                   |                                                              |
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
| `⌘ N` · `R` | Recent Projects                |
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

> `⌥` is `Alt` in Windows and Linux.

---

### ⌘ B — Block / Selection

Syntax-aware selection and multi-cursor.

| Keys        | Action                                    |
| ----------- | ----------------------------------------- |
| `⌘ B` · `E` | Expand Selection (larger syntax node)     |
| `⌘ B` · `S` | Shrink Selection (smaller syntax node)    |
| `⌘ B` · `J` | Moves cursor position to Matching Bracket |
| `⌘ B` · `N` | Select Next Occurrence (add)              |
| `⌘ B` · `P` | Skip Occurrence, Select Next              |
| `⌘ B` · `A` | Select All Occurrences                    |
| `⌘ B` · `C` | Add Cursor Above                          |
| `⌘ B` · `V` | Add Cursor Below                          |

---

### ⌘ F — Fold

All code folding operations.

| Keys        | Action                    |
| ----------- | ------------------------- |
| `⌘ F` · `F` | Toggle Fold at Cursor     |
| `⌘ F` · `A` | Fold All                  |
| `⌘ F` · `U` | Unfold All                |
| `⌘ F` · `R` | Fold Recursive            |
| `⌘ F` · `E` | Unfold / Expand at Cursor |
| `⌘ F` · `1` | Fold to Level 1           |
| `⌘ F` · `2` | Fold to Level 2           |
| `⌘ F` · `3` | Fold to Level 3           |
| `⌘ F` · `4` | Fold to Level 4           |
| `⌘ F` · `5` | Fold to Level 5           |

---

### ⌘ E — Editor

Pane splits, tab navigation, and in-buffer search.

**Search**

| Keys        | Action                              |
| ----------- | ----------------------------------- |
| `⌘ E` · `S` | Open Search Bar (focused)           |
| `⌘ E` · `R` | Open Search / Replace Bar (focused) |

**Splits**

| Keys        | Action      |
| ----------- | ----------- |
| `⌘ E` · `→` | Split Right |
| `⌘ E` · `↓` | Split Down  |
| `⌘ E` · `←` | Split Left  |
| `⌘ E` · `↑` | Split Up    |

**Pane Focus** (vim-style hjkl)

| Keys        | Action           |
| ----------- | ---------------- |
| `⌘ E` · `H` | Focus Pane Left  |
| `⌘ E` · `J` | Focus Pane Below |
| `⌘ E` · `K` | Focus Pane Above |
| `⌘ E` · `L` | Focus Pane Right |

**Tabs**

| Keys        | Action          |
| ----------- | --------------- |
| `⌘ E` · `N` | Next Tab        |
| `⌘ E` · `B` | Previous Tab    |
| `⌘ E` · `P` | Pin / Unpin Tab |

---

### ⌘ W — Window

Panel and dock toggles.

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

**Docks**

| Keys        | Action             |
| ----------- | ------------------ |
| `⌘ W` · `←` | Toggle Left Dock   |
| `⌘ W` · `→` | Toggle Right Dock  |
| `⌘ W` · `↓` | Toggle Bottom Dock |
| `⌘ W` · `0` | Toggle All Docks   |

**Close**

| Keys        | Action                                           | Notes                                                                                   |
| ----------- | ------------------------------------------------ | --------------------------------------------------------------------------------------- |
| `⌘ W` · `X` | Close Active Tab (unpinned) or Close Active Dock | Closes tab when a pane is focused, closes dock otherwise. Pinned tabs are not affected. |

---

## Disabled Defaults

These built-in shortcuts have been intentionally removed to prevent accidental use. Their replacements are listed.

| Disabled Key | Was                              | Replacement |
| ------------ | -------------------------------- | ----------- |
| `⌘ B`        | Toggles Left Dock                | `⌘ W` · `←` |
| `⌘ F`        | Open search bar / project search | `⌘ E` · `S` |
| `⌘ R`        | Toggle Right Dock                | `⌘ W` · `→` |
| `⌘ W`        | Close tab / close dock           | `⌘ W` · `X` |
