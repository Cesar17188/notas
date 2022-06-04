# Pruebas para PUT y DELETE

```ts
describe('test for update', () => {
      it('should return an updated product', (doneFn) => {
        // Arrange
        const mockData = generateOneProduct();
        const id = '1';
        const dto: UpdateProductDTO = {
          title: 'update Product'
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