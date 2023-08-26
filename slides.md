---
theme: seriph
layout: intro
class: text-center  gradient-to-r from-blue-500 to-blue-800!
background: radial-gradient(ellipse at center, rgba(0,0,0,0.5) 0%,rgba(0,0,0,0.5) 100%), url(https://source.unsplash.com/collection/94734566/1920x1080)
highlighter: shiki
lineNumbers: false
info: |
  ### Taller de Aplicaciones Web Descentralizadas con Vue 3 y Truffle

drawings:
  persist: false
transition: slide-left
title: Taller de Aplicaciones Web Descentralizadas
---

# TALLER DE APLICACIONES WEB DESCENTRALIZADAS 

 ### CON VUE 3 Y TRUFFLE

 <div class="flex justify-center gap-4 my-2">
  <img src="https://vuejs.org/images/logo.png" class="w-24 h-24" />
  <div class="flex flex-col justify-center gap-2">
    +
  </div>
  <img src="https://trufflesuite.com/img/truffle-logo-dark.svg" class="w-24 h-24" />
</div>


---
transition: fade-out
---

# Agenda

1. Introducción a las Aplicaciones Descentralizadas (DApps)
2. Configuración del Entorno: Truffle
3. Desarrollo de Contratos Inteligentes con Solidity
4. Interacción con la Red Ethereum usando Ethers
5. Configuración del Entorno: Vue 3
6. Creación de la Interfaz de Usuario con Vue.js
7. Integración Completa y Pruebas
8. Despliegue de la DApp en la Red de Prueba
9. Consideraciones Finales y Recursos


---
layout: center
---

# ¿Qué es una Aplicación Descentralizada (DApp)?

---
transition: slide-up
level: 2
---

# Web3

Web3 es la próxima evolución de Internet, permitiendo una interacción directa con las redes blockchain.

## ¿Qué es Web3?

- **Descentralizado:** Web3 cambia el control de entidades centralizadas a usuarios y comunidades.
- **Interoperable:** Conecta diferentes redes blockchain, permitiendo transferencias de datos y valor sin problemas.
- **Desconfiado:** Los contratos inteligentes automatizan acuerdos, reduciendo la necesidad de intermediarios.
- **Transparente:** Las transacciones y los datos se registran públicamente en el blockchain.

---
transition: slide-up
level: 2
---

# Introducción a las DApps

- Las Aplicaciones Descentralizadas (DApps) son aplicaciones que funcionan en una red blockchain en lugar de servidores centralizados.
- Utilizan contratos inteligentes para ejecutar lógica y almacenar datos en la cadena de bloques.
- Proporcionan transparencia, seguridad y autonomía a los usuarios.

---

# Conceptos Básicos de Blockchain y Ethereum

- **Blockchain**: Una cadena de bloques que registra transacciones de manera segura y transparente.
- **Ethereum**: Una plataforma de blockchain que permite ejecutar contratos inteligentes.

---

# Contratos Inteligentes y su Papel en las DApps

- **Contrato Inteligente**: Un programa autónomo que ejecuta lógica en la cadena de bloques.
- **Funcionamiento**: Los contratos inteligentes son ejecutados por todos los nodos en la red Ethereum.
- **Almacenamiento de Datos**: Los contratos pueden almacenar datos en la cadena de bloques.

---
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# ¿Cómo Difieren de las Aplicaciones Tradicionales?

- Aplicaciones Tradicionales:
  - Datos y lógica se almacenan en servidores centralizados controlados por una entidad.
  - Vulnerables a censura y ataques.
  
- DApps:
  - Datos y lógica se almacenan en la cadena de bloques.
  - No dependen de intermediarios centralizados.
  - Mayor seguridad y resistencia a la censura.

---

# Ventajas de las DApps

- **Transparencia**: Todas las transacciones y operaciones son visibles en la cadena de bloques.
- **Seguridad**: La tecnología blockchain proporciona un alto nivel de seguridad y resistencia a ataques.
- **Autonomía**: Los usuarios tienen control total sobre sus datos y activos.
- **Censura Resistente**: DApps no son susceptibles a la censura centralizada.
- **Interoperabilidad**: Pueden interactuar con otros contratos y DApps en la misma red.

---

# Desafíos de las DApps

- **Escalabilidad**: Algunas blockchains pueden tener limitaciones en la cantidad de transacciones que pueden manejar.
- **Usabilidad**: La experiencia del usuario puede ser compleja debido a la interacción con criptomonedas y claves privadas.
- **Costos**: Algunas operaciones en la cadena de bloques pueden ser costosas en términos de tarifas de gas.
- **Adopción**: Aunque en crecimiento, la adopción masiva de DApps todavía está en desarrollo.

---
preload: false
---

# Ejemplos de DApps

- **Uniswap**: Plataforma de intercambio de criptomonedas descentralizada.
- **CryptoKitties**: Juego de coleccionables basado en blockchain.
- **Decentraland**: Plataforma de mundo virtual descentralizado.
- **Aave**: Protocolo de préstamos y endeudamiento descentralizado.


---
layout: center
class: text-center
---

# Configuración del Entorno: Truffle

---

# Prerrequisitos

- Un proyecto Ethereum en Infura.
- Node.js instalado.
- Una billetera Ethereum para propósitos de prueba (Metamask).


# Instalación de Truffle 

Truffle es una herramienta de desarrollo de contratos inteligentes y un marco de pruebas para redes blockchain.

Instala Truffle globalmente utilizando el administrador de paquetes de Node.js:
```
npm install -g truffle
```

---

# Creación de un Proyecto Truffle

1. Crear un directorio para el proyecto: `mkdir mi-proyecto-dapp`
2. Navegar al directorio: `cd mi-proyecto-dapp`
3. Inicializar un proyecto Truffle: `truffle init`


# Instalar hdwallet-provider

`hdwallet-provider` es un paquete separado que firma transacciones para direcciones derivadas de una mnemotecnia de 12 o 24 palabras.

Por defecto, `hdwallet-provider` utiliza la primera dirección generada a partir de la mnemotecnia. Sin embargo, esto es configurable.

```
npm install @truffle/hdwallet-provider
```

---

# Configuración de la Red de Desarrollo

1. En el archivo `truffle-config.js`, configurar la red de desarrollo:

```javascript
   development: {
     host: "127.0.0.1",
     port: 7545, // Puerto de Ganache o la red local
     network_id: "*", // Match any network id
   },
```

2. Conectar Truffle a la red de desarrollo.

---

# Configuración de Infura

1. Crear una cuenta en [Infura](https://infura.io/).
2. Crear un nuevo proyecto en Infura y obtener la clave de API.
3. En el archivo `truffle-config.js`, configurar Infura:

```javascript
require("dotenv").config();
const HDWalletProvider = require("@truffle/hdwallet-provider");
const { NUXT_PUBLIC_INFURA_KEY, MNEMONIC } = process.env;
const infuraNetwork = 'wss://sepolia.infura.io/ws/v3/'+NUXT_PUBLIC_INFURA_KEY
module.exports = {
  networks: {
    development: {
      host: "127.0.0.1",
      port: 8545,
      network_id: "*",
    },
    sepolia: {
      provider: () => new HDWalletProvider(MNEMONIC, infuraNetwork),
      network_id: 11155111,
      gas: 5500000,
    },
  },
  compilers: {
    solc: {
      version: "^0.8.0",
    },
  },
};
```

4. Conectar Truffle a la red de prueba.

---

# Prueba de la Configuración

1. Crear un contrato de prueba en el proyecto Truffle.
2. Compilar el contrato: `truffle compile`
3. Migrar el contrato a la red de desarrollo: `truffle migrate --network development`
4. Verificar que la migración se realizó correctamente.

---
layout: center
class: text-center
---

# Desarrollo de Contratos Inteligentes

---

# Introducción a Solidity

- **Solidity**: Lenguaje de programación para escribir contratos inteligentes en Ethereum.
- Basado en la sintaxis de JavaScript.
- Diseñado para ejecutarse en la máquina virtual Ethereum (EVM).

---

# Estructura y Sintaxis de los Contratos

- **Contrato Inteligente**: Una clase que define la lógica y los datos almacenados en la cadena de bloques.
- Estructura básica:
  ```solidity
  pragma solidity ^0.8.0;

  contract MiContrato {
    // Estado y variables
    uint256 public miVariable;

    // Constructor
    constructor() {
        miVariable = 0;
    }

    // Funciones
    function setVariable(uint256 value) public {
        miVariable = value;
    }
  }
  ```

---

# Crear un contrato inteligente

Usando un editor, crea un contrato inteligente en el directorio `contracts/`. En este ejemplo, crearemos un contrato básico llamado `SimpleStorage.sol`.

```solidity
pragma solidity >=0.5.8;

contract SimpleStorage {
    uint256 storedData;

    function set(uint256 x) public {
        storedData = x;
    }

    function get() public view returns (uint256) {
        return storedData;
    }
}
```

---

# Compilación y Despliegue de Contratos

1. **Compilación**:
   - Utilizar el compilador de Solidity para convertir el código en bytecode.
   - Generar la ABI (Interfaz de Aplicación de Contrato) para interactuar con el contrato.

2. **Despliegue**:
   - Usar Truffle para desplegar el contrato en una red.
   - Obtener la dirección del contrato y la transacción de despliegue.

---

# Prueba de la Compilación y Despliegue

1. Compilar el contrato: `solc MiContrato.sol --bin --abi --optimize -o build/`
2. Configurar el archivo de migración en Truffle.
3. Migrar el contrato a la red de desarrollo: `truffle migrate --network development`
4. Verificar que el contrato se ha desplegado correctamente.




Claro, aquí tienes las diapositivas para la configuración del entorno de Vue en base a la información proporcionada:

---

# Configuración del Entorno de Vue

## Requisitos Previos

- Instalación de [Node.js](https://nodejs.org/) versión 16.0 o superior

## Iniciar un Nuevo Proyecto

Ejecuta el siguiente comando en tu terminal:

```sh
npm create vue@latest
```

Esto iniciará el proceso de creación de un nuevo proyecto Vue utilizando la herramienta oficial de generación.

---

##  Configuración del Proyecto

- Selecciona opciones como TypeScript, enrutador Vue y más.
  
<div class="language-sh"><pre><code><span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Project name: <span style="color:#888;">… <span style="color:#89DDFF;">&lt;</span><span style="color:#888;">your-project-name</span><span style="color:#89DDFF;">&gt;</span></span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add TypeScript? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add JSX Support? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add Vue Router for Single Page Application development? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add Pinia for state management? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add Vitest for Unit testing? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add an End-to-End Testing Solution? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Cypress / Playwright</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add ESLint for code quality? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add Prettier for code formatting? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span></span>
<span style="color:#A6ACCD;">Scaffolding project in ./<span style="color:#89DDFF;">&lt;</span><span style="color:#888;">your-project-name</span><span style="color:#89DDFF;">&gt;</span>...</span>
<span style="color:#A6ACCD;">Done.</span></code></pre></div>

---

##  Instalación de Dependencias

Navega al directorio de tu proyecto y ejecuta:

```sh
cd <nombre-del-proyecto>
npm install
```
```sh
cd <nombre-del-proyecto>
yarn install
```

Esto instalará las dependencias necesarias para tu aplicación Vue.


## Iniciar el Servidor de Desarrollo

Ejecuta el siguiente comando para iniciar el servidor de desarrollo:

```sh
npm run dev
```

```sh
yarn dev
```


Esto iniciará el servidor y mostrará la dirección en la que puedes ver tu aplicación en el navegador.


---
layout: center
class: text-center
---

# Creación de la Interfaz de Usuario

---

# Introducción a Vue.js y Vue 3

- **Vue.js**: Un framework progresivo para construir interfaces de usuario.
- **Vue 3**: La última versión de Vue con mejoras de rendimiento y nuevas características.
- Comprender componentes, directivas y reactividad.

---

# Creación de Componentes Interactivos

1. **Componentes**: Bloques de construcción reutilizables en Vue.
2. **Directivas**: Instrucciones especiales en la sintaxis de HTML.
3. **Eventos**: Manejo de interacciones del usuario.
4. **Data Binding**: Enlace bidireccional entre datos y vista.

---

# Integración de Datos desde Contratos en la Interfaz

1. Usar Ethers para interactuar con contratos inteligentes.
2. Leer datos del contrato en la interfaz:
   - Obtener información de propiedades y métodos del contrato.
3. Actualizar la interfaz con los datos obtenidos.

---

# Ejemplo: Creación de Componentes Interactivos

```vue
<template>
  <div>
    <h1>{{ message }}</h1>
    <button @click="increaseCount">Incrementar</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "Contador: 0",
      count: 0,
    };
  },
  methods: {
    increaseCount() {
      this.count++;
      this.message = "Contador: " + this.count;
    },
  },
};
</script>
```

---

# Prueba de la Interfaz de Usuario

1. Crear componentes Vue para interactuar con contratos.
2. Usar Vue Devtools para depurar y verificar el estado.
3. Probar la interacción con contratos en la interfaz.

---

## Ejemplo: Integración de Datos desde Contratos en la Interfaz

### Configuración de Ethers

```vue
<script lang="ts" setup>
import { onMounted, ref } from 'vue'
import { type AbstractProvider, ethers, type Signer } from 'ethers'

let signer: Signer | null = null
let provider: AbstractProvider | null = null

onMounted(async () => {
  // More info on: https://docs.ethers.org/v6/getting-started/#starting-connecting
  if (window.ethereum == null) {
    provider = ethers.getDefaultProvider('sepolia', {
      infura: '<infura-key>'
    })
  } else {
    const browserProvider = new ethers.BrowserProvider(window.ethereum)
    provider = browserProvider
    signer = await browserProvider.getSigner()
  }
})

</script>
```

---

### Lectura de Datos desde Contratos

```typescript
// ...
import SimpleStorage from './assets/SimpleStorage.json'

// ...
const contractAddress = '<dirección del contrato>'
const getNumber = ref('0')

async function numberGet() {
  try {
    const contract = new ethers.Contract(contractAddress, SimpleStorage.abi, provider)
    const result = await contract.get()
    getNumber.value = result.toString()
  } catch (error) {
    console.error('Error al obtener el número:', error)
  }
}
```

---

### Interfaz de Usuario para Lectura

```vue
<template>
  <div class="card">
    <h2 class="subtitle">Obtener tu uint256</h2>
    <form class="form" @submit.prevent="numberGet">
      <button class="button" type="submit">Obtener</button>
      <label>
        Tu uint256:
        <input class="input" type="text" v-model="getNumber" readonly />
      </label>
    </form>
  </div>
</template>
```

---

### Estilos

```css
<style>
.card {
  max-width: 500px;
  min-height: 50vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.form {
  height: 20vh;
  display: flex;
  justify-content: space-evenly;
  flex-direction: column;
}
.button {
  background-color: #00d1b2;
  border: none;
  border-radius: 5px;
  color: white;
  font-weight: bold;
  cursor: pointer;
  width: 100%;
}
</style>
```

---

### Escritura de Datos en Contratos

```typescript
// ...

const number = ref(0)
async function numberSet() {
  try {
    const contract = new ethers.Contract(contractAddress, SimpleStorage.abi, signer)
    const transaction = await contract.set(number.value)
    await transaction.wait()
    // Update state or show success message
  } catch (error) {
    console.error('Error setting number:', error)
  }
}
```

---

# Interfaz de Usuario para la Escritura

```html
 <div class="card">
    <h2 class="subtitle">Establecer tu uint256</h2>
    <form class="form" @submit.prevent="numberSet">
      <label>
        Establece tu uint256:
        <input class="input" type="text" v-model="number" />
      </label>
      <button class="button" type="submit">Confirmar</button>
    </form>
    <br />
 <!-- ... -->
</div>
```

---
layout: center
---
# Creación de contrato para un NFT's

---

### Importación y Herencia de Contratos

En esta parte, estamos importando los contratos necesarios de la librería OpenZeppelin. El contrato `AiverseNFT` hereda de `ERC721`, `ERC721Enumerable` y `ERC721URIStorage`, que forman parte del estándar ERC-721. También hereda de `Ownable` para manejar funcionalidades relacionadas con la propiedad.

```solidity
import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/token/ERC721/extensions/ERC721Enumerable.sol";
import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
import "@openzeppelin/contracts/utils/Counters.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract AiverseNFT is ERC721, ERC721Enumerable, ERC721URIStorage, Ownable {
    // ...
}
```

---

### Contadores y Estructura de Token

Aquí, utilizamos la librería `Counters` para gestionar los ID de los tokens. La estructura `Token` contiene información sobre un token, incluido su ID, `tokenURI` (URL de metadatos) y la dirección del propietario.

```solidity
using Counters for Counters.Counter;
Counters.Counter private _tokenIds;

struct Token {
    uint256 tokenId;
    string tokenURI;
    address owner;
}
```

---

### Constructor

El constructor establece el nombre y el símbolo para el contrato NFT. Cuando despleguemos el contrato, estos valores se configurarán.

```solidity
constructor() ERC721("Aiverse NFT", "NFT") {}
```


### Función `safeMint` para Crear Nuevos Tokens

La función `safeMint` se utiliza para crear un nuevo NFT. Incrementa el ID del token, crea el NFT en la dirección del destinatario y establece el `tokenURI`.

```solidity
function safeMint(address recipient, string memory _tokenURI) public returns (uint256) {
    _tokenIds.increment();

    uint256 newItemId = _tokenIds.current();
    _safeMint(recipient, newItemId);
    _setTokenURI(newItemId, _tokenURI);

    return newItemId;
}
```

---

### Hook `beforeTokenTransfer`

Este hook se ejecuta antes de cualquier transferencia de tokens para manejar cualquier lógica personalizada.

```solidity
function _beforeTokenTransfer(address from, address to, uint256 firstTokenId, uint256 batchSize) internal override(ERC721, ERC721Enumerable) {
    super._beforeTokenTransfer(from, to, firstTokenId, batchSize);
}
```

### Función `tokenURI`

La función `tokenURI` devuelve la URI de metadatos asociada con un token.

```solidity
function tokenURI(uint256 tokenId) public view override(ERC721, ERC721URIStorage) returns (string memory) {
    return super.tokenURI(tokenId);
}
```

---

### Función `getTokensByOwner`

La función `getTokensByOwner` recupera una lista de tokens de un propietario específico.

```solidity
function getTokensByOwner(address owner) public view returns (Token[] memory) {
    uint256 balance = balanceOf(owner);
    Token[] memory tokens = new Token[](balance);

    for (uint256 i = 0; i < balance; i++) {
        uint256 tokenId = tokenOfOwnerByIndex(owner, i);
        string memory _tokenURI = tokenURI(tokenId);
        tokens[i] = Token(tokenId, _tokenURI, owner);
    }

    return tokens;
}
```

### Función `getTokenById`

La función `getTokenById` recupera información del token mediante su ID.

```solidity
function getTokenById(uint256 tokenId) public view returns (Token memory) {
    address owner = ownerOf(tokenId);
    string memory _tokenURI = tokenURI(tokenId);
    return Token(tokenId, _tokenURI, owner);
}
```

### Función `supportsInterface`

La función `supportsInterface` verifica si un contrato admite una interfaz específica.

```solidity
function supportsInterface(bytes4 interfaceId) public view override(ERC721, ERC721Enumerable, ERC721URIStorage) returns (bool) {
    return super.supportsInterface(interfaceId);
}
```

### Función `_burn` para Quemar Tokens

La función `_burn` se llama cuando un token se quema (se destruye). Es responsable de limpiar los datos relacionados con el token quemado.

```solidity
function _burn(uint256 tokenId) internal override(ERC721, ERC721URIStorage) {
    super._burn(tokenId);
}
```

---

```solidity
contract AiverseNFT is ERC721, ERC721Enumerable, ERC721URIStorage, Ownable {
    using Counters for Counters.Counter;
    Counters.Counter private _tokenIds;
    struct Token {
        // ..
    }
    constructor() ERC721("Aiverse NFT", "NFT") {}
    function safeMint(address recipient, string memory _tokenURI) public returns (uint256) {
        // ...
    }
    function getTokensByOwner(address owner) public view returns (Token[] memory) {
        // ...
    }
    function getTokenById(uint256 tokenId) public view returns (Token memory) {
        // ...
    }
    function tokenURI(uint256 tokenId) public view override(ERC721, ERC721URIStorage) returns (string memory) {
        return super.tokenURI(tokenId);
    }
    function _beforeTokenTransfer(address from, address to, uint256 firstTokenId, uint256 batchSize) internal override(ERC721, ERC721Enumerable) {
        super._beforeTokenTransfer(from, to, firstTokenId, batchSize);
    }
    function _burn(uint256 tokenId) internal override(ERC721, ERC721URIStorage) {
        super._burn(tokenId);
    }
    function supportsInterface(bytes4 interfaceId) public view override(ERC721, ERC721Enumerable, ERC721URIStorage) returns (bool) {
        return super.supportsInterface(interfaceId);
    }

}
```