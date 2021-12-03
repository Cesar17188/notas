# Creando un clasificador con Scikit-Learn

algunas cosas que comentar que pueden ser utiles

-   cuando se hace el drop intentando eliminar algunas variables que no serán de interés, axis = 1 indica que estas variables son "columnas ", axis = 0 , indicaría que son filas.
-   las dummy variables que se mencionan ligeramente convierten las variables categóricas en indicadoras como 0,1,2,…etc
-   cuando se completaron los valores faltantes en las variables edad y la clase del pasajero (embarked), faltó mencionar un comando muy util para saber en que variables se tienen valores faltantes. Se puede usar train_df.isnull.any().

Cuando se llenan los espacios con vacíos (fillna), para el caso de datos numéricos se utiliza la mediana porque es una de las medidas de tendencia central que menos se afecta por los datos atípicos.

Para el caso de los datos categóricos relacionados con el embarque, se utiliza la letra S porque representa el embarque en la ciudad de South Hampton, en donde más personas se unieron al viaje.

Estos datos se obtienen de un análisis previo a los datos trabajados.

-   Ésta línea: encoder_sex = label_encoder.fit_transform(data_set_train[‘Sex’]) , transforma una etiqueta textual a un equivalente numérico.
-   Ésta línea: categorical_cols = [cname for cname in train_predictors.columns if  
    train_predictors[cname].nunique() <10 and  
    train_predictors[cname].dtype == ‘object’  
    ]  
    Encuentra las columnas que contiene información no numérica.
-   Ésta línea: numerical_cols = [cname for cname in train_predictors.columns if  
    train_predictors[cname].dtype in [‘int64’, ‘float64’]  
    ]  
    Encuentra las columnas con datos numéricos.

Estoy bien? o entendí algo mal. Quedo a la espera de sus comentarios. gracias.