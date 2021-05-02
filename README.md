# Utilizando Source Maps

- São formas de conseguir **visualizar erros no código original** mesmo quando todo o código está amontoado no bundle.js
- Forma de visualizar erros, de forma clara

# Configurar

- Tem diferentes source maps.
    - Alguns são mais detalhados (ambiente desenvolvimento.
    - Outros mais rápidose outros mais lentos
    - Um pra dev e outro pra produção
- No webpack.config.js
    - devtool: 'eval-source-map'

```jsx
const path = require('path')
const HtmlWebpackPlugin = require('html-webpack-plugin')

module.exports = {
	mode: 'development',
	devtool: 'eval-source-map',
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

- Agora o console vai mostrar o erro no arquivo e na linha do erro.
- Muito mais fácil de debugar.