# Crear la página Sport

vamos a hacer cambios en nuestro sports page utilizando la librería google-maps

sports.page.ts
```ts
import { Component } from '@angular/core';
import { Geolocation } from '@capacitor/geolocation';

@Component({
  selector: 'app-sports',
  templateUrl: './sports.page.html',
  styleUrls: ['./sports.page.scss'],
})

export class SportsPage {
  currentCenter: any;
  coordinates: google.maps.LatLngLiteral[] = [];
  defaultZoom = 14;
  center: google.maps.LatLngLiteral;
  
  constructor() { }

  ionViewDidEnter() {
    this.getCurrentPosition();
    this.watchPosition();
  }

  async getCurrentPosition() {
    const coordinates = await Geolocation.getCurrentPosition();
    this.currentCenter = {
      lat: coordinates.coords.latitude,
      lng: coordinates.coords.longitude
    };
    this.center = {
      lat: coordinates.coords.latitude,
      lng: coordinates.coords.longitude
    };
  }

  watchPosition() {
    Geolocation.watchPosition({}, position=> {
      this.center = {
        lat: position.coords.latitude,
        lng: position.coords.longitude
      };
      this.coordinates.push ({
        lat: position.coords.latitude,
        lng: position.coords.longitude
      });
    });
  }
}
```

sports.page.html
```html
<ion-header>
  <ion-toolbar>
    <ion-title>sports</ion-title>
    <ion-buttons slot="end">
      <ion-menu-button></ion-menu-button>
    </ion-buttons>
  </ion-toolbar>
</ion-header>

<ion-content>
  <google-map *ngIf="currentCenter"
  [center]="center"
  [zoom]="defaultZoom">
  <map-marker
  [position]="center"
  icon = 'assets/img/bicycle.png'></map-marker>
  <map-polyline *ngIf="coordinates"
    strokeColor='red' [path]="coordinates">
  </map-polyline>
  </google-map>
</ion-content>
```