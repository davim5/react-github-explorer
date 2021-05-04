# 11 - Primeiro componente React

# O que é?

- São como se fossem as tags no HTML
- São formas de encapsular quantidade de código dentro de um único elemento
- Esse elemento com sua própria funcionalidade, estilização e estrutura.
- Forma de organizar e dividir a aplicação em vários pedacinhos que conectados formam algo amior
- **No React, tudo são componentes.**

# Como é?

- Uma função.
- Começa sempre com letra maiúscula.
- Retorna HTML.
- Um componente por arquivo no máximo (convenção).

# Criando primeiro componente

## Pasta components

- Criar arquivo RepositoryList.jsx

```jsx
export function RepositoryList(){
    return(
        <section className="repository-list">
            <h1>Lista de repositórios</h1>
            <ul>
                <li>
                    <strong>{repositoryName}</strong>
                    <p>Forms in React</p>
                    <a href=""> Acessar repositório</a>
                </li>
                <li>
                    <strong>unform</strong>
                    <p>Forms in React</p>
                    <a href=""> Acessar repositório</a>
                </li>
                <li>
                    <strong>unform</strong>
                    <p>Forms in React</p>
                    <a href=""> Acessar repositório</a>
                </li>
            </ul>
        </section>
    );
}
```

# Mudar estilização

```jsx
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body{
    font: 16px "Helvetica Neue",Arial,Helvetica,sans-serif;
    color: #121214;

}
```

# Coisas legais

- Podemos fazer transição entre HTML e JS de forma muito natural;
- Sempre que quisermos colocar uma variável JS dentro de um HTML, é só separar com chaves **{ }**

```jsx
const repositoryName = 'unform2'
...
								<li> 
									<strong>{repositoryName}</strong>
								  <p>Forms in React</p>
								  <a href=""> Acessar repositório</a>
								</li>
```