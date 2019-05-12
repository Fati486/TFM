# Análisis de las variables fisicoquímicas y sensoriales que influyen en grado de calidad de un vino
### **Introducción**

En los últimos años se ha reconocido la importancia de tener un mayor conocimiento acerca de cómo se comporta sensorialmente el vino, ya que ello permite entre otras cosas conocer el grado de aceptación por parte del consumidor, establecer criterios de calidad, desarrollar nuevos productos que se ajusten a los gustos cambiantes del mercado o compararlo con los competidores.

Hemos visto como en los últimos años ha habido un incremento de inversores en el sector del vino, con lo cual la inversión de numerosas empresas y particulares puede variar en función de la información disponible sobre la calidad del mismo.

En el presente estudio, se pretende mediante técnicas de Machine Learning, explorar la relación existente entre la calidad del vino y las variables fisicoquímicas y sensoriales del mismo (como por ejemplo lo son la ácidez, el pH, y el alcohol), y en consecuencia ver cuales de estas variables hacen que un vino sea considerado bueno.

Para la exploración y el análisis de los datos se utilizaron gráficos (como seaborn y ggplot), y varios algoritmos de aprendizaje automático para determinar qué propiedades fisicoquímicas poseen un mayor impacto en la calidad de un vino.

## **El Dataset**:

Para el desarrollo del proyecto se ha utilizado el Dataset (winequalityX2.csv) sobre diferentes muestras de vino. Este dataset ha sido obtenido de la página https://www.kaggle.com/, con própositos de aprendizaje, y consta de 1599 filas y 12 columnas de atributos physicoquímicos (como por ejemplo: pH) y sensoriales (como por ejemplo: La calidad percibida). Los valores de calidad de este dataset están basados en la media de al menos 3 evaluaciones hechas por expertos, donde cada experto calificó la calidad del vino entre 0 (muy malo) y 10 (excelente). 

Las variables que componen nuestro dataset son las siguientes:

1. *Fixed Acidity (Ácidez Fija):* Es el conjunto de ácidos naturales procedentes de la uva (tartárico, málico, cítrico y succínico) o formados en la fermentación maloláctica (láctico). En general, los ácidos (acidez fija) son preservantes naturales del vino y ayudan a mantener el color y las cualidades aromáticas del mismo.

2. *Volatile Acidity (Ácidez Volátil):* Es el conjunto de ácidos formados durante la fermentación o como consecuencia de alteraciones microbianas; su valor es un índice de la degradación del vino. Si la acidez volátil, presente en todos los vinos, es muy elevada el vino se picará y avigranará con el paso del tiempo. Es conveniente que la acidez volátil de un vino sea lo más baja posible. 

3. *Citric Acid (Ácido Cítrico):* En pequeñas cantidades este ácido puede añadir frescor y sabor a los vinos (es un ácido fijo).

4. *Residual Sugar (Azúcar Residual):* Durante la fermentación, y por acción de las levaduras, el azúcar (glucosa + fructosa) se transforma en alcohol etílico, anhídrido carbónico y otras muchas sustancias que caracterizan al vino. Cuando la fermentación es prácticamente total se dice que el vino es seco, pero lo normal es que en todo vino quede cierta cantidad de azúcares sin fermentar, denominados azúcares residuales.

5. *Chlorides (Cloruros):* Cantidad de sal en el vino.

6. *Free Sulfur Dioxide (Dióxido de Azúfre Libre):* El SO2 es una herramienta indispensable en la elaboración y conservación de vinos. Una correcta utilización del SO2 permite obtener vinos menos oxidados, dotados de un mejor color y aroma, y una menor acidez volátil, debido a sus efectos como antioxidante y antimicrobiano.

7. *Total Sulfur Dioxide (Dióxido de Azúfre Total):* Es la suma de concentraciones libres y amarradas de S02; concentraciones de dióxido de azúfre libres superiores a 50 ppm se vuelven evidentes en el sabor y olor.

8. *Density (Densidad):* Densidad del vino, que suele ser similar al del agua dependiendo de la concentración de azucar y de alcohol.

9. *pH:* Describe cómo de ácido o básico es el vino: 0 (muy ácido) a 14 (muy básico). La mayoría de vinos se encuentra en la escala 3-4.

10. *Sulphates (Sulfatos):* Actúan como un antimicrobial y antioxidante. Un agua con una cantidad de sulfatos inferior a 250mg/l se considera en este aspecto un agua de calidad y con valores superiores a 400mg/l insalubre.

11. *Alcohol:* Cantidad de alcohol del vino. Tras el agua, es el componente más abundante en el vino y el que lo caracteriza. Se produce por la transformación de los azúcares del mosto durante la fermentación. 

12. *Quality (Calidad):* Calificación entre 0 y 10 basada en la percepción sensorial de los expertos.

### **Entorno de Desarrollo**

El entorno de trabajo para el desarrollo del código y la elaboración del proyecto ha sido la plataforma Google Colaboratory, no obstante; el correcto funcionamiento del código también se ha validado en el entorno de la máquina virtual facilitada por la escuela Kschool (Jupyter Notebook).
Los notebooks subidos corresponden a los validados desde la máquina virtual, no obstante, también se dejará comentado el código utilizado en la fase de desarrollo desde la plataforma google colaboratory.

- Lenguaje de programación: Python 3
- Entorno de desarrollo interactivo: IPython Notebook
- Entorno de desarrollo: Google colaboratory
- Entorno de validación: Máquina virtual facilitada por Kschool.

El desarrollo de este trabajo se ha dividido en 3 las siguientes partes (notebooks):

**Parte 1- Carga del Dataset**
En esta primera parte realizaremos el proceso de la carga de nuestro Dataset, y realizaremos una serie de comprobaciones sencillas para validar integridad de los datos.

**Parte 2- Exploración y Análisis de Datos**
En esta parte realizaremos las modificaciones necesarias al Dataset a fin de adaptarlo el dataset a las necesidades del proyecto, y se revisará y analizará como están distribuidas y relacionadas las variables entre sí. Adicionalmente también se categorizará la variable 'calidad' en los siguientes 3 valores: '1'-Bueno, '2'-Aceptable, y '3'-Malo.

**Parte 3- Entrenamiento del Modelo**
En esta última parte, se abordaron los siguientes puntos:

- Tras escalar los datos dividimos los mismos en conjuntos de entrenamiento y validación.
- Luego entrenamos el dataset con 5 modelos, y obtuvimos que el modelo 'Random Forest' fue el que obtuvo mayor precisión y recall.
- Posteriormente extraímos las variables más importantes y volvímos a entrenar el modelo 'Random Forest' solo con ellas para así comparar los resultados.
- Por último aplicamos la técnico del sobremuestreo (SMOTE) para intentar balancear las muestras y con ello volvimos a entrenar con 'random Forest' para comparar y extraer las conclusiones. 
 
 En este último notebook, al ejecutar el código con mi máquina virtual, he tenido un error de sistema al intentar calcular las variables importantes, no obstante en Google Colaboratory funciona sin problemas. Si te da el mismo fallo te recomiendes que ejecutes el código en Colab (para ello he dejado el notebook completo en este file: 'Predicción_de_la_Calidad_del_Vino_usando_Machine_Learning.ipynb'
 
 Cualquier duda y/o critica constructiva será bien recibida. Muchas gracias por leerlo.
  



