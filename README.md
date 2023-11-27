# Proyecto TypeScript con Jest

Este es un proyecto base de TypeScript configurado con Jest.
**Nota** Cuando se transpila de TS a JS, ES6 no detecta los imports de otros archivos.
La solución seria añadir la extension .js en las importaciones de archivos TS para que cuando se haga la transpilacion se mantenga la extension y el codigo funcione o utilizar webpack con la configuracion adecuada.<br>
**Atención:** Crear carpeta /dist en la raiz del proyecto para evitar error de tsconfig.

---

---

## Instrucciones para crear el mismo proyecto desde 0

- Crear el archivo `package.json`

```bash
npm init -y
```

- Instalar las dependencias

```bash
npm install typescript ts-node jest ts-jest @types/jest --save-dev
```

- Crear archivo `tsconfig.json`

```bash
npx tsc --init
```

## Scripts

Incluir scripts y configuracion del type en el archivo `package.json`:

```json
"type": "module",

"scripts": {
    "build": "tsc && npm run remove-tests-folder",
    "remove-tests-folder": "rm -rf dist/__tests__",
    "build:watch": "tsc --build tsconfig.json --watch",
    "test": "jest --coverage",
    "test:watch": "jest --coverage --watchAll",
}
```

## Configuracion de Jest

Crear un archivo `jest.config.cjs` con la siguiente configuración para Jest:
**Nota:** Hay que utilizar la extensión .cjs para evitar errores.

```javascript
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'node',
  testRegex: '(/__tests__/.*|(\\.|/)(test|spec))\\.(jsx?|tsx?)$',
  moduleFileExtensions: ['ts', 'tsx', 'js', 'jsx', 'json', 'node'],
};
```

## Configuración de TypeScript

Hay que editar el archivo tsconfig.json con la siguiente configuración:

```json
{
  "compilerOptions": {
    /* Language and Environment */
    "target": "ES6",
    "module": "ESNext",
    "rootDir": "./src",
    "types": ["node", "jest"],
    /* Emit */
    "outDir": "./dist",
    /* Interop Constraints */
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    /* Type Checking */
    "strict": true,
    /* Completeness */
    "skipLibCheck": true
  },
  "include": ["./src/**/*.ts", "!./src/__tests__/**/*"],
  "ts-node": {
    "esm": true
  }
}
```
