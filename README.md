### **Recommended Plugin**
Nos permitiran tener una configuracion homogenia,sin importar el editor que usemos.
- ESLint
- Prettier
- EditorConfig
### **Basic Comand**
```
$node --version
#install toolkits for nestJS
$npm i -g @nestjs/cli
#installation verification of nestJS
$nest --version
#show all the comands of nestJS
$nest --help

#Create a new Project
$nest new  nameProject

#run project in devep mode
npm run start:dev
```

- Crear un archivo `.editorconfig`:
El cual nos permitira tener todos la misma configuracion sin inportar el editor de codigo.
```
# Editor configuration, see https://editorconfig.org
root = true

[*]
charset = utf-8
indent_style = space
indent_size = 2
insert_final_newline = true
trim_trailing_whitespace = true

[*.ts]
quote_type = single

[*.md]
max_line_length = off
trim_trailing_whitespace = false
```
- El file `src/main.ts`: Es el que se encarga de correr la aplicacion.

### **Recap TypeScript**
```
class Person {
  // private age;
  // private name;
  #builder
  // constructor(age: number, name: string) {
  //   this.age = age;
  //   this.name = name;
  // }
  #builder contraction: aqui se declara y se asigna los valores para el constructor
  constructor(public age:number,private name:string){}

  getSummary() {
    return `my name is ${this.name}, ${this.age}`;
  }
}

const nicolas= new Person(26,'Nicolas Enrique');
nicolas.getSummary();


```
### **Decoradores**
Le dice a nest como una clase de typeScrip como se deberia comportar respecto al framework.

- `@Controller()`: Se define que una clase actue como controller.
- `@Get('nuevo-endpoint')`: Para crear endpoints
- `@Params`: Para obtener parámetros de la URL usas el decorador.
### **Crear enpoits**
- Tip: utilizar plurales para los nombres de los endpoits.Ejemplo:
    - api.example.con/tasks/
    - api.example.con/users/

```
@Get('nameRoots')
newEndpoint(){
    return 'Hello Peru'
}
```
### **Obtener Parametros de URL**
- debemos importar  `import { Controller, Get, Param } from '@nestjs/common
```
#obtener un solo parametro
@Get('products/:productId')
  getProduct(@Param('productId') productId: string) {
    return `product ${productId}`;
  }

#obteniendo 2 parametros
  @Get('categories/:id/products/:productId')
  getCategory(@Param('productId') productId: string, @Param('id') id: string) {
    return `product ${productId} and ${id}`;
  }
```