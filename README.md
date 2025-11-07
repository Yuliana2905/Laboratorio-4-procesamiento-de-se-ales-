# Laboratorio 4 procesamiento de señales
# Señales electromiográficas EMG 
## Docente: Erick Javier Arguello Prada
## Integrantes:
## ·Liseth Yuliana Clavijo 
## ·Maria Camila Rodriguez
## ·Adriana Valentina Alarcon 
## Fecha: Octubre 2025
# Introduccion: 
La electromiografía (EMG) es una técnica utilizada para registrar y analizar la actividad eléctrica generada por los músculos durante la contracción. Esta señal refleja la activación de las unidades motoras y permite estudiar el comportamiento fisiológico del músculo, incluyendo la aparición de fatiga. En el ámbito del procesamiento digital de señales, el análisis de señales EMG resulta fundamental para el desarrollo de aplicaciones biomédicas orientadas al diagnóstico, la rehabilitación y el control de prótesis.
Durante el desarrollo del laboratorio se realiza la adquisición, filtrado y análisis espectral de señales EMG emuladas y reales, con el fin de identificar la variación de parámetros como la frecuencia media y la frecuencia mediana a lo largo de contracciones sucesivas. La disminución progresiva de estas frecuencias se asocia con la fatiga muscular, fenómeno que puede ser evaluado mediante la Transformada Rápida de Fourier (FFT). Este proceso permite correlacionar los cambios en el contenido frecuencial con el esfuerzo sostenido y la pérdida de rendimiento muscular.

<img width="474" height="632" alt="image" src="https://github.com/user-attachments/assets/45a2c3de-f478-46d5-894c-fc587f97d126" />

# Objetivos: 
- Aplicar el filtrado de señales continuas para procesar una señal electromiográfica 
(EMG).
- Detectar la aparición de fatiga muscular mediante el análisis espectral de 
contracciones musculares individuales. 
- Comparar el comportamiento de una señal emulada y una señal real en términos 
de frecuencia media y mediana. 
- Emplear herramientas computacionales para el procesamiento, segmentación y 
análisis de señales biomédicas.


# Marco teorico:

## Señal electromiográfica (EMG)

La señal EMG es el resultado de la superposición de los potenciales de acción generados por las unidades motoras del músculo. Se caracteriza por ser una señal aleatoria, no estacionaria y de amplitud variable, generalmente en el rango de 0 a 5 mV y con un contenido de frecuencia entre 20 y 450 Hz.

Matemáticamente, la señal EMG puede expresarse como:

<img width="251" height="90" alt="image" src="https://github.com/user-attachments/assets/02d10591-3ca8-4c6a-8bdb-16739e082471" />

Donde:

x(t) es la señal EMG total
mi​(t) representa el potencial de acción de la i-ésima unidad motora
τi es el retardo temporal correspondiente a su activación

## Filtrado de la señal

El objetivo del filtrado es eliminar ruido y artefactos provenientes de fuentes externas o del propio cuerpo. Para la señal EMG, se utiliza un filtro pasa banda entre 20 Hz y 450 Hz, que permite conservar el contenido útil de la señal.

En el dominio de la frecuencia, el filtrado puede representarse como:

<img width="237" height="40" alt="image" src="https://github.com/user-attachments/assets/5b52e8d0-fc87-4837-9c54-4811ada92566" />


donde:

𝑋(𝑓) es la transformada de Fourier de la señal original,
𝐻(𝑓) es la función de transferencia del filtro,
𝑌(𝑓) es la señal filtrada.

## Análisis espectral y Transformada de Fourier

La Transformada de Fourier permite descomponer una señal temporal en sus componentes de frecuencia:

<img width="312" height="81" alt="image" src="https://github.com/user-attachments/assets/65cfc7ed-e5b6-42b1-ab75-094ed7f6e04f" />

En la práctica, se emplea la Transformada Rápida de Fourier (FFT) para obtener el espectro de amplitud y analizar cómo varía la potencia en distintas bandas de frecuencia durante las contracciones musculares.

## Frecuencia media y mediana

El análisis espectral de la EMG se basa en el cálculo de parámetros que describen el contenido frecuencial:

### Frecuencia media (𝑓𝑚𝑒d)

<img width="298" height="107" alt="image" src="https://github.com/user-attachments/assets/ab82b792-7d2b-472f-897e-20daeb31352f" />

donde 
𝑃(𝑓𝑖)
P(fi) es la densidad espectral de potencia en la frecuencia 

### Frecuencia mediana (𝑓𝑚𝑒𝑑)

