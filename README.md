# 20 - Typescript no React

- Função principal → Tipar as propriedades que um componente pode receber.
- **Exemplo:**
    - A propriedade repository.
    - Ainda não sabemos exatamente o formato das informações desse repositório.
    - Por não saber o formato do repositório, dificulta a utilização e entendimento dessa propriedade em toda a aplicação.
- Vai ajudar a controlar quais propriedades são obrigatórias
- Saber quais informações preciso.

# Instalar TypeScript

- Instalar como dependência de desenvolvimento

```bash
yarn add typescript -D
```

- Inicializar typescript na aplicação
    - Vai criar um tsconfig.json
        - Configurações prontas

```bash
yarn tsc --init
```

# Configurações TS para React

- No tsconfig.json
- **Não é preciso entender tudo**
- lib → Adiciona funcionalidades/ Tipagens que não teria proprias da DOM
    - dom
    - dom.iterable
    - esnext
- allowjs: true → Permite ter arquivos tanto JS quanto TS (ajuda na transição)
- allowSythetic: true
- strict: true → entrar no modo strict
- moduleResolution: "node"
- resolveJsonModule: true → Possibilidade de importar arquivos JSON
- isolatedModules: true
- noEmit: true → Caso executar o build da aplicação e ele não emitir
- jsx: "react-jsx" → Fala que estamos utilizando jsx
- remover target e module (por enquanto?)
- dar uma vírgula
    - include: ["src"] → Dizendo onde o código exclusivamente vai estar

```bash

```

# Configurações no Webpack

- No webpack.config.js

```bash
yarn add @babel/preset-typescript -D
```

- Adicionar preset
- test: /\.(j|t)sx$/,
- extensions: ['.js','.jsx','.ts','.tsx'],
- entry: ...'index.tsx'
- Mudar tipo do arquivo index para tsx

# Bibliotecas de Tipos

- Algumas bibliotecas não vem com a biblioteca de tipos do TS incluso.
- Normalmente há um @types/ para ser instalado

```bash
yarn add @types/react-dom -D
```
