# Manejo de asincronismo con JavaScript

## Introduction
En este repositorio podrás encontrar la práctica y los ejercicos realizados durante el curso de Asincronismo con JavaScript de [Platzi](https://platzi.com/clases/asincronismo-js/).

## Table of contents
* [General info](#general-info)
* [Technologies](#technologies)
* [Setup](#setup)

## General info
Los ejercicios en este repositorio fueron realizados para ejemplificar los diferentes métodos que tenemos para manejar asincronismo con javascript, los cuales incluyen:
* Callbacks - Una función que se pasa a otra función como argumento.

```
function sum(num1, num2) {
    return num1 + num2 
}

function calc(num1, num2, callback) {
    return callback(num1, num2);
}

console.log(calc(6, 2, sum));
```

* Promises - Se utiliza para funciones asíncronas, representando un valor que puede estar disponible ahora, en el futuro, o nunca, si la promesa es rechazada.

```
const  somethingWillHappen = () => {
    return new Promise((resolve, reject) => {
        if(true) {
            resolve('Hey!');
        } else {
            reject('Whooops!');
        }
    });
};

somethingWillHappen()
    .then(response => console.log(response))
    .catch(err => console.log(err));

```

* Async/await - Implementación de ES8 para simplificar el manejo de asincronía en JS(try/catch).

```
const fetchData = require('../utils/fetchData');
const API = 'https://rickandmortyapi.com/api/character/';

const anotherFunction = async (url_api) => {
    try {
        const data = await fetchData(url_api);
        const character = await fetchData(`${API}${data.results[0].id}`);
        const origin = await fetchData(character.origin.url);

        console.log(data.info.count);
        console.log(character.name);
        console.log(origin.dimension);

    } catch(error) {
        console.error(error);
    }
}

console.log('Before');
anotherFunction(API);
console.log('After');

```

## Technologies
El projecto está creado con :

* Node version: 14.15.4

## Setup
Para instalar todas las dependencias debes correr el comando `$ npm install` desde tu terminal. 

Para correr el código desde tu terminal, usa el siguiente comando:

`$ npm run <script>`


