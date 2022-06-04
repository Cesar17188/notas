# Uso de linear-gradient

Una excelente herramienta para trabajar con **gradients**: [CSS Gradient](https://cssgradient.io/).

```
background: linear-gradient(grados°- lados o esquinas, Color_1 %opcional, color_2 %opcional);
```

-   Los grados van de 0° a 360°, los puedes ingresar en entero o decimal seguido del acrónimo de medida **deg**.
    -   ej.

```
/*Entero*/
background: linear-gradient(270deg, #201E1C 16.69%, #F7931A 100%);
/*Decimal*/
background: linear-gradient(207.8deg, #201E1C 16.69%, #F7931A 100%);
```

-   Los lados (left, right, top y bottom) se usan de manera simple o conjunta para indicar esquinas (to left top), recuerda agregar al inicio del lado o esquina que vas a ingresar la palabra **“to”**
    -   ej.

```
/*Lado*/
background: linear-gradient(to left, #201E1C 16.69%, #F7931A 100%);
/*Esquina inferior derecha*/
background: linear-gradient(to right bottom, #201E1C 16.69%, #F7931A 100%);
```

-   El **porcentaje %** es opcional ten en cuenta que el default para el Color_1 es de 0%, el del Color_2 es del 100%.
    -   ej.

```
/*Default Color 1 0% y Color_2 100%)*/
background: linear-gradient(207.8deg, #201E1C, #F7931A);
```

![%_Standard.PNG](https://static.platzi.com/media/user_upload/%25_Standard-cb66ce11-707a-4043-b005-c4a4b9392edb.jpg)

```
/*% de color asignado manualmente)*/
background: linear-gradient(207.8deg, #201E1C 16.69%, #F7931A 100%);
```

![%_Fixed.PNG](https://static.platzi.com/media/user_upload/%25_Fixed-8b1b113f-db3e-4cf4-bae6-f3dabbe52283.jpg)