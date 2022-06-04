# Pruebas para GET

Vamos a enfocarnos a pruebas Get cuya parametros son más complejos

para lo cual se requieren cambios en product services en la función getAll

product.service.ts
```ts
getAll(limit?: number, offset?: number): Observable<Product[]> {
    let params = new HttpParams();
    if (limit && offset != null) {
      params = params.set('limit', limit);
      params = params.set('offset', offset);
    }
    return this.http.get<Product[]>(`${this.apiUrl}/products`, { params })
    .pipe(
      retry(3),
      map(products => products.map(item => {
        return {
          ...item,
          taxes: .19 * item.price
        }
      }))
    );
  }
```

ahora se puede poner a prueba todos los posibles resultados de getAll

product.service.spec.ts
```ts
 describe('tests for getAll', () => {
    it('should return a product list', (doneFn) => {
      //Arrange
      const mockData: Product[] = generateManyProducts(3);
      //Act
      productsService.getAll()
      .subscribe((data) => {
        //Assert
        expect(data.length).toEqual(mockData.length);
        doneFn();
      });
      //http config
      const url = `${environment.API_URL}/api/v1/products`;
      const req = httpController.expectOne(url);
      req.flush(mockData);
      httpController.verify();
    });
    it('should return product list width taxes', (doneFn) => {
      // Arrange
      const mockData: Product[] = [
        {
          ...generateOneProduct(),
          price: 100, //100 * .19 = 19  
        },
        {
          ...generateOneProduct(),
          price: 200, //200 * .19 = 38  
        },
      ];
      //Act
      productsService.getAll()
      .subscribe((data) => {
        //Assert
        expect(data.length).toEqual(mockData.length);
        expect(data[0].taxes).toEqual(19);
        expect(data[1].taxes).toEqual(38);
        doneFn();
      });
       //http config
       const url = `${environment.API_URL}/api/v1/products`;
       const req = httpController.expectOne(url);
       req.flush(mockData);
       httpController.verify();
    });
  });
```