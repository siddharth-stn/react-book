# React Basics

- # Install React in the Project (CDN and npm)

  - There are three basic kinds of react libraries that are needed
  - They are npm i react react-dom react-router-dom

- # How to create an Element in react?

  - 1. Using the createElement method from react library
       - import React from "react" (/_ it is a default export _/)
       - const Heading = React.createElement("h1", {}, "Hello World!")
       - {} object is used to give attributes
       - eg:- const heading = React.createElement("h1", {id:"something"}, "Hello World!")
       - it is called props object in react

    - # How to create a tree structure of elements in react using createElement method?

      - const Grandfather = React.createElement("div", {id="grandfather"}, React.createElement("div", {id:father}, React.createElement("h1", {id:"child}, "Hello World from Child")))

    - # How to create siblings using createElement method?
      - const Father = React.createElement("div", {id: father}, [React.createElement("h1", {id:"child-one"}, React.createElement("h1", {id: "child-two"}, ))])

  - 2. How to create components/elements using JSX in react?
    - Using functional components, return the jsx elements
    - eg:-
      - const Component = () => {
        - return (
          - <div>
            - <h1> I am a component created using jsx </h1>
          - </div>
        - )
      - }

- # How to create root in react?

  - root is an HTML Element which is used as a root to allow react components to render inside it.
  - root is created by the react-dom library createRoot method.
  - import React DOM from "react-dom/client" (/_ this is a default export _/)
  - const root = ReactDOM.createRoot(document.getElementById("root))

- # How to render a react component/element in root?

  - root.render(<REACT_COMPONENT_OR_REACT_ELEMENT>)
  - this render method is given to the root object by the react-dom library.

- # Folder and file structure

  - core files index.html, styles.css, App.js and .gitignore
  - App.js is the root of react
  - make folder src/components, and src/utils
  - inside components we will make the react functional components in .jsx file
    - each of these files will be exported as a component and then imported and rendered in App.js

- # index.html

  - use emmet ! for basic scaffolding of html
  - then make a <div id="root"></div> in the body of html
  - below this div in body, make a <script src="./App.js" type="module"></script>
  - type="module" is used in script tag as we will be using the import statement in our code.

- # Code Bundler (parcel)

  - it is installed as a dev dependency
  - npm i -D parcel

  - # How to start parcel
    - in the package.json, delete the "main": "..."
    - add this command in the script section
      - "start": "npx parcel index.html"
      - npx executes the package, while npm installs a package
    - now in the terminal npm start, or npm run start
    - for ** Production Build ** we need npm parcel build index.html
    - we can add this command in the script section also as,
      - "build": "npx parcel build index.html"
      - to run this command, in the terminal type npm run build and press enter
    - browserslist:
      - in package.json add(example),
        - "browserslist": {"last 2 chrome versions"}
      - there is a website https://browsersl.ist/ which is helpful to set browserslist
      - browserslist works when build is used

- # What are react hooks?

  - They are kind of utility functions
  - Two main hooks used most of the time in react coding are useState() and useEffect().
  - import {useState, useEffect} from 'react' (/_ they are named export _/)
  - hooks can only be used inside a functional component

  - # useState() hook

    - Whenever a state variable updates react will re-render(reconciliation cycle) that component in which that state variable is being used
    - when the set function of the useState() is called, it will make react to re-render the component
    - Never create useState() inside if - else, for loop or inside a function other than the functional component

  - # useEffect() hook

    - useEffect(() => {}, []), takes in two arguments when called
    - The first argument is a callback function
    - The second argument is an array, called as a dependency array in react terms
    - This dependency array controls the calling of the first argument, ie. the callback function
    - When dependency array is not given as an argument then useEffect() callback is called **everytime** the component is rendered
    - **but when a dependency array is put and the dependency array then callback function is called just once when the component is rendered for the first time**
    - if there is something put inside the dependency array then the callback function is called when that thing is updated

  - # useParams()

    - const {SOME_PARAMETER} = useParams()

  - # useRouteError()
    - const err = useRouteError()

- # App.js with routes in react?

  - import ReactDOM from 'react-dom/client'
  - import Header from '../components/Header'
  - import Main from '../components/Main'
  - import Error from '../components/Error'

  - const App = () => {
    - return (
      - <div>
        - <Header />
        - <Outlet />
      - </div>
    - )
  - }

  - # Routing Configuration

    - we will use npm i react-router-dom (/_ if not already installed _/)
    - In App.js
    - import {createBrowserRouter, RouterProvider, Outlet} from 'react-router-dom'

    - ...
    - ...
    - ... previous code

    - const appRouter = createBrowserRouter
    - ([

      - {

        - path: "/",
        - element: <App/>
        - children: [

          - {
            - path: "/",
            - element: <SOME_COMPONENT/>
          - },
          - {
            - path: "/SOME_OTHER_PATH"
            - element: <SOME_OTHER_COMPONENT/>
          - }

        - ],
        - errorElement: <Error/>

      - }

    - ])
    - const root = ReactDOM.createRoot(document.getElementById("root"))
    - root.render(<RouterProvider router = {appRouter}/ >)

- # Link Element in react

  - Never use <a></a> tag in react as it makes the whole app to re-render
  - import {Link} from 'react-router-dom'
  - <Link to="/SOME_PATH"><li>SOME_TEXT</li></Link>

- # class based components

  - import React from 'react'
  - class About extends React.Component {
    - constructor(props) {
      - super(props)
    - }
    - render() {
      - return (<SOME_JSX_TAG>{this.props.SOME_FIELD}<SOME_JSX_TAG>)
    - }
  - }

  - # Creating state variables in class based components

    - import React from 'react'
    - class About extends React.Component {
      - constructor(props) {
        - super(props)
        - this.state = {
          - count_one: 1,
          - count_two: 2,
        - }
      - }
      - render() {
        - return (
          - <div>
            - <SOME_JSX_TAG>{this.props.SOME_FIELD}<SOME_JSX_TAG>
            - <SOME_OTHER_JSX_TAG>{this.state.count_one}<SOME_OTHER_JSX_TAG>
            - <SOME_OTHER_OTHER_JSX_TAG>{this.state.count_two}<SOME_OTHER_OTHER_JSX_TAG>
          - </div>
        - )
      - }
    - }

    - # How to update the variables created in the state object in class based components?

      - using this.setState() function anywhere in the class
      - it takes in an object which will update the variable
      - if you want to update the count_one variable in the above example
      - then,
      - in the this.setState() function,
      - this.setState({
        - count_one: this.state.count_one + 1,
      - })
      - for an example, we may use this.setState() function inside onClick={() => {this.setState({...update definition here...})}} method of a button element
      - **NEVER UPDATE THE STATE VARIABLE DIRECTELY**
      - **whenever setState() is called and finished running, it triggers an update on the react component (updating phase) - refer the react lifecycle diagram for more info**

- # How is a class component loaded?

  - When a class component is loaded, then the constructor of the class is called first then the render method is called.

- # componentDidMount() method

  - this method is called when the component and its children are completely mounted in the UI/DOM (render() method has completed running)
  - this method is mostly used to make an api call similar to functional components where we make an api call in useEffect(()=>{}, [])
  - useEffect() hook with an empty dependency array [] in functional components works similar to compenentDidMount() method of class based components, _although we should never compare hooks to the lifecycle methods_
  - **In case of multiple children with componentDidMount() method in the same component**

    - If there are multiple children with componentDidMount() then the calling of componentDidMount() will be batched together and both child render will be called before the calling of the componentDidMount()
    - actually when there are two or more children then the render phase will be batched together and the commit phase of the children will be batched together, this happens as the commit phase (DOM update on the UI) is the most expensive(ram consuming/time taking) process

  - # How to call an api from componentDidMount()?

    - first step is to make the componentDidMount() an async function, eg:- async componentDidMount() {}
    - in the definition of this method make the api call using fetch()
    - # using the data that you get from the api
      - create a state variable in this.state and give it some dummy data
      - then using this.setState(), update the data from api to the state variable
      - this state variable with the data can be used in the jsx like any other state variable as explained above

  - **See React lifecycle method diagram in react.wojtek to understand above explanation**

- # componentDidUpdate() method of class based components

  - after the component is finished updating
  - this method is not called after the mounting cycle

- # componentWillUnmount() method of class based components

  - Just before the removal of a component from the DOM this method is called

- # Important Points
  - Whenever a state variable updates react will re-render that component in which that state variable is being used
  - # When to make an api call?
    - as soon as the page loads make api call and then render the UI
    - as soon as the page loads render the UI and then make api call and after the data from api call is returned then render the UI with api data
