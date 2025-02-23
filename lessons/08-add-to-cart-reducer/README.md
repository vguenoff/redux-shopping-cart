## Building a Reducer Method to add an Item to the Shopping Cart

Reducer methods in RTK's `createSlice` method take two arguments. The `state`
and an action of type
[PayloadAction](https://redux.js.org/usage/usage-with-typescript#application-usage).
`PayloadAction` is a generic type that requires you to pass in the specific type
of the payload you are expecting. In our case it's going to be
`PayloadAction<string>`.

One thing that's really impressive about RTK is that it builds its reducers
using [immer](https://github.com/immerjs/immer). Immer allows you to deal with
immutable data in a seemingly mutable way. While it appears that we're directly
modifying our cart state here, if you hover the `state` variable in your IDE
you'll see it's actually of type `WritableDraft<CartState>`, which means it's a
draft of your state. Any changes made there will captured by immer and converted
into a single new state object that will replace your current one after your
redux method is done running. It's pretty clever and much easier to write than
the old redux way of having to make long copies of everything to avoid mutating
the redux state directly!
