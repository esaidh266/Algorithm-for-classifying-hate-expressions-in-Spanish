# Algorithm for classifying hate expressions in Spanish

**Readme en español**

Algoritmo de clasificación de expresiones de odio en mensajes en español. Este algoritmo fue desarrollado en el marco del proyecto Hatemedia (PID2020-114584GB-I00), financiado por MCIN/AEI /10.13039/501100011033.

Importación y uso del modelo para realizar predicciones:

Los diferentes modelos empleados tienen como fin analizar datos extraídos de diferentes redes sociales como por ejemplo Twitter o Facebook de la cual se extraen los comentarios referentes a los periódicos (La Vanguardia, El Mundo, ABC, El País y 20 Minutos) y páginas web de los mismos para su posterior clasificación en función de si estos contienen o no odio.

Para llevar a cabo esta clasificación, se han entrenado distintos modelos como Gradient Boosting, SVM (Support Vector Machines), RF (Random Forest) o CART (Classification And Regression Tree).

Para el uso de los diferentes modelos de predicción se adjuntan los scripts Python “ejemplo.py” y “obtencion_caracteristicas.py” y la carpeta “recursos” en la que se encuentran las distintas bolsas de palabras utilizadas para la obtención de características en el preprocesado de los comentarios a predecir.
Antes de ejecutar estos scripts es necesario instalar las distintas librerías importadas en ellos.

OBTENCION_CARACTERISTICAS.PY:

Las funciones presentes en este script son necesarias para el preprocesado del corpus.  Los distintos modelos necesitan las características extraídas mediante este script para realizar sus  predicciones.

EJEMPLO.PY:

Se detalla a continuación mediante el código de este script el procedimiento a seguir para realizar las predicciones.

Importamos la librería joblib para poder cargar los distintos modelos, así como importamos el otro script adjunto y la librería pandas para trabajar con dataframes:

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/4f5fb782-d126-4887-ab42-866578f79348)

Cargamos el modelo mediante el uso de la librería joblib:

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/b94532ee-6fbb-4d64-b973-351ce163ddba)

Leemos el archivo csv en el que están presentes los distintos comentarios sobre los que queremos realizar las predicciones. Para que el preprocesado se lleve a cabo correctamente necesitamos nombrar como “CONTENIDO A ANALIZAR” la columna que contiene los comentarios.

Se crea un dataframe que contendrá los comentarios, al que más tarde se añadirán las predicciones.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/4c35041f-69f5-4924-8997-28dbd361a45f)

Se obtienen las características que utilizará el modelo para realizar la predicción de llos comentarios:

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/090608fe-074b-4f97-bdca-66dce64b64fe)

Obtenemos las predicciones y mostramos los resultados:

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/b6a30653-dee8-4d5f-a12a-cd46acfa6e31)

Uso del código de entrenamiento:

Se adjunta el notebook de Google Colab “Modelo_binario_.ipynb”, siendo aquí donde encontramos el código a ejecutar para el entrenamiento de los modelos.

Colab es un producto de Google Research que permite a cualquier usuario escribir y ejecutar código arbitrario de Python en el navegador; es especialmente adecuado para tareas de aprendizaje automático, análisis de datos y educación. Con esta herramienta veremos el código en distintas celdas que podremos ejecutar de manera independiente.

Al lanzar la siguiente celda se importan las distintas librerías necesarias para la ejecución de todo el código:

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/7bc3c665-ace4-4507-9c1f-01254fa4d3b0)

Si es la primera vez que ejecutamos esta celda, antes debemos instalar las distintas librerías en el entorno de ejecución que proporciona Google Colab, de la siguiente forma:

! pip install nombre_de_la_libreria

En las siguientes celdas se realiza lo siguiente:

1. La función get_X_y(df) retorna por separado las características y la etiqueta asociada (odio = 1, no odio = 0) con las que se entrena y valida el modelo.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/8daef670-1a30-4d9e-a7a3-61af7b002116)

2. Leemos el archivo .csv a un DataFrame de pandas.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/fa3fd2aa-1af6-4fe5-9375-dedd465fca01)

3. Fusionar intensidades ejecutando

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/2cb7b59f-eca2-4a24-85e9-73d33710f69c)

Empezamos preparando el dataset separando las entradas que contienen odio y las que no.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/689592dc-3d1b-4de9-8241-817193c0b730)

Ejecutamos para obtener las secciones del dataset que consigan un mayor accuracy para posteriormente realizar el entrenamiento de los modelos. 

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/62eca5a1-e7bc-4b57-8ed2-1e6bb5d98d93)

Obtenemos la sección con la que se ha conseguido el mayor accuracy para conformar el cuerpo de entrenamiento y validación de los distintos modelos.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/023c0b88-4b1c-4209-bc03-71783c3df01f)

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/eef054c5-742f-4841-bc71-d542f588d701)

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/d626ff8d-c4e6-4791-be17-4a0d9b3f6a17)

Las siguientes celdas servirán para lanzar el entrenamiento, en este caso, del modelo Gradient Boosting (a continuación aparecen las celdas con el código correspondiente al resto de modelos); y visualizar los resultados en el reporte de clasificación y la matriz de confusión pintada con la librería matplotlib.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/668077d0-ebf6-467d-a1a4-fe4aa79d98ce)

