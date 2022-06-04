# Envío del formulario

Envío del formulario

etiqueta para footer de ionic,  
ion-footer  
Lo vamos a usar para registrar  
centramos y expandimos, agregamos un outline, round  
La agregamos después de </ion-content>

login.page.html
```html
<ion-button 
  expand="full" 
  shape="round" 
  fill="outline" 
  color="success">Click para Registrarse
</ion-button>
```

Antes de cerrar el formulario agregamos un ion-button de login, similar al de registrarse pero sin el outline. Le indicamos a qué formulario pertenece y en qué caso estará habilitado o no. Le indicamos el type.

login.page.html
```html
<ion-button 
    expand="full" 
    shape="round"  
    color="success"
    [disabled]="!loginForm.valid"
    type="submit"
    >Login</ion-button>
```

Completamos la función loginUser en nuestro componente.  
Recibe las credenciales del usuario y las logueamos en consola.

login.page.ts
```ts
loginUser(credentials){
    console.log(credentials);
  }
```