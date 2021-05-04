# 17 - Utilizando o useEffect

- Mais um **hook.**
    - Funções importadas do react.

# O que faz o useEffect?

- Serve pra disparar uma função quando algo acontecer na aplicação
    - Exemplo: um variável mudar

## Sintaxe

- Recebe dois parâmetros
    - **Função**: Qual função quero executar.
    - **Dependências**: Quando executar a primeira função.
        - **Vazio [ ]**, vai executar uma única vez assim que for renderizado em tela
        - **Nunca deixar sem o segundo parâmetro, se não vai entrar em loop.**
        - **Não alterar a dependência dentro da própria função**

```jsx
useEffect(() => {
	função
},[dependencias]);
```

# Buscando dados da API

- **Fetch** → Buscar dados
- Transformar em JSON
- Armazenar na variável de repositórios

```jsx
useEffect(() => {
	fetch('https://api.github.com/orgs/rocketseat/repos')
	.then(response => response.json)
	.then(data => setRepositories(data))
},[]);
```

# useState para listagem

- Vai armazenar um listagem
- Quando é uma lista, iniciamos o valor do estado com um array vazio "[ ]"

```jsx
const [repositories, setRepositories] = useState([])
```