Es aquella frecuencia que divide el área bajo la curva de potencia en dos partes iguales:

<img width="384" height="86" alt="image" src="https://github.com/user-attachments/assets/545a92d6-cff9-4d7c-822a-79a81988110e" />

Durante la fatiga muscular, ambas frecuencias tienden a desplazarse hacia valores menores, indicando una reducción en la velocidad de conducción de las fibras musculares y un cambio en el reclutamiento de unidades motoras.

## Fatiga muscular

La fatiga se define como la disminución de la capacidad del músculo para generar fuerza. En el contexto del análisis EMG, se manifiesta como una disminución del contenido de alta frecuencia en el espectro, producto del enlentecimiento de la propagación del potencial de acción. Este fenómeno puede ser cuantificado observando la tendencia decreciente de 
𝑓𝑚𝑒d y 𝑓𝑚𝑒𝑑 a lo largo de contracciones repetidas.

<img width="379" height="384" alt="image" src="https://github.com/user-attachments/assets/cb5acae4-a8e0-4720-8383-1d62fc5e6d48" />


# Metodología Experimental

El desarrollo experimental se dividió en tres etapas principales: captura de señal emulada, adquisición de señal real y análisis espectral mediante FFT.

### 1. Captura de señal emulada

Se configuró el generador de señales biológicas en modo EMG para simular aproximadamente cinco contracciones musculares voluntarias.

Se registró la señal obtenida mediante un sistema de adquisición (DAQ).

La señal fue segmentada en cinco partes, cada una correspondiente a una contracción.

Para cada segmento, se calculó la frecuencia media y mediana utilizando la densidad espectral de potencia obtenida mediante FFT.

Se representó gráficamente la evolución de dichas frecuencias para observar tendencias.

#### 2. Captura de señal real

Se colocaron tres electrodos de superficie sobre un grupo muscular (por ejemplo, el bíceps), asegurando el contacto con gel conductor y la piel limpia.

El voluntario realizó contracciones repetidas hasta la aparición de fatiga.

La señal capturada fue filtrada con un pasa banda de 20–450 Hz para eliminar ruido.

Se segmentó la señal en las contracciones individuales y se calcularon 
𝑓𝑚𝑒d y 𝑓𝑚𝑒𝑑 de cada una.

Los resultados se graficaron para analizar la evolución de las frecuencias en función del esfuerzo.

### 3. Análisis espectral (FFT)

Se aplicó la Transformada Rápida de Fourier (FFT) a cada contracción de la señal real.

Se obtuvieron los espectros de amplitud para las contracciones iniciales y finales.

Se compararon los resultados observando la reducción del contenido de alta frecuencia en las últimas contracciones.

Se discutió la relación entre estos cambios espectrales y los mecanismos fisiológicos de la fatiga muscular.


# Procedimiento y resultados:
### PARTE A – Captura de la señal emulada 
a. Configurar el generador de señales biológicas en modo EMG, simulando 
aproximadamente cinco contracciones musculares voluntarias. 
b. Adquirir y almacenar la señal generada para su posterior análisis. 
c. Segmentar la señal obtenida en las cinco contracciones simuladas. 
d. Calcular para cada contracción: 
- Frecuencia media  
- Frecuencia mediana  
e. Presentar los resultados de cada contracción en una tabla y representar 
gráficamente la evolución de las frecuencias. 
f. 
Analizar cómo varían estas frecuencias a lo largo de las contracciones 
simuladas.
## Procedimiento 
Se utilizó un generador de señales biológicas para simular la actividad eléctrica muscular (EMG). En el canal 1 se configuró el modo Arbitrary (Arb) con la función EMG, estableciendo una frecuencia portadora de 1 Hz y una frecuencia de modulación de 1 MHz en modo AM (amplitud simulada), con una profundidad de modulación del 1 %. La amplitud se fijó en 5 Vpp, generando una señal que simula contracciones musculares periódicas.

La señal emulada se adquirió mediante el sistema de adquisición de datos (DAQ) y se almacenó para su análisis digital. Posteriormente, se segmentó en cinco contracciones simuladas, cada una representando un ciclo de activación muscular.

Para cada contracción se realizó el análisis espectral, donde se determinaron los valores de frecuencia media y frecuencia mediana, los cuales fueron organizados en una tabla y graficados para observar su evolución a lo largo de las contracciones.

<img width="1016" height="301" alt="image" src="https://github.com/user-attachments/assets/7c90958a-4f0c-4318-8d8f-67f502ca8ea2" />

Imagen 1. Señal obtenida por medio del generador de señales biologicas

