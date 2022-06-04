# Pruebas a la API del navegador
En este escenario se observa que pasa si estamos consumiendo una API  del navegador como geolocalization hacer mock y ver que pasa

En estos casos de librerias que no vienen como inyección de dependencias se podría tener una dificultad de hacer mocking de estas librerias.

creamos un servicio nuevo para incorporar el servicio de geolocation

```
ng g s services/maps
```

y en el servicio de maps ingresamos el código para obtener la geolocalización y recibir parametros

maps.service.ts
```ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class MapsService {

  center = {lat: 0, lng: 0};
  constructor() { }

  getCurrentPosition() {
    navigator.geolocation.getCurrentPosition((response) => {
      const { latitude, longitude } = response.coords;
      this.center = {lat: latitude, lng: longitude}
    });
  }
}
```

Para las pruebas debemos enviar parametros propios de la geolocation y enviarlos a prueba haciendo spy directamente

maps.service.spec.ts
```ts
import { TestBed } from '@angular/core/testing';
import { MapsService } from './maps.service';

describe('MapsService', () => {
  let mapService: MapsService;

  beforeEach(() => {
    TestBed.configureTestingModule({
      providers: [ MapsService ]
    });
    mapService = TestBed.inject(MapsService);
  });

  it('should be created', () => {
    expect(mapService).toBeTruthy();
  });

  describe('test for getCurrentPosition', () => {
    it('should save the center position', () => {
      //Arrange
      spyOn(navigator.geolocation, 'getCurrentPosition').and.callFake((successFn) => {
        const mockGeolocation = {
          coords: {
            accuracy: 0,
            altitude: 0,
            altitudeAccuracy: 0,
            heading: 0,
            latitude: 1000,
            longitude: 2000,
            speed: 0
          },
          timestamp: 0,
        };
        successFn(mockGeolocation);
      });
      // Act
      mapService.getCurrentPosition();
      // Assert
      expect(mapService.center.lat).toEqual(1000);
      expect(mapService.center.lng).toEqual(2000);
    });
  });
});
```