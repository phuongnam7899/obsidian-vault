2024-11-08 17:30

Tags: [[Clean Code]]

---

Include ==redundant information== (the info that can be guess too easily) in name: productWithNameAnDate, personUser,...
- Using: 
	- ==Slang==: user.goToHell() => user.remove(), user.shutUp() => user.mute()
	- ==Unclear abbreviation==: val => value, validation
	- ==Disinformation==: userList = {...} => userList = [...]; allProducts = products.filter(...) => outDatedProducts = products.filter(...)
- Choose names that ==look similar== (=> hard to choose when need): getDailyData, getDayData, getDataOfDay,...
- ==Inconsistent==: 
	- buildHouse, getHome => buildHome, getHome
	- getProducts, fetchUser, retrieveUser, fetchProduct, getCourse => choose one

---
# References