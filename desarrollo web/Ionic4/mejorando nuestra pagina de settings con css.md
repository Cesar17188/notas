# Mejorando nuestra página de Settings con CSS

settings.page.html
```html
<ion-header>
  <ion-toolbar>
    <ion-title>settings</ion-title>
    <ion-buttons slot="end">
      <ion-menu-button></ion-menu-button>
    </ion-buttons>
  </ion-toolbar>
</ion-header>

<ion-content class="ion-text-center ion-padding">
  <div class="success-background">
    <ion-avatar (click)="takePhoto()">
      <img [src]="userImage" alt="" *ngIf="!photo">
      <img [src]="photo" alt="" *ngIf="photo">
    </ion-avatar>
    <h1>Cesar Armendariz</h1>
    <h2>cesareli17188@gmail.com</h2>
    <ion-grid>
      <ion-row class="ion-items-center ion-text-center row-header">
        <ion-col>140</ion-col>
        <ion-col>2k</ion-col>
        <ion-col>500</ion-col>
      </ion-row>
      <ion-row class="ion-items-center ion-text-center">
        <ion-col>Artistas</ion-col>
        <ion-col>Seguidores</ion-col>
        <ion-col>Canciones</ion-col>
      </ion-row>
    </ion-grid>
  </div>
</ion-content>
```

settings.page.scss
```scss
ion-avatar {
  text-align: center;
  margin: 0 auto;
  width: 100px;
  height: 100px;
  margin-top: 16px;
}

.row-header {
  font-size: 32px;
  font-weight: bold;
}

.success-background {
  background-color: var(--ion-color-success);
  color: var(--ion-color-dark);
  padding-bottom: 32px;
  h1 {
    margin: 0;
  }
  h2 {
    margin: 0;
    font-size: 16px;
    margin-bottom: 32px;
  }
}
```