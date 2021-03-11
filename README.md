# Basic webpack babel react setup

This is a basic webpack babel react setup

## Step 1: Initialize the project

Create a folder and initialize a project with:

```
npm init -y
```

(This command will create "package.json" file in the directory. The "-y" option will skip the questions)

Create a "src/index.html" file with the following content:

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>How to set up React, Webpack, and Babel</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>
```

## Step 2: Set Up Webpack

### 2.1 Install webpack dependencies:

1. webpack (core)
2. webpack-cli (cli commands)
3. webpack-dev-server (will allow to run dev server)
4. html-webpack-plugin (simplilfies working with html files)
5. html-loader (html files loader)

Command:

```
npm i webpack webpack-dev-server html-webpack-plugin --save-dev
```

### 2.2 Create webpack configuration file

Create a "webpack.config.js" file with the following content:

```
const HtmlWebPackPlugin = require("html-webpack-plugin");
const path = require('path');

module.exports = {
entry: "./src/App.js",
output: {
  path: path.resolve(__dirname, 'dist'),
  filename: 'bundle.js',
},
plugins: [new HtmlWebPackPlugin({ template: "./src/index.html" })]
};
```

### 2.3 Add build and start to scripts section of package.json:

```
"scripts": {
    "build": "webpack --mode production",
    "start": "webpack-dev-server --open --mode development",
}
```

## Step 3: Set Up Babel

### 3.1 Install babel dependencies:

1. @babel/core
2. babel-loader
3. @babel/preset-env (to compile Javascript ES6 code down to ES5)
4. @babel/preset-react (to compile JSX down to Javascript)

```
npm i @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev
```

### 3.2 Create .babelrc config

Create the config file on the projet root and add this:

```
{
    "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```

### 3.3. Add "babel-loader" to webpack configuration:

Add to webpack.config.js this:

```
...

module.exports = {
    ...
    ...
    module: {
    rules: [
        {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
            loader: "babel-loader"
        }
        }
    ]
    },
    ...
    ...
};
```

## Step 4: Set Up React

### 4.1 Install React

In order to use react install these dependencies:

1. react (provides us with API to work with components)
2. react-dom (allows to render HTML to the DOM)

```
npm i react react-dom
```

### 4.2 Create App.js file

Create App.js file inside src folder with content:

```
import React from "react"
import ReactDOM from "react-dom"

const App = () => (
    <>
        <h1>Hello React</h1>
        <p>Minimal React configuration</p>
    </>
)

ReactDOM.render(<App />, document.getElementById("root"))
```
