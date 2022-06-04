# Pruebas a errores
En estas pruebas veremos como se debe verificar cuando por ejemplo el servidor no esta funcionando bien y como reaccionar de manera correcta

```ts
it('should return a product', (doneFn) => {
      // Arrange
      const mockData: Product = generateOneProduct();
      const id = '1';
      // Act
      productsService.getOne(id).subscribe((data) => {
        // Assert
        expect(data).toEqual(mockData);
        doneFn();
      });
      //http config
      const url = `${environment.API_URL}/api/v1/products/${id}`;
      const req = httpController.expectOne(url);
      req.flush(mockData);
      expect(req.request.method).toEqual('GET');
    });

    it('should return the right msg when the status code is 404', (doneFn) => {
      // Arrange
      const id = '1';
      const msgError = '404 message';
      const mockError = {
        status: HttpStatusCode.NotFound,
        statusText: msgError,
      };
      // Act
      productsService.getOne(id).subscribe({
        error: (error) => {
          // assert
          expect(error).toEqual('El producto no existe');
          doneFn();
        },
      });
      //http config
      const url = `${environment.API_URL}/api/v1/products/${id}`;
      const req = httpController.expectOne(url);
      req.flush(msgError, mockError);
      expect(req.request.method).toEqual('GET');
    });

    it('should return the right msg when the status code is 409', (doneFn) => {
      // Arrange
      const id = '1';
      const msgError = '409 message';
      const mockError = {
        status: HttpStatusCode.Conflict,
        statusText: msgError,
      };
      // Act
      productsService.getOne(id).subscribe({
        error: (error) => {
          // assert
          expect(error).toEqual('Algo esta fallando en el server');
          doneFn();
        },
      });
      //http config
      const url = `${environment.API_URL}/api/v1/products/${id}`;
      const req = httpController.expectOne(url);
      req.flush(msgError, mockError);
      expect(req.request.method).toEqual('GET');
    });

    it('should return the right msg when the status code is 401', (doneFn) => {
      // Arrange
      const id = '1';
      const msgError = '409 message';
      const mockError = {
        status: HttpStatusCode.Unauthorized,
        statusText: msgError,
      };
      // Act
      productsService.getOne(id).subscribe({
        error: (error) => {
          // assert
          expect(error).toEqual('No estas permitido');
          doneFn();
        },
      });
      //http config
      const url = `${environment.API_URL}/api/v1/products/${id}`;
      const req = httpController.expectOne(url);
      req.flush(msgError, mockError);
      expect(req.request.method).toEqual('GET');
    });
  });
```