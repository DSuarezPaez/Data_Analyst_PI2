# <h1 align=center> **PROYECTO INDIVIDUAL Nº2**
# <h1 align=center> **Daniel Suárez**
### <h1 align=center> **`Telecomunicaciones`**


El siguiente proyecto consiste en la realización de un **análisis** completo que permita reconocer el comportamiento de este sector a nivel nacional. Considere que la principal actividad de la empresa es brindar **acceso a internet**, pero también es importante considerar el comportamiento asociado al resto de los servicios de comunicación, con el fin de orientar a la empresa en brindar una buena calidad de sus servicios, identificar oportunidades de crecimiento y poder plantear soluciones personalizadas a sus posibles clientes.

Enlace de GitHub: 

Las telecomunicaciones son medios electrónicos que permiten la transmisión de información entre personas, organizaciones y dispositivos a largas distancias. Estos medios incluyen la telefonía, la televisión, la radio y el internet. El internet es una red global de computadoras interconectadas que permite el intercambio de información en tiempo real. Desde su creación, ha tenido un impacto significativo en la vida de las personas, transformando la manera en que nos comunicamos, trabajamos, aprendemos y nos entretenemos.

En Argentina, la industria de las telecomunicaciones ha sido un factor clave en la transformación digital del país. Por otra parte, la pandemia mundial ha acelerado aún más la adopción de tecnologías digitales, lo que ha llevado a un aumento en la demanda de servicios de telecomunicaciones.

La transferencia de datos y comunicación en Argentina se realiza en su mayoría a través de internet, líneas telefónicas fijas y telefonía móvil. Los servicios de internet son proporcionados por varios proveedores, incluyendo empresas de telecomunicaciones y proveedores de servicios de internet. Además, el gobierno argentino ha tomado medidas para mejorar la conectividad en todo el país, incluyendo la implementación de programas de banda ancha y la construcción de infraestructura de telecomunicaciones.
En resumen, las telecomunicaciones y el internet han transformado la forma en que nos comunicamos y han permitido la transmisión de información a largas distancias en Argentina, lo que ha tenido un impacto significativo en la vida de las personas y en la economía del país.

