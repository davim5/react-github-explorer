# react-github-explorer
- Funcionalidade de Dev Server

# Instalar

```bash
yarn add webpack-dev-server -D
```

# Pra que

- Sempre que mudamos o código precisamos executar webpack para converter o código de novo.
- Podemos automatizar.

# Configuração

- No **webpack.config.js**
- Colocar devServer:
    - Content base: colocar onde está o arquivo html estático

```jsx
const path = require('path')
const HtmlWebpackPlugin = require('html-webpack-plugin')

module.exports = {
	mode: 'development',
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

- Basta executar uma vez agora

```bash
yarn webpack serve
```

- Agora sempre que houver uma mudar algo e salvar o arquivo, o bundle será gerado automaticamente com a alteração.