# Crear un formulario


```html
<h1 class="form-title">Formulario</h1>
<form class="form" (ngSubmit)="onRegister()" #myForm="ngForm">
  <div></div>
  <div class="input-group">
    <label class="form-label" for="Nombre">Nombre</label>
    <input class="form-input" type="text" name="name" required id="name" #nameInput="ngModel" [(ngModel)]="register.name" placeholder="Cesar">
    <p class="message--error" [class.invalid]="nameInput.invalid">Campo requerido</p>
  </div>
  <div></div>
  <div></div>
  <div class="input-group">
    <label class="form-label" for="Email">Email</label>
    <input class="form-input" type="email" name="email" required id="email" #emailInput="ngModel" [(ngModel)]="register.email">
    <p class="message--error" [class.invalid]="emailInput.invalid">Campo requerido</p>
  </div>
  <div></div>
  <div></div>
  <div class="input-group">
    <label class="form-label" for="password">Password</label>
    <input class="form-input" type="password" name="password" required id="password" #passwordInput="ngModel" [(ngModel)]="register.password">
    <p  class="message--error" [class.invalid]="passwordInput.invalid">Campo requerido</p>
  </div>
  <div></div>
  <div></div>
  <div class="form-buttons">
    <button class="buttonSubmit" [disabled]="myForm.invalid" type="submit">Registrar</button>
    <button class="buttonAction" type="button">Accion</button>
  </div>
</form>
```

```scss
.form-title {
  display: flex;
  justify-content: center;
  color: darkgreen;
  font-size: 2.4rem;
  font-family: cursive;
  padding-bottom: 2rem;
}

.form {
  display: grid;
  grid-template-columns: 40px minmax(345px, 530px) 40px;
  grid-template-rows: repeat(5, auto);
}

.input-group {
  display: grid;
  justify-items: stretch;
  padding-bottom: 30px;

  .form-label {
    font-family: cursive;
    padding-bottom: 5px;
  }

  .form-input {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    box-sizing: border-box;
    border: 1.3px solid darkgreen;
    border-radius: 10px;
  }
}

.form-buttons {
  display: flex;
  margin: 10px;
  padding-bottom: 30px;
  justify-content: space-evenly;

  .buttonSubmit {
  font-size:15px;
  font-family:Arial;
  width:140px;
  height:50px;
  border-width:1px;
  color:#fff;
  border-color:#599bb3;
  font-weight:bold;
  border-top-left-radius:8px;
  border-top-right-radius:8px;
  border-bottom-left-radius:8px;
  border-bottom-right-radius:8px;
  box-shadow: 0px 10px 14px -7px #276873;
  text-shadow: 0px 1px 0px #3d768a;
  background:linear-gradient(#599bb3, #408c99);
  }

  .buttonSubmit:disabled {
    background: linear-gradient(27deg, rgba(0,0,0,1) 0%, rgba(195,190,183,1) 100%);
    background-color:transparent;
  }

  .buttonSubmit:hover {
    background: linear-gradient(#408c99, #599bb3);
  }

  .buttonAction {
    font-size:15px;
  font-family:Arial;
  width:140px;
  height:50px;
  border-width:1px;
  color:rgba(255, 255, 255, 1);
  border-color:#599bb3;
  font-weight:bold;
  border-top-left-radius:8px;
  border-top-right-radius:8px;
  border-bottom-left-radius:8px;
  border-bottom-right-radius:8px;
  box-shadow: 0px 10px 14px -7px #276873;
  text-shadow: 0px 1px 0px #3d768a;
  background:linear-gradient(rgba(121, 214, 217, 1), rgba(52, 198, 187, 1));
  }

  .buttonAction:hover {
    background: linear-gradient(rgba(52, 198, 187, 1), rgba(121, 214, 217, 1));
  }
}
.message--error {
  background-color: red;
  color: white;
  opacity: 0;
  transition: all linear .2s;
  &.invalid {
    opacity: 1;
  }
}

@media screen and (min-width: 400px) {
  .form {
    justify-content: center;
  }
}
```