Posteriormente se realiza el cálculo de la frecuencia media y la frecuencia mediana para cada contracción lo cual permite caracterizar el contenido espectral de la señal EMG, es decir cómo se distribuye la energía en las diferentes frecuencias. Al calcular ambas frecuencias para cada una de las cinco contracciones simuladas, se obtiene una descripción cuantitativa de cómo varía el comportamiento frecuencial de la señal EMG a lo largo del tiempo. Esto permite analizar si existen cambios progresivos en la activación simulada del músculo o si la señal mantiene una respuesta estable en todas las contracciones.

```
results = []
for seg in segments:
    f, Pxx = signal.welch(seg, fs, nperseg=1024)
    mean_freq = np.sum(f * Pxx) / np.sum(Pxx)
    median_freq = f[np.where(np.cumsum(Pxx) >= np.sum(Pxx) / 2)[0][0]]
    results.append([mean_freq, median_freq])

df = pd.DataFrame(results, columns=["Frecuencia Media (Hz)", "Frecuencia Mediana (Hz)"])
df.index = [f"Contracción {i+1}" for i in range(len(segments))]

display(df)
```

<img width="502" height="108" alt="image" src="https://github.com/user-attachments/assets/8e790466-9474-452b-bb3c-90e425805f22" />
Imagen 2.Tabla de valores 


En la tabla se presentan los valores de frecuencia media y frecuencia mediana correspondientes a cinco contracciones musculares extraídas de la señal EMG. Estos parámetros reflejan la distribución de energía en el espectro de la señal y están directamente relacionados con la actividad eléctrica de las fibras musculares durante la contracción.
Los valores de frecuencia media y frecuencia mediana obtenidos para las cinco contracciones emuladas se mantienen prácticamente constantes, con ligeras variaciones dentro de un rango estrecho (entre 98 y 99 Hz para la frecuencia media y alrededor de 95 Hz para la mediana).
Esto indica que la distribución de energía en el espectro de la señal EMG emulada no presenta cambios significativos entre contracciones, lo que es coherente con una señal generada artificialmente, en la cual no existe fatiga muscular ni variaciones fisiológicas.
En consecuencia, la estabilidad de estos parámetros confirma que la señal simulada reproduce de manera controlada la actividad eléctrica muscular y permite validar el procedimiento de segmentación y análisis espectral antes de aplicar el mismo método a señales reales.


## Análisis

La señal generada mediante modulación en amplitud reproduce de manera controlada la actividad eléctrica que se origina en el músculo durante la contracción. La portadora de alta frecuencia (1 MHz) representa la actividad eléctrica de las fibras musculares, mientras que la señal moduladora de baja frecuencia (1 Hz) simula la contracción y relajación periódica del músculo.

Al tratarse de una señal emulada, no se observan cambios significativos en las frecuencias a lo largo de las contracciones, lo que indica ausencia de fatiga muscular. No obstante, este proceso permite validar la correcta configuración del equipo, la segmentación de la señal y el análisis de su comportamiento espectral, fundamentos esenciales para el estudio de señales EMG reales.



### PARTE B – Captura de la señal de paciente 
a. Colocar los electrodos sobre el grupo muscular definido por el grupo (por 
ejemplo, antebrazo o bíceps). 
b. Registrar la señal EMG de un paciente o voluntario sano realizando 
contracciones repetidas hasta la fatiga (o la falla). 
c. Aplicar un filtro pasa banda (20–450 Hz) para eliminar ruido y artefactos. 
d. Dividir la señal en el número de contracciones realizadas.
e. Calcular para cada contracción: 
-Frecuencia media  
-Frecuencia mediana  
f. 
Graficar los resultados obtenidos y analizar la tendencia de la frecuencia 
media y mediana a medida que progresa la fatiga muscular. 
g. Discutir la relación entre los cambios de frecuencia y la fisiología de la fatiga 
muscular. 

### PARTE C – Análisis espectral mediante FFT 
a. Aplicar la Transformada Rápida de Fourier (FFT) a cada contracción de la 
señal EMG real. 
b. Graficar el espectro de amplitud (frecuencia vs. magnitud) para observar 
cómo cambia el contenido de frecuencia. 
c. Comparar los espectros de las primeras contracciones con los de las últimas. 
d. Identificar la reducción del contenido de alta frecuencia asociada con la fatiga 
muscular.  
e. Calcular y discutir el desplazamiento del pico espectral y su relación con el 
esfuerzo sostenido. 
f. 
Redactar conclusiones sobre el uso del análisis espectral como herramienta 
diagnóstica en electromiografía.
