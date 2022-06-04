# Pruebas para POST

Ahora veremos pruebas en post, put y delete.

product.service.spec.ts
```ts
afterEach(() => {
    httpController.verify();
  });
  
 describe('test for create', () => {
      it('should return a new product', (doneFn) => {
        // Arrange
        const mockData = generateOneProduct();
        const dto: CreateProductDTO = {
          title: 'new Product',
          price: 100,
          images: ['img'],
          description: 'bla bla bla',
          categoryId: 12,
        };
        // Act
        productsService.create({...dto}).subscribe((data) => {
          // Assert
          expect(data).toEqual(mockData);
          doneFn();
        });
        //http config
        const url = `${environment.API_URL}/api/v1/products`;
        const req = httpController.expectOne(url);
        req.flush(mockData);
        expect(req.request.body).toEqual(dto);
        expect(req.request.method).toEqual('POST');
      });
  });

    describe('test for update', () => {
      it('should return an updated product', (doneFn) => {
        // Arrange
        const mockData = generateOneProduct();
        const id = '1';
        const dto: UpdateProductDTO = {
          title: 'update Product',
          price: 200,
          images: ['img'],
          description: 'bla bla bla bla',
          categoryId: 12,
        };
        // Act
        productsService.update(id, {...dto}).subscribe((data) => {
          // Assert
          expect(data).toEqual(mockData);
          doneFn();
        });
        //http config
        const url = `${environment.API_URL}/api/v1/products/${id}`;
        const req = httpController.expectOne(url);
        req.flush(mockData);
        expect(req.request.body).toEqual(dto);
        expect(req.request.method).toEqual('PUT');
      });
  });

    describe('test for delete', () => {
      it('should delete a product', (doneFn) => {
        // Arrange
        const id = '1';
        // Act
        productsService.delete(id).subscribe((data) => {
          // Assert
          expect(data).toBe(true);
          doneFn();
        });
        //http config
        const url = `${environment.API_URL}/api/v1/products/${id}`;
        const req = httpController.expectOne(url);
        req.flush(true);
        expect(req.request.method).toEqual('DELETE');
      });
  });
```