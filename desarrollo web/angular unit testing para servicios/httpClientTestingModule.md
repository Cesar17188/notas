# HttpClientTestingModule

Debido a que Angular puede conectarse a API's desde sus herramientas, específicamente las de HttpClientModule tambien puede hacer testing desde otra herramienta llamada HttpClientTestingModule. 

Hay que tener en cuenta
El API funcionan desde el backend asi que no hay responsabilidad de frontend. Por lo que se hara mocking para hacer el testing a la funcionalidad de conexión. Ya que si hacemos prueba directas de conexión podemos causar bloqueos a la API.

lo primero sera crear el archivo de pruebas de product.service.ts y lo llamaremos product.service.spec.ts y lo modificaremos de la siguiente manera.

product.service.spec.ts
```ts
import { TestBed } from '@angular/core/testing';
import { HttpClientTestingModule, HttpTestingController } from '@angular/common/http/testing';

import { ProductsService } from './product.service';
import { Product } from '../models/product.model';
import { environment } from '../../environments/environment';

fdescribe('ProductsService', () => {
  let productsService: ProductsService;
  let httpController: HttpTestingController;

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        HttpClientTestingModule
      ],
      providers: [
        ProductsService
      ]
    });
    productsService = TestBed.inject(ProductsService);
    httpController = TestBed.inject(HttpTestingController);
  });
  
  it('should be create', () => {
    expect(productsService).toBeTruthy();
  });

  describe('tests for getAllSimple', () => {
    it('should return a product list', () => {
      //Arrange
      const mockData: Product[] = [
        {
          id: '123',
          title: 'title',
          price: 12,
          description: 'blablabla',
          category: {
            id: 112,
            name: 'as'
          },
          images: ['img', 'img']
        }
      ];
      //Act
      productsService.getAllSimple()
      .subscribe((data) => {
        //Assert
        expect(data.length).toEqual(mockData.length);
        //doneFn();
      });
      //http config
      const url = `${environment.API_URL}/api/v1/products`;
      const req = httpController.expectOne(url);
      req.flush(mockData);
      httpController.verify();
    });
  });
});
```