2024-11-02 14:11

Tags: [[Regex]]

---

### Specific character

#### Include
- `[abc]`: One of characters inside `[]` (this case is `a`, `b` or `c`):
- `[bsr]at`:
	- ==b==at: o
	- ==s==at: o
	- ==r==at: o
	- cat: x
	- nat: x
#### Exclude
- `[^abc]`: Except the following characters inside `[]`
- `[^ab]at`:
	- bat: x
	- aat: x
	- ==c==at: o
	- ==n==at: o
### Character in range
- `[a-d]` : One of characters in range given in `[]` (this case is <->`[abcd]`) (start char [[ASCII]] value mus < end har [[ASCII]] value)
- `[a-d]x`: like above but accept more `x` character (`[a-d]` || `[x]`)
- `[a-cz]boo`:
	- ==a==boo: o
	- ==b==boo: o
	- ==c==boo: o
	- ==z==boo: o
	- eboo: x
- `[a-cA-cx]`: Similar, `[a-c]` || `[A-C]` || `[x]`

---
# References