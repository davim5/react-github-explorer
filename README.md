# 15 - Fast Refresh no Webpack

- Ferramenta que vai ajudar no desenvolvimento
- Quando estamos rodando a aplicação com webpack server e fazemos uma alteração, ele reseta a aplicação (estados e etc..)
    - Ás vezes isso não é prático.
- **Form de conseguir alterar o código da aplicação e ter ele refletido no browser sem resetar o estado dos componentes.**

# Instalar

```jsx
yarn add -D @pmmmwh/react-refresh-webpack-plugin react-refresh
```

# Configurar

- No webpack config
- Importar
- Adicionar na sessão de plugins
    - Somente ambiente de desenvolvimento
        - Verificar se estamos em desenvolvimento
        - Filtrar boolean, para não crashar com o resultado *false*
- Na sessão devServer
    - hot: true,
- No babel loader
    - loader:'babel-loader'
    - options
        - Checar desenvolvimento

```jsx
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const ReactRefreshPlugin = require('@pmmmwh/react-refresh-webpack-plugin')

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
		hot: true,
	},
	plugins: [
		isDevelopment && new ReactRefreshPlugin(),
		new HtmlWebpackPlugin({
			template: path.resolve(__dirname,'public','index.html')
		})
	].filter(Boolean),
	module: {
		rules: [
			{
				test: /\.jsx$/,
				exclude: /node_modules/,
				use: {
					loader: 'babel-loader',
					options: {
						plugins: [
							isDevelopment && require.resolve('react-refresh/babel')
						].filter(Boolean)
					}
				}, 
			},
			{
				test: /\.scss$/,
				exclude: /node_modules/,
				use: ['style-loader','css-loader','sass-loader'], 
			}
		],
	}
};
```