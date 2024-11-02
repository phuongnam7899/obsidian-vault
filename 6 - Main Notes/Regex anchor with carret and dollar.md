2024-10-30 21:58

Tags: [[Regex]]

---

### Start anchor
- `^`:
	- Inside the `[]` => Negation
	- Outside the `[]` => Start of line
- `^foo.*`:
	- ==foo==bar: :LiCheck:
	- ==foo==baz: :LiCheck:
	- bazfoo: :LiCircleX:
### End anchor
- `$`: mark the end of line
- `*.bar$`:
	- foo==bar==: :LiCheck:
	- baz==bar==: :LiCheck:
	- barfoo: :LiCircleX:

---
# References