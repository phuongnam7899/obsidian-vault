2025-01-15 16:58

Tags: [[Vim]]  

---

> [!i] Common language
> - w: start of next word
> - iw: whole word
> - aw: word + space after it 
> - d: delete/cut
> - y: copy (yank)

# Mode change
- Normal Mode: `ESC`
- Insert Mode:
	- Insert before: `i`
	- Insert after: `a`
	- Insert in new line: `o`
- Visual Mode (For marking text)
	- Start visual mode: `v`
# Cursor movement
- Single
	- Left: `h`
	- Right: `l`
	- Up: `k`
	- Down: `j`
- Word:
	- Start of next word: `w`
	- Next end of word: `e`
	- Backward to start: `b`
- Line:
	- Start of line: `^`
	- End of line: `$`
- File:
	- Go to local declaration: `gd`
	- Go to pattern: `/pattern` -> `Enter` ->
		- `n`: next
		- `N`: previous
- Workspace:
	- Go to global declaration: `gD`
# Edit
- Replace until end of word: `cw`
- Undo: `u`
- Redo: `Ctrl+r`
- Delete/cut:
	- To the start of next word: `dw`
	- Whole word: `diw`
	- Line: `dd`
- Find and replace: `:%s/old/new/g` (`:%s/old/new/gc` if want have confirmation)
- Paste: 
	- After cursor: `p`
	- Before cursor: `P`
# Marking text
- Block:
	- Marking outer block of `{}`, `()`: `a{` or `a(`
	- Marking block of tag `<>`: `at`
- Inner block: same as block but use `i` instead of `a`
---
# References