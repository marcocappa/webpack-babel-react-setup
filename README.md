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

Install the following packages:

1. webpack (core)
2. webpack-cli (cli commands)
3. webpack-dev-server (will allow to run dev server)
4. html-webpack-plugin (simplilfies working with html files)
5. html-loader (html files loader)

### 2.1 Install packages

```
npm i webpack webpack-dev-server html-webpack-plugin --save-dev
```

### 2.2 Create webpack config file

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

### 2.3 Add scripts

Add build and start commands to scripts section of package.json:

```
"scripts": {
    "build": "webpack --mode production",
    "start": "webpack-dev-server --open --mode development",
}
```
