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

#### crear un Servicio
los servicios deben ser usados para procesar algo y los componentes nunca deberían guardar datos ni presentar datos falsos...
```
ng g s services/user
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

#### Enviar el token por el header
Si bien podremos crear un servicio para interceptar la peticion http y agregar el token o si ya tenemos el servicio
por ejemplo user agregamos el observable que se encuentra en el codigo he importamos lo requerido. cambie el nombre
auth_token por el nombre del token que tienes en localstorage, es importante estar guardando el token en el 
localstorage cuando se esta logiando para poder hacer este procedimiento.

mas informacion aqui https://amoelcodigo.com/interceptor-angular/

creamos un servicio

```
ng g s services/authInterceptor/authInterceptor
```

Agregamos el siguiente codigo dentro del servicios que acabamos de crear

```
import { Injectable } from '@angular/core';
import { HttpEvent, HttpHandler, HttpInterceptor, HttpRequest } from '@angular/common/http';
import { Observable } from 'rxjs';
@Injectable()
export class AuthInterceptor implements HttpInterceptor {
intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
    const token = localStorage.getItem('auth_token');
if (!token) {
      return next.handle(req);
    }
const headers = req.clone({
      headers: req.headers.set('Authorization', `Bearer ${token}`)
    });
return next.handle(headers);
  }
}
```
si solo vas a implementar el observable seguramente debras importar solo esto

```
import { HttpEvent, HttpHandler, HttpInterceptor, HttpRequest } from '@angular/common/http';
import { Observable } from 'rxjs';
```
Exportar el servicio a los modulos donde se va usar. En appModule debes agregar esto en el provider

```
  providers: [
    {
      provide: HTTP_INTERCEPTORS,
      useClass: AuthInterceptorService,
      multi: true
    }
  ]
  ```

<br/>

#### Como redireccionar a otra pagina (navegar hacia otra pagina)
Podremos usar Router Link dentro del componente Html

```
[routerLink]="['/sheetmusic','allartists']
```

<br/>

#### Enviar datos a un Modal

instalamos 

```
npm install @ng-bootstrap/ng-bootstrap --save
```


importamos en el modulo del componenete que estamos usando ReacticeFormsModule y lo agregamos en 
el array de import. Ejm: si su componente esta dentro de el modulo pages.modulo, entonces en pages  
modulo es que debes importar el ReactiveFormsModule y FormsModule

```
import { ReactiveFormsModule, FormsModule } from '@angular/forms';

```

ahora instalamos

```
npm install bootstrap --save
```

Ahora nos vamos al archivo "angular.json" e importamos a bootstrap

```
"styles": [
  "src/styles.css",
  "node_modules/bootstrap/dist/css/bootstrap.min.css"
]
```

El modal lo introduciomos dentro de esto

```
    <ng-template #editProfileModal let-modal></ng-template>
```

Agregamos  un form dentro de la clase "modal-body" del modal

```
<form [formGroup]="editProfileForm" (ngSubmit)="onSubmit()" >  </form>

```

Importamos en el App module

import { NgbModule } from '@ng-bootstrap/ng-bootstrap';



Mas informacion aqui: https://levelup.gitconnected.com/pass-data-into-ng-bootstrap-modal-in-angular-8-65608361093a

<br/>

#### Generar la carpeta Dist


```
ng build
```

<br/>


#### Bibliografia

https://ronaldl337.wordpress.com/2018/08/22/programando-en-angular-tutorial-1/

<br/>

https://codingpotions.com/angular-seguridad
