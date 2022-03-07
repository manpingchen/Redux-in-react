# Redux-in-react

A React & Redux project using Redux, Redux ToolKit in React Application. </br>
Store and manage states in the web-wide scale.

```javascript
import { configureStore } from "@reduxjs/toolkit";

import counterReducer from "./counter";
import authReducer from "./auth";

const store = configureStore({
  reducer: { counter: counterReducer, auth: authReducer },
});

export default store;
```

## Feature A: Login Form Auth
<img width="881" alt="Screen Shot 2022-03-07 at 11 49 37 PM" src="https://user-images.githubusercontent.com/10693128/157137766-f4dc88af-a53a-4894-b9f1-613d71ee06b9.png">

#### create user login state in Auth Slice
```javascript
import { createSlice } from "@reduxjs/toolkit";

const initialAuthState = { isAuthenticated: false };

const authSlice = createSlice({
  name: "auth",
  initialState: initialAuthState,
  reducers: {
    login(state) {
      state.isAuthenticated = true;
    },
    logout(state) {
      state.isAuthenticated = false;
    },
  },
});

export const authActions = authSlice.actions;
export default authSlice.reducer;
```

#### manage increment and decrement of Counter in Counter Slice
<img width="966" alt="Screen Shot 2022-03-07 at 11 49 45 PM" src="https://user-images.githubusercontent.com/10693128/157138150-74f2d851-6234-46d7-9990-48dc9e4b2d78.png">

```javascript
import { createSlice } from "@reduxjs/toolkit";

const initialCounterState = { counter: 0, showCounter: true };

const counterSlice = createSlice({
  name: "counter",
  initialState: initialCounterState,
  reducers: {
    increment(state) {
      state.counter++;
    },
    decrement(state) {
      state.counter--;
    },
    increase(state, action) {
      state.counter = state.counter + action.payload;
    },
    toggleHandler(state) {
      state.showCounter = !state.showCounter;
    },
  },
});

export const counterActions = counterSlice.actions;
export default counterSlice.reducer;
```
