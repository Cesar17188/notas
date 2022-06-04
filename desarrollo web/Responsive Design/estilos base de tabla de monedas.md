# Estilos base de tabla de monedas

Nadie le presto atencion a porque le puso 15px en margin bottom :v…yo si …anteriormente se puso 30 px en margin bottom con .main-exchange-container p …asi que se afecta al padre .main-echange-container y lo heredan sus crias


```html
<section class="main-tables-container">

 <div class="main-currency-table">

 <p class="currency-table--title">Monedas</p>

 <div class="currency-table--container">

 <table>

 <tr>

 <td class="table__top-left">Bitcoin</td>

 <td class="table__top-right table__right">$ 1.96 <span></span></td>

 </tr>

 <tr>

 <td>Ethereum</td>

 <td class="table__right">$ 0.07 <span></span></td>

 </tr>

 <tr>

 <td>Ripple</td>

 <td class="table__right">$ 2.15 <span></span></td>

 </tr>

 <tr>

 <td class="table__bottom-left">Stellar</td>

 <td class="table__bottom-right table__right">$ 4.96 <span></span></td>

 </tr>

 </table>

 </div>

 <div class="currency-table--date">

 <p> <b>Actualizado:</b> 19 Julio 23:45</p>

 </div>

 </div>

 <div></div>

 </section>

```

```css
.main-currency-table {

 width: 70%;

 min-width: 235px;

 max-width: 500px;

 height: 360px;

 margin: 0 auto;

 font-family: "Inter", sans-serif;

}

.main-currency-table .currency-table--title{

 margin-bottom: 15px;

 font-size: 1.8rem;

 font-weight: bold;

 line-height: 2.3rem;

 color: var(--bitcoin-orange);

}

.main-currency-table .currency-table--container {

 width: 90%;

 min-width: 230px;

 max-width: 300px;

 height: 250px;

 margin: 0 auto;

}

.currency-table--container table {

 width: 100%;

 height: 100%;

}

.currency-table--container td {

 width: 50%;

 font-size: 1.6rem;

 font-weight: 500;

 line-height: 1.9rem;

 color: var(--grey);

 background-color: var(--just-white);

 text-align: justify;

}
```