En una última celda podemos descomentar la segunda línea si queremos exportar un modelo ya entrenado.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/5e4561d2-0fc2-45f8-9da6-1047c92b8383)

Authores:
- Elias Said-Hung
- Julio Montero-Díaz
- Oscar De Gregorio
- Almudena Ruiz
- Xiomara Blanco
- Juan José Cubillas
- Daniel Pérez Palau 

Financiado por: 
Agencia Estatal de Investigación – Ministerio de Ciencia e Innovación

Con el apoyo de:
- POSSIBLE S.L.

Más información
- [https://www.hatemedia.es/](https://www.hatemedia.es/) o contactar con:  elias.said@unir.net

---

**Readme in English**

Algorithm for classifying hate expressions in messages in Spanish. 

This algorithm was developed within the framework of the Hatemedia project (PID2020-114584GB-I00), funded by MCIN/ AEI /10.13039/501100011033.

Importing and using the model to make predictions:

The purpose of the different models used is to analyze data extracted from different social networks such as Twitter or Facebook from which comments regarding newspapers (La Vanguardia, El Mundo, ABC, El País and 20 Minutos) and web pages of the same for subsequent classification depending on whether or not they contain hate.

To carry out this classification, different models have been trained, such as Gradient Boosting, SVM (Support Vector Machines), RF (Random Forest) or CART (Classification And Regression Tree).

For the use of the different prediction models, the Python scripts “ejemplo.py” and “obtencion_caracteristicas.py” and the “recursos” folder are attached, in which the different bags of words used to obtain characteristics in the preprocessing are located in comments to predict.

Before running these scripts, installing the different libraries imported into them is necessary.

OBTAIN_CHARACTERISTICS.PY:

The functions present in this script are necessary for preprocessing the corpus. The different models need the features extracted using this script to make predictions.

EXAMPLE.PY:

The procedure to make the predictions is detailed below using the code of this script.

We import the joblib library to be able to load the different models, as well as import the other attached script and the pandas library to work with data frames:

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/4f5fb782-d126-4887-ab42-866578f79348)

We load the model by using the joblib library:

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/b94532ee-6fbb-4d64-b973-351ce163ddba)

We read the CSV file in which the different comments on which we want to make the predictions are present. For the preprocessing to be carried out correctly, we need to name the column that contains the comments as “CONTENT TO ANALYZE”.

A data frame will contain the comments, to which the predictions will be added later.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/4c35041f-69f5-4924-8997-28dbd361a45f)

The characteristics that the model will use to predict the comments are obtained:

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/090608fe-074b-4f97-bdca-66dce64b64fe)

We get the predictions and show the results:

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/b6a30653-dee8-4d5f-a12a-cd46acfa6e31)

Training code usage:

The Google Colab notebook “Modelo_binario_.ipynb” is attached. This is where we find the code to execute for training the models.

Colab is a Google Research product that allows any user to write and run arbitrary Python code in the browser. It is especially suitable for machine learning, data analysis and education tasks. With this tool, we will see the code in different cells that we can execute independently.

When launching the following cell, the different libraries necessary for the execution of all the code are imported:

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/7bc3c665-ace4-4507-9c1f-01254fa4d3b0)

If it is the first time that we execute this cell, we must first install the different libraries in the execution environment provided by Google Colab, as follows:

! pip install library_name

In the following cells, the following is done:

1. The function get_X_y(df) separately returns the characteristics and the associated label (hate = 1, non-hate = 0) with which the model is trained and validated.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/8daef670-1a30-4d9e-a7a3-61af7b002116)

2. We read the .csv file into a Pandas DataFrame.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/fa3fd2aa-1af6-4fe5-9375-dedd465fca01)

3. Merge intensities by running

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/2cb7b59f-eca2-4a24-85e9-73d33710f69c)

We prepare the dataset by separating the entries containing hate and those not.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/689592dc-3d1b-4de9-8241-817193c0b730)

We execute to obtain the sections of the dataset that achieve greater accuracy to later train the models.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/62eca5a1-e7bc-4b57-8ed2-1e6bb5d98d93)

We obtain the section with which the highest accuracy has been achieved to form the training and validation body of the different models.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/023c0b88-4b1c-4209-bc03-71783c3df01f)

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/eef054c5-742f-4841-bc71-d542f588d701)

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/d626ff8d-c4e6-4791-be17-4a0d9b3f6a17)

The following cells will be used to launch the training, in this case, of the Gradient Boosting model (the cells with the code corresponding to the rest of the models appear below) and visualize the results in the classification report and the confusion matrix painted with the matplotlib library.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/668077d0-ebf6-467d-a1a4-fe4aa79d98ce)

In the last cell, we can uncomment the second line to export an already-trained model.

![Image](https://github.com/users/esaidh266/projects/5/assets/84383299/5e4561d2-0fc2-45f8-9da6-1047c92b8383)

Authors:
- Elias Said-Hung
- Julio Montero-Díaz
- Oscar De Gregorio
- Almudena Ruiz
- Xiomara Blanco
- Juan José Cubillas
- Daniel Pérez Palau

Financed by: State Research Agency – Ministry of Science and Innovation

Supported by:
- POSSIBLE S.L.

For more information:
- [https://www.hatemedia.es/](https://www.hatemedia.es/) or contact elias.said@unir.net


