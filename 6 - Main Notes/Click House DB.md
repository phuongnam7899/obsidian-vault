2025-01-12 15:56

Tags: [[Database]] [[OLAP]] [[ClickHouse]]

---

- Is an OLAP (Online Analytical Processing) database
- Is a Columnar Storage DB
- Better for applications that need to ==perform calculations based on columns==
- Supports ==indexing and partitioning==
- ==Compresses data==: Stores compressed data -> reduces I/O disk -> increases processing speed

## How does ClickHouse compress data?

2 steps:

- Encode data: Techniques like Delta Encoding or Dictionary Encoding will be used based on the data type -> Reduces complexity and storage usage
- Compress data: Apply compression algorithms to the encoded data

---

# References

- [[What is columnar storage]]
- [[What is Dictionary Encoding]]
- [[What is Delta Encoding]]
