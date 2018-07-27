# reactBoilerplate
* practicing a boilerplate for react without create-react-app
* Guide and Credits go to : https://hackernoon.com/how-to-build-a-react-project-from-scratch-using-webpack-4-and-babel-56d4a26afd32 

**Note:** this is a barebones build, does not provide functionality like redux!

**npm start** to run locally

## NPM Bundles:
* webpack: module bundler, bundles projects into a single file in production.
* webpack-cli: provides webpack functionality in command line.
* babel-core: used to transform es6 to es5
* babel-loader: webpack helper. (Notice how you load this module in webpack.config.js)
* babel-preset-env: further converts es6, es7, es8 to es5.
* babel-preset-react: converts JSX to Javascript
* css-loader & style-loader: webpack helper to load style into the app.


## webpack.config.js
This is where we tell webpack how it should bundle our files.

```
const path = require("path");

module.exports = {
  entry: "./src/index.js",
  output: {
    path: path.join(__dirname, "/dist"),
    filename: "index_bundle.js"
  }
};

```
Tell webpack to enter at index.js, then bundle everything into a dist directory with an index_bundle.js

```
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        },
      },
      {
        test: /\.css$/,
        use: ["style-loader", "css-loader"]
      }
    ]
  }
```
Tell webpack to use load javascript files and css files.

```
  plugins: [
    new HtmlWebpackPlugin({
      template: "./src/index.html"
    })
  ]
```
Tell webpack to use html-webpack injects script inside the HTML file, writing it to the /dist directory.

## .babelrc
* This tells babel which presets to use for transpiling. 
* env: used for transpiling code to es5
* react: used for transpiling jsx to es5

