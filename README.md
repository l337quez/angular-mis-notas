### Angular, mis notas
Angular por defecto usa http://localhost:4200/ 

<br/>

#### Ayuda en angular
```
ng help
```
<br/>

#### Crear un proyecto
```
ng new nombre_del_proyecto
```
<br/>

#### Compartir un proyecto
usuarlmente se comaparte el proyecto menos la carpeta node_modules, ya que esta carpeta tiene muchisimos archivos y dura en copiar, entoncesla otra persona deber ejecutar el siguiente comando para instalar todas las dependencias
```
npm install
```

<br/>

#### Ejecutar el proyecto
abimos la terminal y debemos pararnos dentro del proyecto
```
ng serve
```
Si queremos que se abra el navegador con la ip y el puerto con la que trabajamos hacemos esto. 
```
ng serve -o
```

<br/>


#### crear un componente

```
ng g c nombre_del_componente
```

<br/>


#### crear un modulo
Para organizar el proyecto, creamos modulos, en resumida un modulo es una carpeta donde adentro habran otros modulos..
```
ng g m nombre_del_modulo
```

<br/>


#### Para interactuar con el Backend necesitamos el httpclient
debemos en importar el modulo en los imports

```
import { HttpClientModule } from '@angular/common/http';
imports: [
    HttpClientModule
  ]
```

<br/>

https://ronaldl337.wordpress.com/2018/08/22/programando-en-angular-tutorial-1/
