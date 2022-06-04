# Página Sports y Angular Maps

primero instalamos la librería necesaria, ya que angular maps no esta actualizada y no se puede utilizar momentaneamente se recomienda instalar

```
npm install --save @types/googlemaps
```

posteriormente se importa el modulo de google maps en nuestro app.module.ts

app.module.ts
```ts
import { GoogleMapsModule } from '@angular/google-maps';

@NgModule({
  declarations: [AppComponent],
  entryComponents: [],
  imports: [
    GoogleMapsModule,
  ],
  providers: [{ provide: RouteReuseStrategy, useClass: IonicRouteStrategy }],
  bootstrap: [AppComponent],
})
```

posteriormente en tu index.html se pega el siguiente script, cambiando el YOUR_API_KEY por tu clave de activación de la API de google maps

index.html
```html
  <script async defer src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap"></script>
```


posteriormente en tu sports page se haran los siguientes cambios

sports.module.ts
```ts
import { GoogleMapsModule } from '@angular/google-maps';

@NgModule({
  imports: [
    GoogleMapsModule,
  ],
  declarations: [SportsPage]
})
```

sport.page.html
```html
<ion-content>
  <google-map></google-map>
</ion-content>
```