En el presente análisis se pretende expresar las recomendaciones en base a los datos públicos extraídos directamente del sitio web del Ente Nacional de Comunicaciones (ENACOM, https://datosabiertos.enacom.gob.ar) de Argentina, además de datos de estructura poblacional residenciados en Argentina, datos extraídos del sitio web del Ministerio del Interior de Argentina (Dirección Nacional de Población, https://www.argentina.gob.ar/interior/renaper).

En primer lugar, se realiza la extracción de datos de la paginas web anteriormente mencionadas. a pesar de existir diferentes datas para diferentes renglones, se decidió hacer el análisis en base a las provincias del país, por lo tanto, los datasets extraídos fueron:

-	historico_velocidad_internet.xlsx
-	Internet_Accesos-por-tecnologia.xlsx
-	Internet_BAF.xlsx
-	Internet_Penetracion.xlsx
-	poblacion_identificada.csv

una vez obtenidos los datos, se procede a unificar las tablas que están relacionadas, esto se hizo a través de Excel y Python, de esta manera se generan nuevas tablas para su respectivo análisis. Las tablas generadas fueron: 

-	cobertura_provincia_2022.csv
-	data_mod.csv


## <h1 align=center> **`Análisis Exploratorio De Datos`**

Documento: EDA_PI2.ipynb

El código desarrollado realiza varias operaciones en un DataFrame de pandas llamado 'data', la cual contiene información sobre diferentes tipos de acceso a internet y sus usos en un período de tiempo (2014-2022). Y se llevó a cabo de la siguiente manera:

**1.- Detección de Outliers**

De acuerdo a lo observado en la descripción estadística y los gráficos generados de las variables numéricas se pudo notar la presencia de outliers en las siguientes variable: ‘Total’, los valores considerados fuera de parámetros fueron tratados de igual manera que los demás datos ya que son datos oficiales y no se consideran errados.

Se calculan los cuartiles y el rango intercuartílico (IQR) de la columna 'Total' para identificar los outliers. Los outliers son valores que son significativamente diferentes de los demás en un conjunto de datos. En este caso, se utilizan los cuartiles y el IQR para definir los límites superior e inferior para los Outliers. 

**2.- Detección de valores duplicados**

Para el DataFrame utilizado no se detectaron valores duplicados.

**3.- Detección de valores faltantes**

Se calculó la cantidad de valores faltantes en cada columna del DataFrame, la cual evidenció 2 valores faltantes para la columna ‘Dial up’, los mismo fueron sustituidos por el valor medio de esa columna.

**4.- Distribución de las variables**

Consistió en la creación de varios histogramas de las variables numéricas donde se evidenció una distribución sesgada hacia la izquierda con picos de distribución bastante pronunciados en todas las variables. Esto quiere decir que todos los valores que toman las variables se concentran hacia los valores menores posibles, reduciéndose en cantidad a medida que los valores de las variables se hacen mayores. Por otra parte, la presencia de valores atípicos o ‘outliers’ puede indicar una distribución no normal. en el caso de 'Accesos por cada 100 hogares' de igual manera presenta el mismo comportamiento solo que con valores más distribuidos. (Ver Figura1- EDA_PI2.ipynb).

**5.- Relación entre las variables**

Se creó una matriz de dispersión (scatter matrix) para las variables numéricas del DataFrame. Una matriz de dispersión es una matriz de gráficos de dispersión, donde cada celda de la matriz es un gráfico de dispersión que muestra la relación entre dos variables. En ese mismo sentido también se creó un mapa de calor de estas correlaciones para representar gráficamente a través de un degradado de colores para indicar la magnitud de los valores la misma. (Ver Figura 2 y Figura 3 - EDA_PI2.ipynb).

**6.- Identificación de Patrones y Tendencias**

Para esta parte del análisis, se utilizaron librerías de visualización de datos para identificar patrones y/o tendencias en el comportamiento de las curvas generadas en los gráficos.

•	'Accesos por cada 100 hogares nacional por año'

(Ver Figura 4 - EDA_PI2.ipynb). En el Histograma de 'Accesos por cada 100 hogares Nacional por año' se evidencia un claro crecimiento en el periodo del análisis, cada año presenta un aumento con respecto al año anterior, es decir, en el periodo analizado el crecimiento ha sido constante.

•	'Accesos por cada 100 hogares Por Provincia'

(Ver Figura 5 - EDA_PI2.ipynb). Este gráfico muestra el número de accesos a internet en por cada 100 hogares Argentina por provincia desde 2014 hasta 2022. El eje 'x' representa el año y el eje 'y' representa el número de accesos a internet. Las líneas representan las diferentes provincias de Argentina. A demás, se observa una tendencia casi constante al aumento en la cantidad de accesos a internet en todas las provincias, donde la provincia de Buenos Aires presenta un notable mayor crecimiento en cantidad y proporción con respecto a las otras provincias.

•	'Acceso (uso de BAF y Dial Up) a internet nacional'

(Ver Figura 6 - EDA_PI2.ipynb). con respecto al diagrama de barras se observa una tendencia creciente constante en el número de accesos a internet a través de 'Banda ancha fija', mientras para 'Dial up' se hace casi imperceptible el uso y el efecto dado que los números de acceso a internet a través del mismo es prácticamente nulo.

•	'Acceso (uso de BAF y Dial Up) a internet por provincia'

(Ver Figura 7 - EDA_PI2.ipynb). en el grafico conjunto de uso de 'Dial up' y 'Banda ancha fija' se observan las tendencias claras en cuanto a la cantidad de accesos para cada caso, en el caso de 'Dial up' presenta una clara tendencia a la disminución a lo largo del periodo analizado, por otra parte, en el caso de uso de 'Banda ancha fija' se evidencia la tendencia clara del aumento en la cantidad en el periodo analizado.

•	'Mbps (Media de bajada) nacional por año'

(Ver Figura 8 - EDA_PI2.ipynb). en el diagrama se evidencia un claro comportamiento con tendencia al aumento proporcionalmente considerables en cuanto al promedio 'Media de bajada' a nivel nacional en el periodo desde el 2014 al 2022.

•	'Mbps (Media de bajada) Por Provincia'

(Ver Figura 9- EDA_PI2.ipynb). en la gráfica se observa la tendencia al aumento en la velocidad media de bajada por provincia, en ese sentido, también se observa, que hasta el año 2017 se presentaba un crecimiento parejo en todas las provincias, a partir de ese mismo año el crecimiento comienza a diferenciarse en proporción por provincia, siendo Capital Federal la curva con mayor crecimiento, sin que esto afecte el crecimiento de las demás provincias, es decir el crecimiento en la media de bajada para todas las provincias ha sido continuo en el periodo analizado.

•	'Total Accesos Nacional por año'

(Ver Figura 10- EDA_PI2.ipynb). En el Histograma de 'Total Accesos Nacional por año' se evidencia un claro crecimiento en el periodo del análisis, cada año presenta un aumento con respecto al año anterior, es decir, en el periodo analizado el crecimiento ha sido constante.

•	'Total Accesos Por Provincia' 

(Ver Figura 11- EDA_PI2.ipynb). Este gráfico muestra el número de accesos a internet por cada 100 hogares en Argentina por provincia desde 2014 hasta 2022. El eje 'x' representa el año y el eje 'y' representa el número de accesos a internet. Las líneas representan las diferentes provincias de Argentina. A demás, se observa una tendencia casi constante al aumento en la cantidad de accesos a internet en todas las provincias, donde la provincia de Buenos Aires presenta un notable mayor crecimiento en cantidad y proporción con respecto a las otras provincias.

•	'Acceso por Tecnología por año'

(Ver Figura 12 - EDA_PI2.ipynb). Este diagrama de barras muestra el 'Acceso por Tecnología por año' donde para todas las tecnologías en su proporción presentan un crecimiento constante a lo largo del periodo analizado, excepto para tecnología ADSL la cual presenta una tendencia a la baja considerable a partir del año 2017 hasta el final del periodo.


## <h1 align=center> **`Análisis  De Datos`**

Documento: Scripts para PBI.ipynb

**Cálculo de indicadores clave de rendimiento**

Para esta etapa del proyecto se trabajó sobre la base de la data analizada anteriormente, y se le anexa el cálculo de los indicadores clave de rendimiento planteados que se consideran relevantes para el análisis propuesto. El código desarrollado realiza varias operaciones de cálculo y manipulación de datos en el DataFrame ‘data'. En ese sentido, se definen dos funciones, calculate_kpi1 y calculate_kpi2, que calculan un indicador clave de rendimiento (KPI) para las variables 'Accesos por cada 100 hogares' y ‘Mbps (Media de bajada)' respectivamente. En estas funciones, se calcula el cambio porcentual entre los valores consecutivos de la columna especificada en el grupo de datos. Por otra parte, se calcula solo para el último trimestre del periodo analizado el ‘Porcentaje de cobertura de acceso a internet por habitantes’, esto se hace multiplicando la columna 'Total' (que representa la cantidad total de acceso a internet) por 100 y luego dividiéndolo por la columna 'Población' (que representa la población total). El resultado es un porcentaje que indica qué porcentaje de la población tiene acceso a internet. A continuación, se definen las fórmulas correspondientes para cada indicador:

1.	KPI Tasa de crecimiento Accesos por cada 100 hogares (KPI_1)

KPI_1 = ((Nuevo acceso - Acceso actual) / Acceso actual) * 100

2.	KPI Tasa de crecimiento Mbps (Media de bajada) (KPI_2)

KPI_2 = ((Media nueva - Media actual) / Media actual) * 100

3.	KPI Porcentaje de cobertura de acceso a internet por habitantes

% Cobertura = (‘Total’ * 100) / ‘Población’

**Análisis De Gráficos, Métricas E Indicadores De Rendimiento**

**Contexto General**

<img src ="src\media_baja_año.png">


En el periodo seleccionado para el análisis, se observa un comportamiento con tendencia al aumento proporcionalmente considerable en cuanto a la media de bajada a nivel nacional en el periodo desde el 2014 al 2022.La media de bajada se refiere a la velocidad de descarga de datos desde internet a un dispositivo. En otras palabras, es la velocidad a la que los datos fluyen desde el servidor de internet al dispositivo del usuario. La velocidad de descarga se mide en megabits por segundo (Mbps). La tendencia al aumento en la media de bajada indica que la velocidad de descarga de datos ha aumentado en el país en el periodo seleccionado. El aumento en la velocidad de descarga de datos puede deberse a una variedad de factores, como mejoras en la infraestructura de internet, actualizaciones en los dispositivos de los usuarios, etc. Por otra parte, la gráfica de ‘Mbps (Media de bajada) por año’ muestra que el último periodo, es decir, desde el 2021 al 2022, tuvo el mayor incremento en la velocidad del internet. Es importante destacar que la gráfica representa de manera absoluta la tendencia general en todo el país, lo que sugiere que el aumento en la velocidad de descarga de datos se ha producido en todas las provincias del país. Además, el cálculo de Tasa de crecimiento Accesos por cada 100 hogares (KPI_1) es de 1,77 en promedio para el periodo seleccionado, es decir, en cada trimestre del periodo hubo un incremento de 1,77 % en la cantidad de accesos a internet por cada 100 hogares, así como también, para la Tasa de crecimiento Mbps (Media de bajada) (KPI_2) se registró un valor de 7,10% de incremento promedio trimestral a nivel nacional.


<img src ="src\acceso_100_hog.png">


El gráfico de barras de ‘Accesos por cada 100 hogares Nacional por año’ muestra un claro crecimiento en el periodo del análisis 2014 - 2022. Cada año presenta un aumento con respecto al año anterior, lo que indica que el crecimiento ha sido constante en el periodo analizado. En total, el número de accesos casi se ha duplicado en 8 años. El aumento constante en el número de accesos indica que cada vez más hogares tienen acceso a internet. En ese sentido, cabe destacar que el crecimiento en el número de accesos se ha producido en todo el país, lo que sugiere que el acceso a internet se ha expandido a todas las provincias del país. Este crecimiento es una buena señal para el desarrollo del país, ya que el acceso a internet es un factor clave para el desarrollo económico y social.


<img src ="src\du_baf.png">


El gráfico conjunto de uso de ‘Dial up’ y ‘Banda ancha fija’ muestra dos tendencias claras en cuanto a la cantidad de accesos para cada caso. En el caso de ‘Dial up’, se observa una clara tendencia a la disminución a lo largo del periodo analizado. Por otra parte, en el caso de uso de ‘Banda ancha fija’, se evidencia la tendencia clara del aumento en la cantidad en el periodo analizado. ‘Dial up’ y ‘Banda ancha fija’ son dos tecnologías de acceso a internet. ‘Dial up’ es una tecnología de acceso a internet que utiliza la línea telefónica para conectarse a internet. La velocidad de conexión es limitada y depende de la calidad de la línea telefónica. ‘Banda ancha fija’, por otro lado, es una tecnología de acceso a internet que utiliza una conexión de cable o fibra óptica para conectarse a internet. La velocidad de conexión es mucho mayor que la de ‘Dial up’. En ese sentido, podemos concluir que la tendencia a la disminución en el uso de ‘Dial up’ se debe a la obsolescencia de esta tecnología dado que la velocidad de conexión es muy baja en comparación con la de ‘Banda ancha fija’. Además, la calidad de la línea telefónica puede afectar la velocidad de conexión. Por otro lado, la tendencia al aumento en el uso de ‘Banda ancha fija’ se debe a la creciente demanda de acceso a internet de alta velocidad. La tecnología de ‘Banda ancha fija’ ofrece una velocidad de conexión mucho mayor que la de ‘Dial up’. Así mismo, la calidad de la conexión es más estable y no se ve afectada por la calidad de la línea telefónica.  que estas tendencias se han replicado en todo el país, lo que significa que el acceso a internet se ha expandido a todas las provincias.


<img src ="src\uso_tecnologia.png">


El gráfico de barras ‘Acceso por Tecnología por año’ muestra que todas las tecnologías de acceso a internet presentan un crecimiento constante en su proporción a lo largo del periodo analizado, excepto la tecnología ADSL, que presenta una tendencia a la baja considerable a partir del año 2017 hasta el final del periodo. ADSL es una tecnología de acceso a internet que utiliza la línea telefónica para conectarse a internet. La velocidad de conexión es limitada y depende de la calidad de la línea telefónica. En comparación con otras tecnologías de acceso a internet que usan banda ancha fija como lo son: la fibra óptica y el cable modem, la velocidad de conexión de ADSL es mucho menor. La tendencia a la baja en el uso de ADSL está estrechamente relacionada al bajo uso del ‘Dial Up’.
Es importante destacar que el crecimiento en el uso de otras tecnologías de acceso a internet se ha producido en todo el país y la tendencia a desaparecer la tecnología de ADSL, lo cual supone oportunidades en cuanto a la sustitución de esa tecnología en zonas donde todavía exista un uso relativamente considerable, por las tecnologías de vanguardia que ofrezcan mejor servicio en cuanto al acceso y a velocidades de navegación.



## <h1 align=center> **`Conclusiones y Recomendaciones Generales`**

**Conclusiones**

1.- El número de accesos a internet por cada 100 hogares ha crecido de forma constante en el periodo 2014-2022, lo que indica que hay una demanda creciente de este servicio en el país.

2.- La tendencia al aumento en la media de bajada indica que la velocidad de descarga de datos ha aumentado en el país en el periodo seleccionado. El aumento en la velocidad de descarga de datos puede deberse a una variedad de factores, como mejoras en la infraestructura de internet, actualizaciones en los dispositivos de los usuarios, etc.

3.- desde el 2021 al 2022, tuvo el mayor incremento en la velocidad del internet.

4.- el cálculo de Tasa de crecimiento Accesos por cada 100 hogares (KPI_1) es de 1,77 en promedio para el periodo seleccionado, mientras que para la Tasa de crecimiento Mbps (Media de bajada) (KPI_2) se registró un valor de 7,10% de incremento promedio trimestral a nivel nacional.

5.-  Cada año, el número de accesos ha aumentado con respecto al año anterior, lo que indica que el crecimiento ha sido sostenido. En total, el número de accesos casi se ha duplicado en 8 años. Este aumento constante en el número de accesos sugiere que cada vez más hogares tienen acceso a internet, lo que es una buena señal para el desarrollo económico y social del país.
6.- podemos concluir que la tendencia a la disminución en el uso de ‘Dial up’ se debe a la obsolescencia de esta tecnología dado que la velocidad de conexión es muy baja en comparación con la de ‘Banda ancha fija’.

7.- El uso de tecnologías de banda ancha fija, como la fibra óptica y el cable modem, ha aumentado en el mismo periodo, lo que indica que los usuarios prefieren una conexión de alta velocidad y calidad. La tecnología de ‘Banda ancha fija’ ofrece una velocidad de conexión mucho mayor que la de ‘Dial up’.

8.- todas las tecnologías de acceso a internet presentan un crecimiento constante en su proporción a lo largo del periodo analizado, excepto la tecnología ADSL, que presenta una tendencia a la baja considerable a partir del año 2017 hasta el final del periodo.

9.- En comparación con otras tecnologías de acceso a internet que usan banda ancha fija como lo son: la fibra óptica y el cable modem, la velocidad de conexión de ADSL es mucho menor.

10.- La tendencia a la baja en el uso de ADSL está estrechamente relacionada al bajo uso del ‘Dial Up’.


**Recomendaciones**

1.- Debido a la alta demanda y al constante crecimiento de los accesos a internet a nivel nacional se recomienda invertir en infraestructura y tecnologías actualizadas dado que el crecimiento de ahora en más se hará exponencial, ya que el acceso a internet es un factor clave para el desarrollo económico y social, puesto que permite la comunicación, la información, la educación, el entretenimiento, el comercio, etc. Todo esto con una visión estratégica enfocada en la expansión general tanto como en número de accesos como aumento de velocidad de bajada a nivel nacional.

2.- El uso de tecnologías obsoletas, como el dial up y el ADSL, ha disminuido en el mismo periodo, lo que indica que hay oportunidades de sustituir estas tecnologías por otras más avanzadas en las zonas donde todavía existan.
3.- se recomienda la adquisición de equipos y prestaciones de servicios especializados en la tecnología de fibra óptica, ya que la misma se mantiene en constante crecimiento en la adquisición por parte de potenciales clientes.

4.- se recomienda mantener el mismo impulso con la tecnología de cable modem, ya que la misma representa una opción accesible, económica y con buen servicio, por tales razones se mantiene como la opción preferida en el uso de tecnologías de acceso a internet.

5.- especial atención para áreas rurales, donde a menudo están desatendidas debido a los costos de construir infraestructura de red como cables y torres de transmisión. Esto puede dificultar tu búsqueda de la mejor opción de banda ancha de alta velocidad para áreas rurales. Para casos de zonas desatendidas, se presume es por el difícil acceso y falta de infraestructura, se recomienda crear planes de financiamiento, de sustitución de tecnologías obsoletas y de servicios tipo ‘Wireless’ o internet satelital.




El estatus correspondiente al proyecto es de: completo/publicado.
# Data_Analyst_PI2
