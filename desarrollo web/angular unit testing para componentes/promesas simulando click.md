# Promesas simulando click

cuando simulamos eventos desde el render es necesario usar el fakeasync y tick

products.component.html
```html
<section class="container">
  <h1>Products Component</h1>
  <h3>Rta</h3>
  <button class="btn-promise" (click)="callPromise()">Call promise</button>
  <p class="rta">{{ rta }}</p>
  <div class="my-grid">
    <app-product
      *ngFor="let product of products"
      [product]="product">
  </app-product>
  </div>
  <button class="btn-products" [disabled]="status === 'loading'" (click)="getAllProducts()">
    <span *ngIf="status === 'init' || status === 'success'">Load more</span>
    <span *ngIf="status === 'loading'">Loading...</span>
    <span *ngIf="status === 'error'">Error</span>
    </button>
</section>
```

```ts
describe('test for callPromise', () => {
    it('should call to promise', async() => {
      // Arrange
      const mockMsg = 'my mock string';
      valueService.getPromiseValue.and.returnValue(Promise.resolve(mockMsg));
      // Act
      await component.callPromise();
      fixture.detectChanges();
      // Assert
      expect(component.rta).toEqual(mockMsg);
      expect(valueService.getPromiseValue).toHaveBeenCalled();
    });

    it('should show "my mock string" in <p> when btn was clicked', fakeAsync(() => {
      // Arrange
      const mockMsg = 'my mock string';
      valueService.getPromiseValue.and.returnValue(Promise.resolve(mockMsg));
      const btnDe = fixture.debugElement.query(By.css('.btn-promise'));

      // Act
      btnDe.triggerEventHandler('click', null);
      tick();
      fixture.detectChanges();
      const rtaDe = fixture.debugElement.query(By.css('p.rta'));
      // Assert
      expect(component.rta).toEqual(mockMsg);
      expect(valueService.getPromiseValue).toHaveBeenCalled();
      expect(rtaDe.nativeElement.textContent).toEqual(mockMsg);
    }));
  });
```

## Reto
```ts
it('should change the status "loading" to "error" when btn-products was clicked', fakeAsync(() => {
      // Arrange
      productService.getAll.and.returnValue(defer(() => Promise.reject('error')));
      const btnDe = fixture.debugElement.query(By.css('.btn-products'));
      // Act
      btnDe.triggerEventHandler('click', null);
      fixture.detectChanges();
      expect(component.status).toEqual('loading');
      tick(4000); // exec, obs, setTimeout, promise
      fixture.detectChanges();
      // Assert
      expect(component.status).toEqual('error');
    }));
```