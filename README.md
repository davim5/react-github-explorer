# 12 - Propriedades no React

- Segundo conceito mais importante

# O que são?

- Funcionam como atributos funcionam para Tags HTML
- Informações/variáveis que podemos passar para um componente funcionar de forma diferente
    - **Exemplo:**
        - href em um <a>
        - Vai mudar o comportamento do link de acordo

# Conceito de Propriedade

- Consiste em poder enviar um informação do componente pai para o filho.

## Enviando informação

- Passar na tag

```jsx
import { RepositoryItem } from "./RepositoryItem";

export function RepositoryList(){
    return(
        <section className="repository-list">
            <h1>Lista de repositórios</h1>
            <ul>
                <RepositoryItem repository='name'/>
                <RepositoryItem repository='name'/>
                <RepositoryItem repository='name'/>
                <RepositoryItem repository='name'/>
            </ul>
        </section>
    );
}
```

### Enviando Objeto

- Podemos passar, ao invés de um texto, um objeto.
- Assim podemos colocar todas as informações de um repositório dentro de um único objeto.

```jsx
import { RepositoryItem } from "./RepositoryItem";

const repository = {
    name: 'unform',
    description: 'Forms in React',
    link: 'https://github.com/unform'
}

export function RepositoryList(){
    return(
        <section className="repository-list">
            <h1>Lista de repositórios</h1>
            <ul>
                <RepositoryItem repository={repository}/>
                <RepositoryItem repository={repository}/>
                <RepositoryItem repository={repository}/>
                <RepositoryItem repository={repository}/>
            </ul>
        </section>
    );
}
```

## Acessando a informação

- Podemos acessar todas as propriedades de um componente através dos argumentos da função.
- React coloca todas as propriedades dentro de um argumento chamado **props**.

```jsx
export function RepositoryItem(props){
    return(
        <li>
            <strong>{props.repository}</strong>
            <p>bla bla bla</p>
            <a href=""> Acessar repositório</a>
        </li>
    );
}
```

### Acessando Objeto

```jsx
export function RepositoryItem(props){
    return(
        <li>
            <strong>{props.repository.name}</strong>
            <p>{props.repository.description}</p>
            <a href={props.repository.link}> Acessar repositório</a>
        </li>
    );
}
```

## Verificação caso esteja vazia

- Caso a propriedade acessada esteja vazia

```jsx
export function RepositoryItem(props){
    return(
        <li>
            <strong>{props.?repository}</strong>
            <p>bla bla bla</p>
            <a href=""> Acessar repositório</a>
        </li>
    );
}
```

# Criando componente de Repositório

- Cada repositório da lista vai ser um componente.
- Pode ser repetido quantas vezes quiser.
    - **Quando percebemos que tem algo repetindo no programa, na maioria das vezes, faz sentido criar um componente para encapsular aquilo.**

```jsx
export function RepositoryItem(props){
    return(
        <li>
            <strong>{props.repository.name}</strong>
            <p>{props.repository.description}</p>
            <a href={props.repository.link}> Acessar repositório</a>
        </li>
    );
}
```

- Criado objeto **repository** para armazenar e enviar todas as informações necessárias de um só vez.

```jsx
import { RepositoryItem } from "./RepositoryItem";

const repository = {
    name: 'unform',
    description: 'Forms in React',
    link: 'https://github.com/unform'
}

export function RepositoryList(){
    return(
        <section className="repository-list">
            <h1>Lista de repositórios</h1>
            <ul>
                <RepositoryItem repository={repository}/>
                <RepositoryItem repository={repository}/>
                <RepositoryItem repository={repository}/>
                <RepositoryItem repository={repository}/>
            </ul>
        </section>
    );
}
```

- OBS: Ás vezes pode precisar de um refresh pra carregar um componente novo página.