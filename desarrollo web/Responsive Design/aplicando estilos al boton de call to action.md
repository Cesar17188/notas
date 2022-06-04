# Aplicando estilos al botón de call to action

```css
.plan-container--title {

 position: absolute;

 width: 120px;

 height: 31px;

 left: calc(50% - 60px);

 top: -15px;

 border-radius: 8px;

 color: var(--just-white);

 font-size: 1.2rem;

 padding: 6px;

}

.plan-container--title-recommended {

 background: linear-gradient(207.8deg, #201e1c 16.69%, #f7931a 100%);

}

.plan-container--title-basic {

 background: linear-gradient(207.8deg, #201e1c 16.69%, #22068a 100%);

}

.plan-container--title-pro {

 background: linear-gradient(207.8deg, #201e1c 16.69%, #14a101 100%);

}

.plan-card--title {

 padding-top: 30px;

 font-size: 1.4rem;

 font-weight: 500;

 line-height: 1.8rem;

 color: black;

}

.plan-card--price {

 padding: 5px 0;

 font-size: 5.2rem;

 font-weight: bold;

 line-height: 5.3rem;

 color: black;

}

.plan-card--price span {

 font-size: 1.2rem;

 font-weight: 300;

 position: absolute;

 top: 40px;

 left: calc(30% - 7px);

}

.plan-card--saving {

 font-size: 1.2rem;

 color: #757575;

}

.plan-card--ca {

 width: 150px;

 height: 48px;

 margin-top: 20px;

 background-color: #FAF8F7;

 border-radius: 4px;

 font-size: 1.4rem;

 font-weight: bold;

 line-height: 1.8rem;

 color: var(--black);

 font-family: "DM Sans", sans-serif;

}

.plan-card--ca-r {

 border: 2px solid var(--bitcoin-orange);

}

.plan-card--ca-b {

 border: 2px solid #22068a;

}

.plan-card--ca span{

 display: inline-block;

 width: 20px;

 height: 20px;

 vertical-align: text-bottom;

}

.plan-card--ca-r span {

 background-image: url("./assets/icons/orange-right-arrow.svg");

}

.plan-card--ca-b span {

 background-image: url("./assets/icons/blue-right-arrow.svg");

 background-position: center;

 background-repeat: no-repeat;

}

.plan-card--ca-p span {

 background-image: url("./assets/icons/green-right-arrow.svg");

 background-position: center;

 background-repeat: no-repeat;

}
```