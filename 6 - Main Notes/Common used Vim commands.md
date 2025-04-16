2025-01-15 16:58

Tags: [[Vim]]  

---


# Mode change
- Normal Mode: `ESC`
- Insert Mode:
	- Insert before: `i`
	- Insert after: `a`
	- Insert in new line: `o`
- Visual Mode (For marking text)
	- Start visual mode: `v`
# Motion (Cursor movement)


> [!i] Common language
> - i: inner of...
> - a: inner of ... (include itself)
> - f: forward to next ...
> - F: back to previous...

- Single
	- Left: `h`
	- Right: `l`
	- Up: `k`
	- Down: `j`
## Horizontal
- Word:
	- Start of next word: `w`
	- Next end of word: `e`
	- Backward to start: `b`
- In Line:
	- Start of line: `^`
	- End of line: `$`
## Vertical
- Block:
	- Move to next paragraph: `}`
	- Move to previous paragraph: `{`
- `%`: matching start/end `{`, `[`, `(`
## Global
- File:
	- Go to local declaration: `gd`
	- Go to pattern: `/pattern` -> `Enter` ->
		- `n`: next
		- `N`: previous
		- Remove all highlight: `nohlseach`
	- Move to line number X: `Xgg`
	- Move screen down 1/2 page: `Ctrl+d`
	- Move screen up 1/2 page: `Ctrl+u`
	- Center cursor on screen: `zz`
- Workspace:
	- Go to global declaration: `gD`

# Actions
- Change (Replace until end of ...): `c` + `...` 
- Undo: `u`
- Redo: `Ctrl+r`
- Delete/cut: `d` + ...
	- Line: `dd`
- Find and replace: `:%s/old/new/g` (`:%s/old/new/gc` if want have confirmation)
- Yank (copy): `y` + ...
- Paste: 
	- After cursor: `p`
	- Before cursor: `P`
- Append to next new line: `o`


| Actions (Verbs)   | Selectors (Modifiers) | Objects (Nouns)            |
| ----------------- | --------------------- | -------------------------- |
| d - delete        | i - inner             | w - word                   |
| c - change        | a - around/including  | s - sentence               |
| y - yank (copy)   | t - till (up to)      | p - paragraph              |
| v - visual select | f - find forward      | b - block/parentheses ()   |
| p - paste         | F - find backward     | B - block/braces {}        |
| r - replace       | $ - end of line       | [ - square brackets []     |
| x - delete char   | 0 - start of line     | ' - single quotes          |
| s - substitute    | / - search forward    | " - double quotes          |
| g - go            | ? - search backward   | t - HTML/XML tag           |
| m - mark          | n - next match        | W - WORD (space separated) |

---
# References