# 21 - Componentes com Typescript

# Configurar componentes em JSX para TSX

## App

- Só mudar para tsx

## RepositoryItem

- Mudar para tsx
- Erro no props (Parameter 'props' implicity has an 'any' type
    - De forma padrão, props recebe o tipo "any".
    - Ele não sabe qual é seu tipo.
        - Para typescript isso é dado como erro.
    - Precisa dizer o que o props deve receber

    ### Interface

    - Poderia ser type
        - Tem funcionalidades muito semelhantes.
        - Mas interface é mais usado
    - Convenção: Quando se vai criar um tipagem ou dizer o formato das propriedades de um componente.
        - Repete nome do componente seguido de "Props"

    ```tsx
    interface RepositoryItemProps {
    	repository: {
    		name: string;
    		description: string;
    		html_url: string;
    	}
    }
    ```

    - **Não precisaria colocar todas informações recebidas dentro do tipo?**
        - Não. No TS, só é necessário tipar as que irão ser utilizadas na aplicação.
    - Se a propriedade não fosse obrigatória, é só colocar um "**?**" antes do "**:**"

    ### Na função

    ```tsx
    export function RepositoryItem(props: RepositoryItemProps)
    ```

    # No Estado

    - Quando se tem um estado que é um array, precisamos informar seu tipo.
        - Ou seu tipo fica "**never**"
    - Criar uma *Interface* para o Repository

    ```tsx
    interface Repository {
    	name: string;
    	description: string;
    	html_url: string;
    }
    ```

    - Se o Estado fosse armazenar somente um repositório,
    - Existe um funcionalidade do typescript que é ***generic.***
        - No caso, o useState, pode ser qualquer tipo.
        - Então precisa passar qual é tipo do Estado.
            - Em "<>", antes dos parênteses.

            ```tsx
            const [repositories, setRepositories] = useState<Repository[]>([]);
            ```