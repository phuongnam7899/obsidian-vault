2024-12-31 12:08

Tags: [[Frontend]]

---

```mermaid
flowchart TD
    Start[Browser Performance Optimization] --> Step1[Step 1: Remove Redundant]
    Step1 --> Step2[Step 2: Split to be Lazy]
    Step2 --> Step3[Step 3: Compress]

    subgraph Step1Details[Step 1: Remove Redundant]
        M[Minify Technique]
        T[Tree Shaking]
        I[Remove Redundant Images]
    end

    subgraph Step2Details[Step 2: Split to be Lazy]
        CS[Code Splitting]
        LI[Lazy Loading Images/Videos]
        VR[Virtual Scroll]
        DF[Lazy Data Fetching]
    end

    subgraph Step3Details[Step 3: Compress]
        G[Gzip - More Compatible]
        B[Brotli - More Effective]
    end

    Step1 --> Step1Details
    Step2 --> Step2Details
    Step3 --> Step3Details
```

# Step 1: Remove redundant

- [[Minify technique]] - remove redundant characters
- [[Tree shaking technique]] - eliminate unused code
- [[Remove redundant size of images]]

# Step 2: Split to be lazy

- After the 1st step, we ensure that all code in the bundled file is useful for the application. But the fact is: Users might not want to see and use all things in your app at once
- Analogy: Your app is a restaurant with 100 dishes in the menu, but each customer can only order some of them
- -> Don't make your chef cook all dishes until customers actually order
  ![[Pasted image 20241231131509.png]]
- Solution: only load what and when users need
- Techniques:
  - [[Code Splitting for Lazy Loading Codes]]
  - [[Lazy loading images or videos]]
  - [[Lazy Rendering with Virtual Scroll]]
  - [[Lazy data fetching]]

# Step 3: Compress

- After we ensure all things are needed, we can compress the file to make it even lighter -> reduce the load time (and the bandwidth also)
- You can choose between gzip - compatible with more browsers and brotli - compress more effectively
  ![[Pasted image 20241231133218.png]]

---

# References
