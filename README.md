# Proyecto TypeScript con Jest

Este es un proyecto base de TypeScript configurado con Jest.
Incluye configuración CI con GitHub Actions.

---

---

## Instrucciones para crear el mismo proyecto desde 0

- Crear el archivo `package.json`

```bash
npm init -y
```

- Instalar las dependencias

```bash
npm install typescript ts-node jest @types/jest --save-dev
```

- Crar archivo `tsconfig.json`

```bash
npx tsc --init
```

## Scripts

Tener las siguientes configuraciones de scripts y el type en el `package.json`:

```json
"type": "module",

"scripts": {
    "build": "tsc",
    "build:watch": "tsc --build tsconfig.json --watch",
    "test": "jest --coverage",
    "start": "npx ts-node src/index.ts"
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
  "ts-node": {
    "esm": true
  }
}
```
