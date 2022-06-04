# Componentes con dependencias
En unit testing se provo conceptos de forma individual por medio de mockigs y spies a dependencias.

Por lo que vamos a hacer un mocking a las dependencias del component

veamos como se forma cuando products component depende de product component que a su vez depende de product service

products.component.spec.ts
```ts
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { of  } from 'rxjs';
import { ProductsComponent } from './products.component';
import { ProductComponent } from './../product/product.component';
import { ProductsService } from './../../services/product.service';
import { generateManyProducts } from './../../models/product.mock';

describe('ProductsComponent', () => {
  let component: ProductsComponent;
  let fixture: ComponentFixture<ProductsComponent>;
  let productService: jasmine.SpyObj<ProductsService>;

  beforeEach(async () => {
    const spy = jasmine.createSpyObj('ProductsService', ['getAll']);

    await TestBed.configureTestingModule({
      declarations: [ ProductsComponent, ProductComponent ],
      providers: [
        { provide: ProductsService, useValue: spy }
      ]
    })
    .compileComponents();
  });

  beforeEach(() => {
    fixture = TestBed.createComponent(ProductsComponent);
    component = fixture.componentInstance;
    productService = TestBed.inject(ProductsService) as jasmine.SpyObj<ProductsService>;

    const productsMock = generateManyProducts(3);
    productService.getAll.and.returnValue(of(productsMock));
    fixture.detectChanges(); //ngOnInit()
  });

  it('should create', () => {
    const productsMock = generateManyProducts(3);
    productService.getAll.and.returnValue(of(productsMock));
    fixture.detectChanges();
    expect(component).toBeTruthy();
    expect(productService.getAll).toHaveBeenCalled();
  });
});
```