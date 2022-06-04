# Pruebas maliciosas para GET

 En las pruebas no es simplemente seguir el camino feliz o (happy path) sino tambien hacer las pruebas poniendo distintos parámetros.

Por ejemplo en el caso de pruebas en el product service se puede intentar mandar precios de la lista de productos en 0 o en negativa y verificar lo que debería devolver, e incluso hay que enviar parametros de limit y offset para verificar su funcionalidad.

product.service.spec.ts
```ts
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
        {
          ...generateOneProduct(),
          price: 0, //0 * .19 = 0
        },
        {
          ...generateOneProduct(),
          price: -100, // = 0
        },
      ];
      //Act
      productsService.getAll()
      .subscribe((data) => {
        //Assert
        expect(data.length).toEqual(mockData.length);
        expect(data[0].taxes).toEqual(19);
        expect(data[1].taxes).toEqual(38);
        expect(data[2].taxes).toEqual(0);
        expect(data[3].taxes).toEqual(0);
        doneFn();
      });
       //http config
       const url = `${environment.API_URL}/api/v1/products`;
       const req = httpController.expectOne(url);
       req.flush(mockData);
       httpController.verify();
    });

    it('should send query params width limit 10 offset 3', (doneFn) => {
      //Arrange
      const mockData: Product[] = generateManyProducts(3);
      const limit = 10;
      const offset = 3;
      //Act
      productsService.getAll(limit, offset)
      .subscribe((data) => {
        //Assert
        expect(data.length).toEqual(mockData.length);
        doneFn();
      });
      //http config
      const url = `${environment.API_URL}/api/v1/products?limit=${limit}&offset=${offset}`;
      const req = httpController.expectOne(url);
      req.flush(mockData);
      const params = req.request.params;
      expect(params.get('limit')).toEqual(`${limit}`);
      expect(params.get('offset')).toEqual(`${offset}`);
      httpController.verify();
    });
  });
```

si hay que cambiar algo en el código del servicio se lo puede hacer

product.service.ts
``` ts
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
          taxes: item.price > 0 ? .19 * item.price : 0
        }
      }))
    );
  }
```