# Redux (Predictable state container)

## Data Flow
Redux uses strict unidirectional data flow as 
> `(1)Actions -> (2)Reducers -> (3)Store -> (4)View -> (1)Actions`

## Store and its helper methods
A store object holds application state and has methods to manipulate application state.
- `getState` : gives current state
- `dispatch` : takes action to call reducer and update state
- `subscribe`: binds listener to store changes
- `replaceReducer`: used to handle hot-reloading and code-splitting

## Creating store
createStore is used to create a store which connects reducers, initial application state and optional middleware.

```
import { createStore, applyMiddleware } from 'redux';
import Reducers from 'path/to/combinedReducer';

import middleware1 from 'your-middleware';
import middleware2 from 'path/to/your-custom-middleware';

const initialApplicationState = <your_initial_application_state>;
const appliedMiddleware = applyMiddleWare(middleWare1, middleware2, ...);

createStore(Reducers, initialApplicationState = {}, appliedMiddleware);
```

## Middleware 
A middleware is intermediary between actions and reducer. It takes the dispatched action evaluates it so reducer can get proper information and application have more responsible actions.

A middleware`s 
- first method gets store dispatch(wrapped dispatched) and getState helpers.
- second method gets next(actual store.dispatch) and 
- third/final function gets actions.
With help of context we can access all provided arguments and use them under middleware
> `({dispatch, getState}:store) => next: store.dispatch => action => {}`

`Caveat`: Dispatched action via store.dispatch will actually travel the whole middleware chain again, including the current middleware.

## Custom middleware
```
Example:

const customLogger = ({getState, dispatch}) => next => action => {

    console.log(getState());
    dispatch(action); // runs through complete middleware chain again
    console.log(getState());

    console.log('dispatch action ', action);
    const result = next(action);
    console.log('next state', result);
}
```

## combineReducers
`combineReducers` takes different reducer and combine them as a single reducer to use and update single store.

```
Example:

const combineReducer = (Reducers) => {
    return (state = {}, action) => {
        return Object.keys(Reducers).reduce((accumulator, reducer) => {
            accumulator[reducer] = Reducers[reducer]({
                store,
                action
            });
            return accumulator;
        }, {});
    };
}
```

## Provider
To share single application state and avoid passing chained props from one child to another child. we need to use context. To bind context to application and child component a component is required which creates context and makes it available for its children. this is a popular pattern and is provided by react-redux provider.

```
import { Provider } from 'react-redux';
import Store from 'path/to/application-store-created-with-createStore';

<Provider store={Store}>
    {children}
</Provider>
```
*Example of provider implementation and consumption:*
```
import { Component } from 'react';
import PropTypes from 'prop-types';

class Provider extends Component {
    getChildContext () {
        return {
            store: props.store
        }
    }
    return ({children});
}
Provider.childContextTypes = {
    store: PropTypes.Object
}
```

## connect
To consume store without passing it thorough nested components as props we use context.
To use context we need to connect our component to this context and this is where connect method from react-redux comes handy.

```
import { connect } from 'react-redux';

connect(mapStateToProps, mapDispatchToProps)(App);
```
*Example of HOC context implementation:*
```
import PropTypes from 'prop-types';

const connect = (statesProps, actionProps, props) => {
    return (<HOC 
        stateProps={stateProps}
        actionProps={actionProps} 
        {...props}
    >);
};

const HOC = (props, context) => {
    const store = context.store;

    const storeProps = {
        props.storeProps(store, props)
    };

    const actionProps = {
        props.actionProps(store.dispatch)
    };

    return (<Component {...storeProps} {..actionProps} />);
};

HOC.contextType = {
    store: PropTypes.Object
}
```
