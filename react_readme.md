# React Basics

- # Install React in the Project (CDN and npm)

  -- There are three basic kinds of react libraries that are needed
  -- They are npm i react react-dom react-router-dom

- # How to create an Element in react?

  - 1. Using the createElement method from react library
       -- import React from "react"
       -- const Heading = React.createElement("h1", {}, "Hello World!")
       -- {} object is used to give attributes
       -- eg:- const heading = React.createElement("h1", {id:"something"}, "Hello World!")
       -- it is called props object in react

    - # How to create a tree structure of elements in react using createElement method?

      -- const Grandfather = React.createElement("div", {id="grandfather"}, React.createElement("div", {id:father}, React.createElement("h1", {id:"child}, "Hello World from Child")))

    - # How to create siblings using createElement method?
      - const Father = React.createElement("div", {id: father}, [React.createElement("h1", {id:"child-one"}, React.createElement("h1", {id: "child-two"}, ))])

  - 2. How to create components/elements using JSX in react?

- # How to create root in react?

  -- root is an HTML Element which is used as a root to allow react components to render inside it.
  -- root is created by the react-dom library createRoot method.
  -- import ReactDOM from "react-dom"
  -- const root = ReactDOM.createRoot(document.getElementById("root))

- # How to render a react component/element in root?

  -- root.render(<REACT_COMPONENT_OR_REACT_ELEMENT>)
  -- this render method is given to the root object by the react-dom library.

- # Code Bundler (parcel)
  - it is installed as a dev dependency
  - npm i -D parcel
