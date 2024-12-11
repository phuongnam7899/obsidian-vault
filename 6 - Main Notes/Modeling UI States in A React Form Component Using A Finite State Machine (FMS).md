2024-11-08 17:00

Tags: [[3 - Tags/Design Pattern]] [[ReactJS]] 

---

# What is FMS

-   Design pattern ****that allows us to model a large system as a collection of loosely coupled components
-   Each component in the system changes its behavior when the internal state changes.
-   Consists of states and state transitions
-   Has finite states and state transition
-   Example: Traffic light
    -   States:
        -   Light switch: 2 states: ON & OFF
        -   Traffic light: 3 state: RED, YELLOW, GREEN
    -   State transition:
        -   Change color after a time base on current color

# Simple Case

-   Original

```jsx
import React, { useState } from "react";

function FriendStatus(props) {
  const [isOnline, setIsOnline] = useState(null);

  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }
    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    // Specify how to clean up after this effect:
    return function cleanup() {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });

  if (isOnline === null) {
    return "Loading...";
  }
  return isOnline ? "Online" : "Offline";
}
```

-   FMS

```jsx
import React, { useState } from "react";

const UiState = {
  LOADING: "LOADING",
  ONLINE: "ONLINE",
  OFFLINE: "OFFLINE",
};

const UiStateMessageMap = {
  [UiState.LOADING]: "Loading...",
  [UiState.ONLINE]: "Online",
  [UiState.OFFLINE]: "Offline",
};

const getUiState = (status) => {
  const { isOnline } = status;
  if (isOnline === null) return UiState.LOADING;
  return isOnline ? UiState.ONLINE : UiState.OFFLINE
};

function FriendStatus(props) {
  const [uiState, setUiState] = useState(UiState.LOADING); // init state

  useEffect(() => {
    function handleStatusChange(status) {
      const nextUiState = getUiState(status);
      setUiState(nextUiState);
    }
    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    // Specify how to clean up after this effect:
    return function cleanup() {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });

  return UiStateMessageMap[uiState];
}
```

⇒ For simple components with only some state, FMS may be overkill

# Complex case
![[Pasted image 20241108170107.png]]
-   State describe (split up component into sub-systems):
    
    -   In SUCCESS status for all ERROR state, feedback message display
    -   In SUCCESS, DISAMBIGUATION, and all ERROR states, show icon next to input
    -   In all states except LOADING, inputs are enable
-   Delegate the rendering logic

| Component       | What to render                                                                                             | Value depends on                                        | Affected by UI |
| ----------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------- | -------------- |
| Countries   | Dropdown menu containing countries retrieved from the server                                               | Found location & User input                             | LOADING |
| QueryInput  | Input field containing the country/city name or zip code & Checkmark or exclamation mark icon for feedback | Found location & User input                             |    LOADING, SUCCESS, All Error states            |
| Feedback    | Success message containing location name                                                                   | Found location & Static messages mapped to error states |         SUCCESS, All Error states       |
| Suggestions | Dropdown menu containing matched locations                                                                 | Matched locations from the server                       |    DISAMBIGUATION            |
|             |                                                                                                            |                                                         |                |


---
# References