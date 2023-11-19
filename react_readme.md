# React Basics

- # Install React in the Project (CDN and npm)

  - There are three basic kinds of react libraries that are needed
  - They are npm i react react-dom react-router-dom

- # How to create an Element in react?

  - 1. Using the createElement method from react library
       - import React from "react"
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
  - import React DOM from "react-dom/client"
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

- # App.js

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

- # How to make routes?
