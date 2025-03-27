2025-01-12 15:56

Tags: [[Database]]

---

-  Is OLAP (Online Analytical Processing) database
- Is a Columnar Storage DB
- Better for application that need to ==calculate much rely on columns==
- Support ==indexing and partitioning==
- ==Compress data==: Store compressed data -> reduce I/O disk -> increase process speed

## How Click House compress data?
2 steps:
- Encode data: Technique like Delta Encoding or Dictionary encoding will be used based on the data type -> Reduce complexity and storage used
- Compress data: 


---
# References
- [[What is columnar storage]]
- [[What is Dictionary Encoding]]
- What is delta encoding