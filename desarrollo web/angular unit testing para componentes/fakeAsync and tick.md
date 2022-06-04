# FakeAsync and tick

FakeAsync and tick son dos métodos de Angular para analizar ciertos escenarios que incluyen la participación de execution, observers, setTimeout, promises, funcionando de la siguiente manera

product.component.ts
```ts
getAllProducts() {
    this.status = 'loading';
    this.productsService.getAll(this.limit, this.offset)
    .subscribe({
      next: (products) => {
        this.products = [...this.products, ...products];
        this.offset += this.limit;
        this.status = 'success';
      },
      error: (error) => {
        setTimeout(() => {
          this.products = [];
          this.status = 'error';
        }, 3000);
      }
    });
  }
```

product.component.spec.ts
```ts
it('should change the status "loading" to "success"', fakeAsync(() => {
      // Arrange
      const productsMock = generateManyProducts(10);
      productService.getAll.and.returnValue(defer(() => Promise.resolve(productsMock)));
      // Act
      component.getAllProducts();
      fixture.detectChanges();
      expect(component.status).toEqual('loading');
      tick(); // exec, obs, setTimeout, promise
      fixture.detectChanges();
      // Assert
      expect(component.status).toEqual('success');
    }));


    it('should change the status "loading" to "error"', fakeAsync(() => {
      // Arrange
      const productsMock = generateManyProducts(10);
      productService.getAll.and.returnValue(defer(() => Promise.reject('error')));
      // Act
      component.getAllProducts();
      fixture.detectChanges();
      expect(component.status).toEqual('loading');
      tick(4000); // exec, obs, setTimeout, promise
      fixture.detectChanges();
      // Assert
      expect(component.status).toEqual('error');

    }));
```