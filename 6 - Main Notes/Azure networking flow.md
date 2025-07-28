2025-07-15 14:46

Tags: 

---

1. VTI understanding about requirement
- At some periods of time, when user access the application URL, you want them to see maintenance page instead of the normal page
- The downtime of the redirection should be zero
2. Problem
- As we investigated, Azure deployment slots acts as separate instances of the app services, which we are using to run our BE application. It could help with zero downtime redirection for the BE app, but when user access the application URL, before reaching the BE, what they actually reach first is the FE app, which is stored in the Azure Storage. So we think that the Azure deployment slots might not help much in this case (Please help to correct if there's any thing that I misunderstood)
3. Suggested solution
- Our suggestion is redirecting the user when they hit the FE app by create another static site in the Azure Storage for the maintenance page, then when we want user to see the maintenance page, we just need to update the application gateway to redirect user to that page instead of normal page (it could be done manually, but I believe we can prepare script to execute faster)
4. Other points
- Is the design for the maintenance page ready now? If not, will our team our or another team need to prepare it?


---
# References