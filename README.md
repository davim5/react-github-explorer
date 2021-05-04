# 18 - Listando repositorios

- Pegar repositórios carregados da API
- Para cada um, mostrar um *RepositoryItem*

# map

- Quando se tem informações armazenadas em um vetor para cada componente mostrar algo diferente.
- Percorrer repositórios e para cada um executar uma função
- map → para cada repositório vai ser retornado um *RepositoryItem*

# Como fazer

- Com chaves
    - Precisa colocar **return**

    ```jsx
    <ul>
    	{repositories.map(repository=> {
    		return <RepositoryItem repository={repository} />
    	})}
    </ul>
    ```

- Com parenteses
    - Pode **omitir return**

    ```jsx
    <ul>
    	{repositories.map(repository=> (
    		<RepositoryItem repository={repository} />
    	))}
    </ul>
    ```

- Se couber, pode ser na mesma linha

```jsx
<ul>
	{repositories.map(repository=> <RepositoryItem repository={repository} />)}
</ul>
```

# Pegando as informações

- No repository item
- O nome tem que ser o mesmo do enviado pela API.

# Warning

- Cada filho em uma lista precisa ter uma **propriedade única** chamada ***key.***
- Tem que ser o **primeiro elemento**.
- Propriedade interna no react.

```jsx
<ul>
	{repositories.map(repository=> {
		return <RepositoryItem key={repository.name} repository={repository} />
	})}
</ul>
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d23e4ce4-f9dc-4b51-92c3-dfe053b3b0ba/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d23e4ce4-f9dc-4b51-92c3-dfe053b3b0ba/Untitled.png)