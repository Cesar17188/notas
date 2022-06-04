# Estilos a la lista de productos

HTML
 ```html

<h1>*ngFor Objs</h1>

<div class="products--grid">

 <div *ngFor="let product of products">

 <img [src]="product.image" alt="image">

 <h2>{{product.price | currency}}</h2>

 <p>{{ product.name }}</p>

 </div>

</div>
 
```

SCSS
```scss
.products--grid {

 display: flex;

 flex-direction: column;

	 div {

		 img {

				 width: 100%;

				 height: auto;
	
				 border-radius: 10px;

				}

		  h2 , p {

				 margin: 0;

				}
	
			}

}

  

@media screen and (min-width: 400px) {

	 .products--grid {

					display: grid;

					grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));

					grid-gap: 15px;

				 }

}

  

@media screen and (min-width: 450px) {

	.products--grid {

			 display: grid;

			 grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));

			 grid-gap: 15px;

			 }

}

  
  

@media screen and (min-width: 780px) {

	.products--grid {

				display: grid;

				grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));

				grid-gap: 15px;

			 }

}

 @media screen and (min-width: 1490px) {

	.products--grid {

					display: grid;

					grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));

					grid-gap: 15px;

				 }

}

  

@media screen and (min-width: 1840px) {

	.products--grid {

					display: grid;

					grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));

					grid-gap: 15px;

				 }

}

  

@media screen and (min-width: 2000px) {

		.products--grid {

					display: grid;

					grid-template-columns: repeat(auto-fill, minmax(400px, 1fr));

					grid-gap: 15px;

				}

}
```