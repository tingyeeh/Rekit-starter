# 升级Rekit Webpack 3 到 Webpack 4
### 升级必备安装
```
yarn add --dev webpack webpack-dev-server webpack-manifest-plugin url-loader style-loader postcss-loader less-loader file-loader eslint-loader css-loader html-webpack-plugin mini-css-extract-plugin
```
### 做一些修改
#### 因为有以下 Warning
```
React-Hot-Loader: react-🔥-dom patch is not detected. React 16.6+ features may not work.
```
所以把 react-hot-loader 改成 @hot-loader/react-dom
```
yarn add --dev @hot-loader/react-dom
```
添加 alias 到 .\config\webpack.config.dev.js 和 .\config\webpack.config.prod.js
```
'react-dom': '@hot-loader/react-dom',
```
#### 因为有以下 error
```
Warning: Please use `require("history").createBrowserHistory` instead of `require("history/createBrowserHistory")`. Support for the latter will be removed in the next major release.
```
所以修改 .\src\common\history.js
```
import createHistory from 'history/createBrowserHistory';

// A singleton history object for easy API navigation
const history = createHistory();
export default history;

```
改成
```
import { createBrowserHistory as createHistory } from 'history'
const history: History = createHistory()
export default history;
```

### 其他 TODO
添加 semantic ui
```
yarn add react-dom react-redux react-scripts react-textarea-autosize redux redux-form semantic-ui-react 
```
```
yarn add --dev @babel/plugin-transform-react-jsx-source @babel/preset-env cpy-cli craco-less
```

```
yarn add lodash
yarn add --dev babel-plugin-lodash @babel/cli @babel/preset-env semantic-ui-less --dev
```
