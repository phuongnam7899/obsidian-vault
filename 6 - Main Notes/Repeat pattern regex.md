2024-11-03 09:25

Tags: [[Regex]] 

---

Using curly bracket `{}`
### Specific number
- `{x}`: with `x` is a number of times to repeat (repeat the previous express)
- `^[0-9]{3}`:
	- ==123==: o
	- ==345==: o
	- 12: x
	- 1234: x
### Range
- `{x,y}`: repeat at least `x` times and most `y` times
- `[a-z]{1-3}`:
	- ==ab==: o
	- ==a==: o
	- ==abc==: o
	- abcd: x
- `{x,}` : repeate min `x` time
- `{,x}` : repeate max `x` time

---
# References