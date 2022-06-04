# Detallando estilos de tabla de monedas

![[Pasted image 20220105171238.png]]

```css
.main-currency-table, .main-comision-table{

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

.main-comision-table .comision-table--title {

 margin-bottom: 15px;

 font-size: 1.8rem;

 font-weight: bold;

 line-height: 2.3rem;

 color: var(--secondary-blue);

}

.main-currency-table .currency-table--container, .main-comision-table .comision-table--container{

 width: 90%;

 min-width: 230px;

 max-width: 300px;

 height: 250px;

 margin: 0 auto;

}

.currency-table--container table, .comision-table--container table{

 width: 100%;

 height: 100%;

}

.currency-table--container td, .comision-table--container td{

 width: 50%;

 font-size: 1.6rem;

 font-weight: 500;

 line-height: 1.9rem;

 color: var(--grey);

 background-color: var(--just-white);

 text-align: justify;

 padding-left: 15px;

}

.table__top-left {

 border-radius: 15px 0 0 0;

}

.table__top-right {

 border-radius: 0 15px 0 0;

}

.table__bottom-left {

 border-radius: 0 0 0 15px;

}

.table__bottom-right {

 border-radius: 0 0 15px 0;

}

  

.currency-table--container .table__right, .comision-table--container .table__right{

 text-align: center;

 font-size: 1.4rem;

 color: #757575;

 font-weight: normal;

 padding-left: 0;

}

.currency-table--container .down {

 display: inline-block;

 width: 15px;

 height: 15px;

 margin-left: 10px;

 background-image: url("./assets/icons/trending-down.svg");

 background-size: cover;

 background-position: center;

 background-repeat: no-repeat;

}

.currency-table--container .up {

 display: inline-block;

 width: 15px;

 height: 15px;

 margin-left: 10px;

 background-image: url("./assets/icons/trending-up.svg");

 background-size: cover;

 background-position: center;

 background-repeat: no-repeat;

}
```