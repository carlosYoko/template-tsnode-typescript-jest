# Proyecto TypeScript con Jest

Template basic de configuración TypeScript con Jest.

<br>
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

Crear un archivo `jest.config.json` con la siguiente configuración para Jest:

```json
{
  "transform": {
    "^.+\\.tsx?$": [
      "ts-jest",
      {
        "tsconfig": "./tsconfig.json",
        "module": "commonjs"
      }
    ]
  },
  "moduleFileExtensions": ["ts", "tsx", "js", "jsx", "json", "node"]
}
```

## Configuración de TypeScript

Hay que editar el archivo tsconfig.json con la siguiente configuración:

```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "commonjs",
    "sourceMap": true,
    "rootDir": "./src",
    "outDir": "./dist",
    "strict": true,
    "esModuleInterop": true,
    "noEmitOnError": false,
    "removeComments": true
  },
  "include": ["./src/**/*"],
  "exclude": ["node_modules", "dist", ".src/__tests__"]
}
```
