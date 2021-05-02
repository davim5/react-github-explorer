# Ambiente Dev e Produção

- Configura um ambiente de desenvolvimento e um de produção.

# Criar variável

- const isDevelopment
    - Vai receber um variável ambiente.
        - Variável pra configurar algo de acordo com o ambiente da aplicação.
        - **NODE_ENV**
- Verificar se a variável é diferente de 'production'

```jsx
const isDevelopment = process.env.NODE_ENV !== 'production';
```

- Na configuração do webpack, modifcar o **mode** e o **devtool** dependendo da condição da variável.
    - mode: isDevelopment ? 'development' : 'production',
    - devtool: isDevelopment ? 'eval-source-map' : 'source-map',

```jsx
const path = require('path')
const HtmlWebpackPlugin = require('html-webpack-plugin')

module.exports = {
	mode: isDevelopment ? 'development' : 'production',
	devtool: isDevelopment ? 'eval-source-map' : 'source-map',
	entry: path.resolve(__dirname,'src','index.jsx'),
	output: {
		path: path.resolve(__dirname,'dist'),
		filename: 'bundle.js'
	},
	resolve: {
		extensions: ['.js','.jsx'],
	},
	devServer: {
		contentBase: path.resolve(__dirname,'public'),
	},
	plugins: [
		new HtmlWebpackPlugin({
			template: path.resolve(__dirname,'public','index.html')
		})
	],
	module: {
		rules: [
			{
				test: /\.jsx$/,
				exlude: /node_modules/,
				use: 'babel-loader', 
			}
		],
	}
};
```

# Criar variável NODE_ENV

- No Windows

## Instalar cross-env

- Serve para definir variáveis ambiente independente do SO

```bash
yarn add cross-env -D
```

# Scripts no package.json

- Scripts para executar mais fácil.
- Quando script é executado a partir do package.json, não precisa pôr yarn.
    - **dev**: ambiente de desenvolvimento
        - webpack serve
    - **build**: ambiente de produção.
        - cross-env NODE_ENV=production webpack

```json
{
  "name": "01-github-explorer",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT",
	"scripts": {
		"dev": "webpack serve",
		"build": "cross-env NODE_ENV=production webpack",
	},
  "dependencies": {
    "react": "^17.0.2",
    "react-dom": "^17.0.2"
  },
  "devDependencies": {
    "@babel/cli": "^7.13.16",
    "@babel/core": "^7.14.0",
    "@babel/preset-env": "^7.14.0",
    "@babel/preset-react": "^7.13.13",
    "babel-loader": "^8.2.2",
    "html-webpack-plugin": "^5.3.1",
    "webpack": "^5.36.2",
    "webpack-cli": "^4.6.0",
    "webpack-dev-server": "^3.11.2"
  }
}
```

- Agora pode rodar com *yarn dev* para ambiente de desenvolvimento.

```bash
yarn dev
```