2024-12-31 13:32

Tags: [[Frontend Optimization]]

---

![[Pasted image 20241231133358.png]]

# Technique 1: Caching

> [!w] This technique might be put in Strategy #1 because, at its deepest, caching is reducing the distance. But the idea of caching = faster is easier to remember, like the Pythagorean theorem, no need to prove it again to use. So let it be here

- Caching is fast, but the downsides are:
  - Inconsistency if the data updated regularly
  - Limited amount of data to be stored (mostly because of the cost)
- => Only use it for data that is regularly used and less updated
- There are some [[Browser cache types]] that can be used

# Technique 2: Multi Thread

- JavaScript is single-thread (called the main thread)
- Everything that runs synchronously will block the main thread -> users cannot interact with the UI
- Here's web workers come to help processing the heavy calculation tasks in independent threads
  ![[Pasted image 20241231134926.png]]
- [[Communication between web worker and main thread]]
- [[how to use web worker]]

---

# References

- [[Reduce wait time to increase FE performance]]
