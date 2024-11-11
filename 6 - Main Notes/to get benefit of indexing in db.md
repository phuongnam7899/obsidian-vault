2024-11-11 11:59

Tags: [[Database]] 

---

- If the index is "field1 field2 field3"
- If query WHERE by "field1" or "field1 field2" or "field2 field1" => still get benefit
- If query by "field2" or "field3" -> not get benefit
=> Must ==contain the fields in order of index==, but the ==order of field in query is not important==

---
# References