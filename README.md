# 16 - Estilização da listagem

- Remover o Counter

# Estilizar os repositórios

- Na pasta styles
    - Criar arquivo repositories.scss → Estilização dos repositórios
- Importar repositories.scss no RepositoryList.jsx

```jsx
import { RepositoryItem } from "./RepositoryItem";

import '../styles/repositories.scss';

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

## Estilizando

### &

- Se refere ao próprio elemento

### Evitando treta com margin top

- Assim, o ultimo elemento ficaria com margin também ❌

```scss
li{
	margin-bottom: 20px
}
```

- Desse modo.
    - Toda *li* que possui um *li* antes, vai ter margin top ✅

```scss
li{
	& + li{
		margin-top: 20px;
	}
}
```

### Estilização completa

```scss
section.repository-list{
    margin: 40px;

    h1{
        margin-bottom:16px;
    }

    ul{
        list-style: none;

        li{
            & + li{
                margin-top: 20px;
            }

            p{
                font-size: 14px;
                color: #444;
                margin-top: 8px;
            }

            a{
                display: inline-block;
                margin-top: 16px;
                text-decoration: none;
                color: #8257e6;
            }
        }
    }
}
```