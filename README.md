# NODE CLI 


## Configuración
Crear el archivo package.json y un archivo de entrada index.js
- package.json
```
{
  "name": "outside-cli",
  "version": "1.0.0",
  "license": "MIT",
  "scripts": {},
  "devDependencies": {},
  "dependencies": {}
}
```
- index.js
```
module.exports = () => {
  console.log('Welcome to the outside!')
}
```
## Crear un archivo bin
Se necesitara una manera de invocar la aplicación creada, asi como agregarlo a la ruta del sistema para que pueda ser llamado desde cualquier lugar, esto se puede hacer con un archivo bin
  - bin/outside
  ```
  #!/usr/bin/env node
require('../')()
  ```
Tambien es necesario dar permisos de ejecución:
```
$ chmod +x bin/outside
```
Luego agregaremos la ruta del binario al archivo package.json, esto lo colocará automaticamente en la ruta del sistema del usuario cuando se instale el paquete como un paquete global.
- package.json
```
{
  "name": "outside-cli",
  "version": "1.0.0",
  "license": "MIT",
  "bin": {
    "outside": "bin/outside"
  },
  "scripts": {},
  "devDependencies": {},
  "dependencies": {}
}
```

```
$ npm install -g outside-cli
```

## Comandos y argumentos
Se instalara la primere dependencia llamada: minimist, esta será util para el manejo de los argumentos.
```
$ npm install --save minimist
```

## Indicadores de carga
Para esta aplicación no se puede medir el progreso ya que se estara haciendo solicitudes a una API externa, pero se utilizadara una rueda giratoria basica para darle feedback al usuario, para ello se utilizaran e instalaran las siguientes dependencias:

```
$ npm install --save axios ora
```
 ## Referencia
 https://timber.io/blog/creating-a-real-world-cli-app-with-node/#parsing-commands-and-arguments