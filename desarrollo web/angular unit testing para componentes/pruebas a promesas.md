# Pruebas a promesas

Aqui ejecutaremos pruebas a promesas desde componentes para lo cual probaremos utilizando value service que tiene una función de llamada a una promesa

primero lo inyectaremos como dependencia

products.component.ts
```ts
import { ValueService } from './../../services/value.service';

constructor(
    private valueService: ValueService,
  ) { }

async callPromise () {
    const rta = await this.valueService.getPromiseValue();
    this.rta = rta;
  }
```

luego lo llamaremos para hacer las pruebas 

products.component.spec.ts
```ts
import { ValueService } from './../../services/value.service';

describe('ProductsComponent', () => {
  let valueService: jasmine.SpyObj<ValueService>;

  beforeEach(async () => {
    const productServiceSpy = jasmine.createSpyObj('ProductsService', ['getAll']);
    const valueServiceSpy = jasmine.createSpyObj('ValueService', ['getPromiseValue']);

    await TestBed.configureTestingModule({
      declarations: [ ProductsComponent, ProductComponent ],
      providers: [
        { provide: ProductsService, useValue: productServiceSpy },
        { provide: ValueService, useValue: valueServiceSpy }
      ]
    })
    .compileComponents();
  });
 
beforeEach(() => {
    fixture = TestBed.createComponent(ProductsComponent);
    component = fixture.componentInstance;
    productService = TestBed.inject(ProductsService) as jasmine.SpyObj<ProductsService>;
    valueService = TestBed.inject(ValueService) as jasmine.SpyObj<ValueService>;

    const productsMock = generateManyProducts(3);
    productService.getAll.and.returnValue(of(productsMock));
    fixture.detectChanges(); //ngOnInit()
  });


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
```

