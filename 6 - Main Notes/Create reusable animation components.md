2024-11-03 09:23

Tags: [[ReactJS]] [[Animation]] 

---


### Basic usage of GSAP

```jsx
import React, { useEffect, useRef } from "react";
import { gsap } from "gsap";

function App() {
  const myHeader = useRef(null);
  useEffect(() => {
    gsap.to(myHeader.current, {
      opacity: 0,
      duration: 2,
    });
  }, []);
  return <h1 ref={myHeader}>Using gsap.to() method</h1>;
}
```

### Create reusable components

**FadeIn.js**

```jsx
const FadeIn = ({
  children,
  direction = null,
  duration = 1,
  distance = 200,
}) => {
  let componentRef = useRef(null);
  let fadeDirection;
  switch (direction) {
    case "left":
      fadeDirection = { x: distance };
      break;
    case "right":
      fadeDirection = { x: -distance };
      break;
    case "up":
      fadeDirection = { y: distance };
      break;
    case "down":
      fadeDirection = { y: -distance };
      break;
    default:
      fadeDirection = { x: 0 };
  }
  useEffect(() => {
    gsap.from(componentRef.current, {
      duration,
      opacity: 0,
      ...fadeDirection,
    });
  }, [duration, fadeDirection]);
  return <div ref={componentRef}>{children}</div>;
};
```

**Usage**

```jsx
<FadeIn direction="left">
  <h1> Hello World!</h1>
</FadeIn>
```


---
# References