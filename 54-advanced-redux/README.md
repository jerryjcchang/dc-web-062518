# Advanced Redux

- review thunks and dispatch
- see the power of getState in a thunk
- add more functionality to our application
- check out some advanced functionality (optional)

## TODO
- X show galleries from list of galleries
- X highlight selected painting
- X Unknown gallery instead of empty chiclet
- X show spinner when loading paintings


- X make delete button work
Deletion should be persisted

1 DELETE request to backend - deletes the painting
2 PATCH request to mark as deleted (`painting.deleted = true`)

- votes / likes

1 Display on the paintingshow component
2 button on the paintingshow component
3 action for that button to dispatch
4 maybe a new reducer? update to an existing reducer?

X Display the likes
X Update in place, rather than painting jump
X Show that a painting has been deleted

- add create / edit painting form
- search bar for paintings
- show trash bin of paintings deleted

## Questions
- router and redux
- auth

## Thunks and Spinners

We frequently want to show loading and error states on our components
Thunk lets us dispatch loading and error actions around our promises to make this easier

```js
function getData() {
  // thunk action!
  return function(dispatch) {
    dispatch({type: 'LOADING'})
    fetch('url_for_data')
      .then(
        res => res.json()
      ).then(data =>
        dispatch({ type: 'LOADED', data })
      ).catch(err =>
        dispatch({type: 'ERROR', err });
      )
  }
}
```

## Review and Questions

- where is the store state actually living?
  in the store

- how should we organize our folders / files?
  - redux folder, components folder
  - once reducers get big enough, put them in their own files
  - can use combineReducers at multiple levels

- What's the flow at this point?
- Order of tasks as a developer
  - Build vertically!
  - One user story at a time
- How do we think in redux?


- where should ids get created? (in the action or in the reducer (or neither?))
  - action > reducer
  - database best
  - except if you want both a client side cuid and a unique id in the database
    - for instance, if you wanted to line up some objects created in offline mode

- when should we setState, now that we're using redux?
  - when to create a local state vs. add the state to redux?
  - if it _doesn't_ affect anything else, local state is okay
  - redux is always safe, but more boilerplate to write

- when should we pass props vs. when should we connect to redux?
  - generally, pull from the store
  - except when mapping
  - or when you want to reuse a component differently in different places

## Advanced Concepts
- Selectors and `reselect`
- ImmutableJS
- Middlewares
- Redux and React Router
- Redux and Auth
- Sagas, Observables
