# Queries distribuidos

Acerca de que al trabajar de manera local olvidamos que la transferencia de información y la comunicación, impacta sobre el tiempo en el cual se obtienen los resultados y la información, en las empresas el tiempo es dinero, y si estamos preparados para analizar este tipo de problemas con lógica, podemos ser mas eficientes, este tipo de conocimiento es lo que crea un plus a nuestro trabajo.

1.  Analiza cual tabla tiene la menor cantidad de datos (columnas+tablas)
2.  Filtra esos registros donde sea menor cantidad
3.  Trae esos pocos registros a la misma región donde están la mayor cantidad de datos


-   Retraso total en la comunicación = Retraso total de acceso + (Volumen total de datos / tasa de transferencia)
    
-   Retraso total en la comunicación =( numero mensajes/10 ) + (numero de bits /50000)