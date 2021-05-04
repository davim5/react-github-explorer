# 13 - Estados do Componente

# O que é?

- Variáveis que o React vai monitorar sempre.
- Toda vez que seus valores mudarem, ele vai renderizar o componente.
- Forma de conseguir ter variáveis que ao alterar na aplicação, vão refletir na página.

# Criar componente de exemplo

- Contador

```jsx
export function Counter(){
	return(
		<div>
			<h2>0<h2/>
			<button type="button">
				Increment
			</button>
		<div/>
	);
}
```

- Criar função de incrementar
- Disparar função sempre que o botão for clicado
    - *onClick=*{função}

```jsx
let counter = 0;

function increment(){
	counter += 1;
}

export function Counter(){
	return(
		<div>
			<h2>0<h2/>
			<button type="button" onClick={increment}>
				Increment
			</button>
		<div/>
	);
}
```

## useState

- Importar **useState** do react
- Sempre que uma função do react começar com "use", é um **hook.**

```jsx
import { useState } from 'react';
```

### Declarando o useState

- Utilizando o useState

```jsx
// let counter = 0
let counter = useState(0)
```

- o useState não retorna apenas o valor da variável
- Ele retorna **duas "**coisas", em um Array.
    - counter[0] → Valor da variável
    - counter[1] → Função que permite alterar o valor da variável.
- A melhor maneira é utilizar atribuição por estruturação.

```jsx
const [counter,setCounter] = useState(0);
```

### Alterando o valor

- Somente é possível usando a função setCounter

```jsx
function increment(){
	// counter += 1;
	setCounter(counter + 1);
}
```

## Fragment

- Toda vez que colocamos dois componentes, sempre precisa ter um componente por volta deles
- Fragment: funciona como uma div, mas não afeta no css.
    - Uma div poderia atrapalhar no css

```jsx
return(
	<>
		<RepositoryList />
		<Counter />
	</>
)
```

# Componente Contador Completo

```jsx
import { useState } from 'react';

export function Counter(){

	const [counter, setCounter] = useState(0);
	
	function increment(){
		setCounter(counter + 1);
	}

	return(
		<div>
			<h2>0<h2/>
			<button type="button" onClick={increment}>
				Increment
			</button>
		<div/>
	);
}
```