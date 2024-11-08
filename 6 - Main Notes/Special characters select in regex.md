2024-11-05 21:46

Tags: [[Regex]] 

---

- With characters that have special meaning (`^&*.[]()\`), need to escape using `\` before
- `\.boo`: 
	- ==.==boo: o
	- bboo: x
- ==Note==: If special  char is inside the `[]` => ==no need== to be escaped (==except== `^` and `-` cause they have special meaning in `[]`)
- `[.#$\^]boo`:
	- ==.==boo: o
	- ==#==boo: o
	- ==^==booo: o
	- dboo: x

---
# References