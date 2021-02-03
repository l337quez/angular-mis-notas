#### poner la mano para hacer click en un button
cuando se pierde la mano en un boton puedes usar la clase pointer, por ejemplo

```
<li>
    <a (click)="_userService.logout()" class= "pointer"><i class="zmdi zmdi-time-restore"></i> Cerrar sesion</a>
</li>
```

<br/>

Si no funciona, se puede agregar la clase en el styles. En el archivo principal de css de todo el proyecto

```
.pointer {
  cursor:  pointer;
}
```
