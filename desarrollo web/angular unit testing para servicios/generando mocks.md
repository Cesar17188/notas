# Generando Mocks

No es necesario crear data manualmente para hacer las pruebas de conexión a las API, se puede generar de manera automatizada utilizando una lebrería que genera datos de forma aleatoria.

## Faker js

desde la terminal vamos a instalarla
```
npm i faker-js/faker --save-dev
```

ahora vamos a crear un archivo llamado product.mock.ts en la carpeta de models, donde crearemos data de prueba con faker

product.mock.ts
```ts
import { faker } from '@faker-js/faker';
import { Product } from './product.model';

export const generateOneProduct = (): Product => {
  return {
    id: faker.datatype.uuid(),
    title: faker.commerce.productName(),
    price: parseInt(faker.commerce.price(), 10),
    description: faker.commerce.productDescription(),
    category: {
    id: faker.datatype.number(),
    name: faker.commerce.department()
    },
    images: [faker.image.imageUrl(), faker.image.imageUrl()]
  };
}

export const generateManyProducts = (size = 10): Product[] => {
  const products: Product[] = [];
  for (let index = 0; index < size ; index++) {
    products.push(generateOneProduct());
  }
  return [...products];
}
```

finalmente haremos los siguientes cambios en product.service.spec.ts haciendo una importación de product.mock.ts

product.service.spec.ts
```ts
import { generateManyProducts } from '../models/product.mock';

describe('tests for getAllSimple', () => {
    it('should return a product list', () => {
      //Arrange
      const mockData: Product[] = generateManyProducts(2);
      //Act
      productsService.getAllSimple()
      .subscribe((data) => {
        //Assert
        expect(data.length).toEqual(mockData.length);
        //doneFn();
      });
      //http config
      const url = `${environment.API_URL}/api/v1/products`;
      const req = httpController.expectOne(url);
      req.flush(mockData);
      httpController.verify();
    });
  });
```