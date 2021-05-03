# Para poder importar arquivos css.

# Criar pastas styles

- No src
- Criar global.css
    - Configurações globais

- Quando utilizamos react, toda a parte arquivos de css são importados por dentro do Javascript em si.

```jsx
import './styles/global.css'
```

# Criar uma regra para arquivos CSS no webpack.config

- Instalar **style-loader** e **css-loader** como dependência de desenvolvimento.

    ```bash
    yarn add style-loader css-loader -D
    ```

    - São utilizados em conjunto.
    - Pegam todo o css da aplicação e utilizar na página conforme necessário.

```jsx
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

const isDevelopment = process.env.NODE_ENV !== 'production';

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
				exclude: /node_modules/,
				use: 'babel-loader', 
			},
			{
				test: /\.css$/,
				exclude: /node_modules/,
				use: ['style-loader','css-loader'], 
			}
		],
	}
};
```