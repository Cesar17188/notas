# Regresión logística con Scikit-Learn: evaluación del modelo

**Matriz de confusión**  
Representación gráfica que nos permite ver el grado de acierto de nuestro modelo. El gráfico tiene cuatro divisiones: Verdaderos Positivos (VP), Falsos Positivos (FP), Falsos Negativos (FN) y Verdaderos Negativos (VN). Siendo los datos verdaderos los que nos interesa maximizar (valores de la diagonal).

**Graficado de la Matriz de Confusion:**

-   Los datos necesarios los obtenemos de nuestro modelo (con ayuda del módulo metrics):

```
cnf_matrix = metrics.confusion_matrix(y_test,y_pred)
```

-   Definimos los ejes con sus respectivas etiquetas

```
class_names = [0,1]
fig,ax = plt.subplots() #obtenemos las variables figura y ejes del gráfico (nos permite cambiar los atributos propios de cada seccion)
tick_marks = np.arange(len(class_names))  #definimos los valores que van a tener las líneas de guía
plt.xticks(tick_marks, class_names)
plt.yticks(tick_marks, class_names) #definimos los tick marks en el gráfico
```

-   Creamos la presentación del gráfico

```
sns.heatmap(pd.DataFrame(cnf_matrix), annot = True, cmap='Blues_r', fmt='g')
ax.axis.set_label_position('top')
plt.tight_layout()
plt.title('Matriz de confusion', y=1.1)
plt.y_label('Etiqueta Actual')
plt.x_label('Etiqueta de Prediccion)
```

```
- seaborn nos permite crear un mapa de calor a partir de los valores entregados (la matriz de confusión en este caso), los parámetros que entregamos son: annot → permite colocar los valores sobre el gráfico, cmap → estilo del gráfico, fmt → formato de los valores
- ax.xaxis,set_label_position() → nos permite definir donde colocar la etiqueta del eje x
- plt.tight_layout() → crea un padding en torno al gráfico (lo enmarca)
```

**Nota**

-   Otra forma de evaluar nuestro modelo es a través del método accuracy_score del módulo metrics:

```
metrics.accuracy_score(Y_test,y_pred)
```

Soy estudiante de medicina y me gustaría aclarar algunos conceptos interesantes sobre la diabetes por si alguno tiene curiosidad:

-   La diabetes es una enfermedad del metabolismo (es decir, la falla está en los procesos bioquímicos de nuestro cuerpo que se encargan de convertir los alimentos en energía)
    
-   La diabetes se caracteriza por **glucosa alta en sangre** (se llama Hiperglucemia).
    
-   La glucosa es una de las moléculas energéticas más importantes, del grupo de los **azúcares** o lo que también llamamos **carbohidratos** (este nombre es más correcto)
    
-   Generalmente esta enfermedad inicia en pacientes mayores de 40 años de edad (es muy raro verlo en pacientes más jóvenes, y si lo vemos, pensamos en que esta pueda tener un origen genético
    
-   El cuerpo requiere, para procesar correctamente la glucosa, de una proteína llama **Insulina** que entre otras funciones **disminuye la cantidad de glucosa en sangre**
    
-   Lo que pasa en el cuerpo de un paciente con diabetes es que, por muchas posibles causas, su cuerpo no está procesando correctamente esta glucosa.
    

La razón más común de esto es que, por una dieta inadecuada (alta en carbohidratos) a lo largo de muchos años, el cuerpo es **incapaz de producir la cantidad suficiente de Insulina** para compensar la **alta concentración de glucosa en sangre** .

Esto produce toxicidad en las células del cuerpo de quien padece diabetes, debido a que la glucosa en altas concentraciones resulta tóxica para muchos órganos.  
Entre los problemas más relevantes causados por diabetes en un paciente previamente sano, se encuentran:

-   Ceguera
-   Daño al riñón (que puede causar falla renal)
-   Problemas en la circulación de sangre de las piernas del paciente (lo que puede causar hasta la muerte de parte de la pierna del paciente por falta de nutrientes y falta de protección del sistema inmune contra virus y bacterias, y, en muchos casos, requerir de amputación)
-   Muerte a edad relativamente temprana o problemas relacionados al daño al corazón (como infarto).

La diabetes puede reducir la esperanza de vida (la cantidad máxima de años que una persona viviría normalmente estando sana) en hasta 10 años.