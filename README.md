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


#### crear un guard (para proteger las rutas de la pagina)

Existen 4 tipos:
* CanActivate: Mira si el usuario puede acceder a una página determinada.

* CanActivateChild: Mira si el usuario puede acceder a las páginas hijas de una determinada ruta.

* CanDeactivate: Mira si el usuario puede salir de una página, es decir, podemos hacer que aparezca un mensaje, por ejemplo, de comfirmación, si el usuario tiene cambios sin guardar.

* CanLoad: Sirve para evitar que la aplicación cargue los módulos perezosamente si el usuario no está autorizado a hacerlo.

```
ng g g  services/guards/loginGuard
```


<br/>

#### error con el .map
instalamos
```
npm i rxjs-compat --save-dev
```
E importarlo como a continuación

```
import 'rxjs/Rx';
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

#### Usando local storage

El storage es como una memoria cache del navegador.

* Para guardar

```
localStorage.removeItem('id');
```

* Para eliminar todo de localstorage

```
localStorage.clear();
```

* Para eliminar un item

```
localStorage.setItem('id', resp.id);
```

* En local storage solo se guarda texto, es decir un objecto no se puede guardar, se debe primero convertir en string

```
localStorage.setItem('id', JSON.stringfy(resp.user));
```

<br/>

#### Como redireccionar a otra pagina (navegar hacia otra pagina)
Podremos usar Router Link dentro del componente Html

```
[routerLink]="['/sheetmusic','allartists']
```

<br/>

#### Bibliografia

https://ronaldl337.wordpress.com/2018/08/22/programando-en-angular-tutorial-1/

<br/>

https://codingpotions.com/angular-seguridad
