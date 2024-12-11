2024-11-02 15:10

Tags: [[ReactJS]] [[3 - Tags/Design Pattern]]

---

# What is Compound Component?

-   Components pattern allows writing a declarative and flexible API for complex components
-   Using multiple loosely coupled child components.
-   Each of them performs a different task

# Why use?

-   Component API is declarative.
-   Child components are loosely coupled ⇒ Easy to reorder, add and remove the child component without effect on others.

# Example (Arcodion component)

## Old approach

Using React.Children.map and cloneElement

### Accordion.tsx

Share all states for children

```tsx
import { Children, cloneElement, ReactNode, useState } from "react";

function Accordion({ children }: { children: ReactNode }) {
  const [openItem, setOpenItem] = useState(null);

  return (
    <div>
      {Children.map(children, (child: any) =>
        cloneElement(child, { openItem, setOpenItem })
      )}
    </div>
  );
}
```

### AccordionItem.tsx

```tsx
export const AccordionItem = ({
  children,
  openItem,
  setOpenItem,
  id
}: {
  children: ReactNode;
  openItem?: string;
  setOpenItem?: any;
  id: string;
}) => {
  return (
    <div>
      {Children.map(children, (child: any) =>
        cloneElement(child, { openItem, setOpenItem, id })
      )}
    </div>
  );
};
```

### AccordionHeader.tsx

```tsx
export const AccordionHeader = ({
  setOpenItem,
  id,
  children
}: {
  setOpenItem?: any;
  id?: string;
  children: ReactNode;
}) => {
  return (
    <div onClick={() => setOpenItem(id)}>
      {children}
    </div>
  );
};
```

### AccordionPanel.tsx

```tsx
export const AccordionPanel = ({
  children,
  openItem,
  id
}: {
  children: ReactNode;
  openItem?: string;
  id?: string;
}) => {
  return (
    <div
      padding={openItem === id ? "16px" : "0px"}
      height={openItem === id ? "fit-content" : "0px"}
    >
      {children}
    </div>
  );
};
```

## New approach

Using react hook: useContext, useMemo

### Accordion.tsx

Share all states for children

```tsx
import {
  Children,
  cloneElement,
  Context,
  createContext,
  ReactNode,
  useContext,
  useMemo,
  useState
} from "react";

const AccordionContext: Context<{
  openItem: string;
  setOpenItem: any;
}> = createContext({
  openItem: "",
  setOpenItem: null
});

function Accordion({ children }: { children: ReactNode }) {
  const [openItem, setOpenItem] = useState("");

  const value = useMemo(() => ({ openItem, setOpenItem }), [openItem]);

  return (
    <div>
      <AccordionContext.Provider value={value}>
        {children}
      </AccordionContext.Provider>
    </div>
  );
}
```

### AccordionItem.tsx

```tsx
export const AccordionItem = ({
  children,
  id
}: {
  children: ReactNode;
  id: string;
}) => {
  return (
    <div>
      {Children.map(children, (child: any) => cloneElement(child, { id }))}
    </div>
  );
};
```

### AccordionHeader.tsx

```tsx
const useAccordionContext = () => useContext(AccordionContext);
export const AccordionHeader = ({
  id,
  children
}: {
  id?: string;
  children: ReactNode;
}) => {
  const { setOpenItem } = useAccordionContext();
  return (
    <div onClick={() => setOpenItem(id)}>
      {children}
    </div>
  );
};
```

### AccordionPanel.tsx

```tsx
const useAccordionContext = () => useContext(AccordionContext);

export const AccordionPanel = ({
  children,
  id
}: {
  children: ReactNode;
  id?: string;
}) => {
  const { openItem } = useAccordionContext();
  return (
    <div
      padding={openItem === id ? "16px" : "0px"}
      height={openItem === id ? "fit-content" : "2px"}
    >
      {children}
    </div>
  );
};
```


---
# References