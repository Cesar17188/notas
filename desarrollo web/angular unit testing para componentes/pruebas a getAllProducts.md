# Pruebas a getAllProducts
Las pruebas que se realizan al método getAllProducts nos da la visualización cuando incrementarmos los valores de un limit (#máximo de productos visualizados) y un offsset(# máximo de carga desde el último renderizado) para renderizar los productos desde la API.

Por lo que se realizarón varios cambios en el component de products y en su prueba

products.component.ts
```ts
 products: Product[] = [];
 limit = 10;
 offset = 0;
 status: 'loading' | 'success' | 'error' | 'init'= 'init';

  constructor(
    private productsService: ProductsService
  ) { }

  ngOnInit(): void {
    this.getAllProducts();
  }

  getAllProducts() {
    this.status = 'loading';
    this.productsService.getAll(this.limit, this.offset)
    .subscribe(products => {
      this.products = [...this.products, ...products];
      this.offset += this.limit;
      this.status = 'success';
    });
  }
```

products.component.html
```html
<section class="container">
  <h1>Products Component</h1>
  <div class="my-grid">
    <app-product
      *ngFor="let product of products"
      [product]="product">
  </app-product>
  </div>
  <button [disabled]="status === 'loading'" (click)="getAllProducts()">
    <span *ngIf="status === 'init' || status === 'success'">Load more</span>
    <span *ngIf="status === 'loading'">Loading...</span>
    <span *ngIf="status === 'error'">Error</span>
    </button>
</section>
```

products.component.spec.ts
```ts
  describe('test for getAllProducts()', () => {
    it('should return product list from service', () => {
      // Arrange
      const productsMock = generateManyProducts(10);
      productService.getAll.and.returnValue(of(productsMock));
      const countPrev = component.products.length;
      // Act
      component.getAllProducts();
      // TODO
      const expectedImg = fixture.debugElement.query(By.css('app-product img'));
      fixture.detectChanges();
      // Assert

      expect(component.products.length).toEqual(productsMock.length + countPrev);
      expect(component.products[0].images[0]).toEqual(expectedImg.nativeElement.src);
    });
  });
});
```