# React + Fetch Code Along

Getting set up:
1. Create react app: `npx create-react-app react-fetch-code-along`
2. Navigate into project directory: `cd fetch-react-code-along`
3. Start app: `npm start`

**Note**: To simplify matters in this lab, everything will be done in `App.js`.

Tasks
- Enter the following API URL in your Chrome browser and explore the data: http://carparks-sg.herokuapp.com/api
  - You can install the [JSON Viewer chrome extension](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh) to prettify the JSON response
- Delete everything inside `App.js`, and create a class component named `App`
- In `App.js`, define a function named `componentDidMount()`, and inside it, make a fetch request and console.log the response
```js
componentDidMount() {
  const response = fetch("http://carparks-sg.herokuapp.com/api")
  console.log(response)
}
```

- In `App.js`, make `componentDidMount()` an `async` method. `console.log` the `response` to see what it is

```js
async componentDidMount() {
  const response = await fetch("http://carparks-sg.herokuapp.com/api")
  console.log(response)
}
```

- In `App.js`, extract the data from the response by calling `await response.json()`. `console.log` `data` to see what it is.

```js
async componentDidMount() {
  const response = await fetch("http://carparks-sg.herokuapp.com/api")
  const data = await response.json();
  console.log(data)
}
```

- In `App.js`, do 2 things:
  - First, initialize a state object with the following properties 
  ```js
  class App extends Component {
    constructor() {
      super();
      this.state = {
        carparks: []
      };
    }
  ```
  - Second, in `componentDidMount()`, call `this.setState()` to update the `carparks` field with the array that is stored in `data`

  ```js
  async componentDidMount() {
    const response = await fetch("http://carparks-sg.herokuapp.com/api")
    const data = await response.json();
    this.setState({
      carparks: data
    })
  }
  ```