# React Starter

## Tutorial

[![Video Tutorial React Starter](https://img.youtube.com/vi/v7dR15NEe-8/0.jpg)](https://www.youtube.com/watch?v=v7dR15NEe-8)

## Get the code

```
git clone --depth=1 https://github.com/cizar/dh-react-starter.git ~/my-project
```

## Try it out!

```
cd ~/my-project
npm install
npm start
```

## Step by step

Create an empty directory and go into it

```
mkdir my-project && cd $_
```

Create the **package.json** file

```
npm init -y
```

Install project dependencies

```
npm install --save react react-dom \
  babel-core babel-preset-env babel-preset-react babel-preset-stage-2 \
  webpack webpack-dev-server babel-loader
```

Create **.babelrc** to configure Babel

```
cat << __EOF__ > .babelrc
{
  "presets": ["env", "react", "stage-2"]
}
__EOF__
```

Create **webpack.config.js** to configure Webpack

```
cat << __EOF__ > webpack.config.js
var path = require('path')
var config = {
  context: path.resolve(__dirname, 'src'),
  entry: './index.js',
  output: {
    path: path.resolve(__dirname, 'build'),
    filename: 'bundle.js'
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: 'babel-loader'
      }
    ]
  }
}
module.exports = config
__EOF__
```

Create the **index.html** file

```
cat << __EOF__ > index.html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>React</title>
</head>
<body>
  <div id="root"></div>
  <script src="bundle.js"></script>
</body>
</html>
__EOF__
```

Create the source code directory structure

```
mkdir -p src/components
```

Create the main application component

```
cat << __EOF__ > src/components/App.js
import React from 'react'

class App extends React.Component {
  render () {
    return (
      <div>
        <h1>Funciona!</h1>
      </div>
    )
  }
}
export default App
__EOF__
```

Create the application entry point

```
cat << __EOF__ > src/index.js
import React from 'react'
import ReactDOM from 'react-dom'
import App from './components/App'
const target = document.getElementById('root')
ReactDOM.render(<App />, target)
__EOF__
```

Run the development server

```
./node_modules/.bin/webpack-dev-server --open
```
