# Aplicativos JavaScript com Node.js
## Módulo fs
- Abreviação de **sistemas de arquivos**
### Incluir em seu projeto
- `promisses`
- `async`
```js
const fs = require("fs").promises;
```
### Listar conteúdo de um diretório
- `readdir`
- `readdirsync`
```js
📂 stores
  📄 sales.json
  📄 totals.txt
  📂 201
  📂 202
```
### Leitura de conteúdo de uma pasta
```js
const items = await fs.readdir("stores");
console.log(items); // [ 201, 202, sales.json, totals.txt ]
```
- Matriz de cadeias de caracteres
  - Opção `withFileTypes`
    - Objeto `Dirent`
    - Métodos `isFile` e `isDirectory`
  ```js
  const items = await fs.readdir("stores", { withFileTypes: true });
  for (let item of items) {
  const type = item.isDirectory() ? "folder" : "file";
  console.log(`${item.name}: ${type}`);
  }
  // 201: folder, 202: folder, sales.json: file, totals.txt: file
  
  ```
### Recursão
- Quando um método chama a si mesmo
  - Pastas e subpastas
  - Programa para localizar arquivos
  - Determinar se é uma pasta
  - Pesquisar arquivos nela
  - Repetir tarefa
    - Chamando a si mesmo
  ```js
  function findFiles(folderName) {
  const items = await fs.readdir(folderName, { withFileTypes: true });
  items.forEach((item) => {
    if (item.isDirectory()) {
      // this is a folder, so call this method again and pass in
      // the path to the folder
      findFiles(`${folderName}/${item.name}`);
    } else {
      console.log(`Found file: ${item.name} in folder: ${folderName}`);
    }
  });
  }

  findFiles("stores"); 
  ```
### Determinar diretório atual
- Constante `__dirname`
  ```js
  console.log(__dirname);
  ```
- Caminho para executar o código
    - O valor `_dirname` será `/stores/201/sales`
      ```js
      📂 stores
      📂 201
          📂 sales
      ```
### Trabalhar com caminhos
## Módulo path
  - Para trabalhar com caminhos
    ```js
    const path = require("path");
    ```

🚧 Continuação em Breve... 🚧