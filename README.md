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

```python
plt.figure(figsize=(12,3))
plt.plot(t, data, label="Señal EMG")
for s, e in segments:
    plt.axvspan(s/FS, e/FS, color='pink', alpha=0.25)
plt.xlabel("Tiempo (s)")
plt.title("Señal EMG Segmentada en 5 Contracciones")
plt.show()

```
<img width="1016" height="301" alt="image" src="https://github.com/user-attachments/assets/7c90958a-4f0c-4318-8d8f-67f502ca8ea2" />

Imagen 1. Señal obtenida por medio del generador de señales biologicas

Posteriormente se realiza el cálculo de la frecuencia media y la frecuencia mediana para cada contracción lo cual permite caracterizar el contenido espectral de la señal EMG, es decir cómo se distribuye la energía en las diferentes frecuencias. Al calcular ambas frecuencias para cada una de las cinco contracciones simuladas, se obtiene una descripción cuantitativa de cómo varía el comportamiento frecuencial de la señal EMG a lo largo del tiempo. Esto permite analizar si existen cambios progresivos en la activación simulada del músculo o si la señal mantiene una respuesta estable en todas las contracciones.

```python
for i, (s, e) in enumerate(segments, start=1):
    seg = data[s:e]
    meanf, medf = mean_median_freq(seg, FS)
    results.append([i, meanf, medf])

df = pd.DataFrame(results, columns=["Contracción", "Frecuencia Media (Hz)", "Frecuencia Mediana (Hz)"])
print(df)
```

<img width="502" height="108" alt="image" src="https://github.com/user-attachments/assets/8e790466-9474-452b-bb3c-90e425805f22" />


Imagen 2.Tabla de valores frecuencia media y frecuencia mediana


En la señal EMG real se observa que la frecuencia media presenta valores entre 76 y 78 Hz, mientras que la frecuencia mediana permanece prácticamente constante alrededor de 9.76 Hz.
Aunque las variaciones son leves, se aprecia una tendencia general al descenso de la frecuencia media conforme avanzan las contracciones. Este comportamiento indica una reducción progresiva del contenido de alta frecuencia en el espectro de la señal, lo cual es un indicador de fatiga muscular.

La disminución de la frecuencia media está asociada con la disminución de la velocidad de conducción de las fibras musculares y con el cambio en el reclutamiento de unidades motoras durante el esfuerzo repetido.
En contraste con la señal emulada, estos resultados reflejan un proceso fisiológico real, donde el músculo presenta adaptaciones eléctricas al mantener contracciones sostenidas, evidenciando la transición hacia la fatiga.

```python
plt.figure(figsize=(6,3))
plt.plot(df["Contracción"], df["Frecuencia Media (Hz)"], marker='o', label="Frecuencia Media")
plt.plot(df["Contracción"], df["Frecuencia Mediana (Hz)"], marker='s', label="Frecuencia Mediana")
plt.xlabel("Contracción")
plt.ylabel("Frecuencia (Hz)")
plt.title("Evolución de las Frecuencias por Contracción")
plt.legend()
plt.grid(alpha=0.4)
plt.show()
```


<img width="531" height="317" alt="image" src="https://github.com/user-attachments/assets/b4c6d869-197f-41fe-bdd9-7ca050f995d0" />


Imagen 3.Evolucion de frecuencias por contracciones


Ambas curvas son casi planas, lo que indica poca variación en las frecuencias a lo largo de las contracciones.

La frecuencia media es mucho mayor que la frecuencia mediana, lo cual puede significar que hay valores altos aislados (picos) en la señal que elevan la media pero no afectan tanto la mediana.

En estudios de fatiga muscular, por ejemplo, se esperaría que estas frecuencias disminuyeran con el tiempo; aquí, como se mantienen constantes, se podría concluir que no hay signos claros de fatiga durante las contracciones registradas.



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


#### a) Electrodos
Ya que no contábamos con el modulo de EMG, se implementó el modulo AD8232 de ECG para poder hacer la captura de la señal electromiografía superficial por medio de electrodos, aprovechando que este modulo tiene la capacidad de detectar el diferencial de potenciales eléctricos en la piel. Los electrodos se colocaron de manera superficial sobre el brazo izquierdo de una paciente sana, naturalmente diestra de 19 años, siguiendo esta disposición:

Electrodo verde (GND): Se ubicó sobre el codo, haciendo de este una referencia eléctrica.

Electrodo rojo: sobre la parte proximal del musculo braquiorradial, cerca al codo.

Electrodo amarillo: posición distal mas proximal a la muñeca.

<img width="800" height="936" alt="image" src="https://github.com/user-attachments/assets/04b950bc-f4df-438e-a9e1-4a1b34a75a7d" />


El antebrazo izquierdo, al ser no dominante, presenta menor entrenamiento motor, lo que puede reflejarse en una menor amplitud de señal y una aparición más lenta de la fatiga. Lo cual en ese momento no teníamos conocimiento, pero es un dato importante para la amplitud de la señal.


### b) Registro de la señal


<img width="1001" height="393" alt="image" src="https://github.com/user-attachments/assets/0b5fd095-0ab8-4e83-b845-c0332d573d45" />

Imagen 4.Señal EMG obtenida
### c) Filtro Pasa banda

<img width="999" height="470" alt="image" src="https://github.com/user-attachments/assets/f311368e-7486-42c1-b89b-f0aafe3d5d08" />
La señal original (en color azul) presenta una amplitud mayor y un nivel medio desplazado hacia valores positivos, lo cual indica la presencia de un componente de corriente continua (DC) y de ruido de baja frecuencia producido por el movimiento o interferencias externas. Además, se observan picos irregulares y variaciones bruscas que dificultan la interpretación de la actividad muscular real.

Por otro lado, la señal filtrada (en color naranja) se encuentra centrada alrededor de cero voltios y presenta una amplitud más estable. El filtrado pasa banda eliminó los componentes de baja frecuencia (<20 Hz), asociados a artefactos por movimiento, y los de alta frecuencia (>450 Hz), relacionados con el ruido electrónico. De esta forma, se conserva únicamente el rango de frecuencia donde se encuentra la información útil del potencial eléctrico muscular.
### d) Espectro de frecuencia
<img width="670" height="352" alt="image" src="https://github.com/user-attachments/assets/63ddd06c-4be4-439f-9218-5044fbff9095" />

Se aplicó la Transformada Rápida de Fourier (FFT) para trasladar la señal del dominio temporal al dominio frecuencial, lo que permitió determinar las regiones donde se concentraba la mayor parte de la energía muscular. En las señales EMG, la energía principal suele ubicarse entre los 40 y 150 Hz, aunque pueden aparecer otros picos dependiendo del músculo analizado y del tipo de contracción realizada.

### e) Tabla con los calculos de las contracciones
<img width="386" height="141" alt="image" src="https://github.com/user-attachments/assets/7270aca9-2197-4792-9eb6-f361e351b826" />

La tabla presenta las frecuencias medias y medianas calculadas para cinco contracciones musculares.
Las frecuencias medias se encuentran entre 44.57 Hz y 48.91 Hz,
Las frecuencias medianas entre 39.02 Hz y 48.82 Hz.
Estos valores indican que la distribución de energía de la señal EMG se mantiene dentro del rango típico de 40 a 60 Hz, coherente con la literatura para señales musculares.
La consistencia de los valores entre contracciones sugiere que el músculo analizado mantiene un patrón de activación estable, sin variaciones bruscas que indiquen fatiga o interferencias externas. En particular, las contracciones 1 y 5 presentan frecuencias medianas ligeramente más altas (~48 Hz), lo que podría reflejar una mayor activación o fuerza de contracción en esos casos.
### f) Grafica de los resultados y fatiga muscular 
<img width="545" height="289" alt="image" src="https://github.com/user-attachments/assets/931a3633-a812-47a1-a275-ff0ce47fe9b5" />

La gráfica evidencia un proceso de fatiga temporal caracterizado por una disminución inicial de las frecuencias (especialmente la mediana) y una recuperación posterior. Esto sugiere que el músculo experimentó un agotamiento transitorio de sus unidades motoras, seguido por una fase de recuperación o compensación.

## Análisis
Este filtrado tiene como objetivo eliminar las componentes que no corresponden a la actividad muscular.

<20 Hz son por lo general respiración o movimientos de la voluntaria
450 Hz ruido natural de la corriente eléctrica El uso de filtfilt es para que se filtre sin que haya un desfase, manteniendo así la alineación temporal de la señal El filtro implementado es de tipo Butterworth, este se implementó por su respuesta plana, sin ondulaciones y su atenuación progresiva que no cambia la morfología de la señal. Este filtro mantiene la forma real de la señal muscular y mininiza el riesgo de amplificar ruidos no deseados.


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

f. Redactar conclusiones sobre el uso del análisis espectral como herramienta 
diagnóstica en electromiografía.


El objetivo al aplicar la transformada rápida de Fourier a una señal electromiografía real con el fin de analizar los cambios en el contenido de frecuencia durante múltiples contracciones musculares y determinar como la fatiga muscular afecta la distribución espectral de esta señal.
Procedimiento.
 Se trabajo una señal EMG real registrada durante una serie de contracciones musculares voluntarias, el archivo fue cargado en Google Colab
A partir de los intervalos de tiempo entre estas muestras se estima una frecuencia de muestreo (fs) para así poder reconocer la resolución temporal y espectral de este registro.
Se aplico un filtro pasa banda de 20 a 450 Hz que corresponde al rango de frecuencias útiles de EMG este con el fin de eliminar ruido de baja frecuencia y altas frecuencias no asociadas con la actividad muscular.
La señal fue enviada en múltiples segmentos equivalentes, representando diferentes contracciones musculares, cada una de estas fue analizada por separado para observar su comportamiento espectral.
A cada contracción se le aplico la FFT para obtener el espectro de amplitud entre la frecuencia y la magnitud esto permite visualizar que componentes de frecuencia predominan durante cada una de las contracciones

Para cada contracción se identifica la frecuencia con mayor amplitud la cual indica el componente más dominante del espectro, este valor fue comparado entre contracciones iniciales y finales.
por utlimo se graficaron los espectros de tres contracciones representativas.
la primera contraccion inicio del esfuerzo
la segunda contraccion mitad del esfuerzo
la ultima contraccion fase de fatiga


#codigo 
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy.signal import butter, filtfilt, welch

ruta = '/content/Captura_1_REAL.txt'

data = np.loadtxt(ruta, skiprows=1)
tiempo = data[:,0]
voltaje = data[:,1]
fs = 1.0 / np.mean(np.diff(tiempo))
print(f"Frecuencia de muestreo estimada: {fs:.1f} Hz")

duracion = 30.0
mask = tiempo <= duracion
tiempo_30 = tiempo[mask]
voltaje_30 = voltaje[mask]


lowcut, highcut, order = 20.0, 500.0, 4
b, a = butter(order, [lowcut/(fs/2), highcut/(fs/2)], btype='band')
voltaje_filtrado = filtfilt(b, a, voltaje_30)


n_contr = 460
segmentos = np.array_split(voltaje_filtrado, n_contr)
tiempos_seg = np.array_split(tiempo_30, n_contr)
print(f"Segments: {len(segmentos)} (longitudes min/max = {min(len(s) for s in segmentos)} / {max(len(s) for s in segmentos)})")

resultados = []
for i, seg in enumerate(segmentos, start=1):
    if len(seg) < 4:

        resultados.append([i, np.nan, np.nan, np.nan, np.nan])
        continue

    nperseg = min(1024, len(seg))
    f, Pxx = welch(seg, fs=fs, nperseg=nperseg)
    # frecuencia media (centroide)
    f_media = np.sum(f * Pxx) / np.sum(Pxx)
    # frecuencia mediana (50% de energía acumulada)
    energia_acum = np.cumsum(Pxx)
    idx_med = np.where(energia_acum >= energia_acum[-1]/2)[0]
    if idx_med.size == 0:
        f_med = np.nan
    else:
        f_med = f[idx_med[0]]
    # pico espectral (frecuencia de máxima magnitud)
    f_pico = f[np.argmax(Pxx)]
    # proporción de potencia en altas frecuencias (>200 Hz)
    mask_high = f > 200
    if np.sum(Pxx) > 0:
        ratio_high = np.sum(Pxx[mask_high]) / np.sum(Pxx)
    else:
        ratio_high = np.nan

    resultados.append([i, f_media, f_med, f_pico, ratio_high])

# Tabla
df_res = pd.DataFrame(resultados, columns=['Contracción','Frecuencia_media_Hz','Frecuencia_mediana_Hz','Frecuencia_pico_Hz','Ratio_potencia_>200Hz'])
display(df_res.head(10))


plt.figure(figsize=(10,4))
plt.plot(df_res['Contracción'], df_res['Frecuencia_media_Hz'], '-o', markersize=3, label='Frecuencia media')
plt.plot(df_res['Contracción'], df_res['Frecuencia_mediana_Hz'], '-s', markersize=3, label='Frecuencia mediana')
plt.plot(df_res['Contracción'], df_res['Frecuencia_pico_Hz'], '-^', markersize=3, label='Frecuencia pico')
plt.xlabel('Contracción')
plt.ylabel('Frecuencia (Hz)')
plt.title('Evolución de frecuencias por contracción (460)')
plt.legend()
plt.grid(True, linestyle='--', alpha=0.5)
plt.tight_layout()
plt.show()


plt.figure(figsize=(10,3))
plt.plot(df_res['Contracción'], df_res['Ratio_potencia_>200Hz'], '-o', markersize=3)
plt.xlabel('Contracción')
plt.ylabel('Fracción potencia >200 Hz')
plt.title('Reducción del contenido de alta frecuencia ( > 200 Hz )')
plt.grid(True, linestyle='--', alpha=0.5)
plt.tight_layout()
plt.show()

indices_ejemplo = [1, int(n_contr/2), n_contr]
plt.figure(figsize=(12,6))
for idx, pos in enumerate(indices_ejemplo, start=1):
    seg = segmentos[pos-1]
    nperseg = min(1024, len(seg))
    f, Pxx = welch(seg, fs=fs, nperseg=nperseg)
    plt.subplot(3,1,idx)
    plt.semilogy(f, Pxx, linewidth=0.8)
    plt.xlim(0, 500)
    plt.ylabel('PSD')
    plt.title(f'Contracción {pos} - espectro (Welch)')
    plt.grid(True, which='both', linestyle='--', alpha=0.5)
plt.xlabel('Frecuencia [Hz]')
plt.tight_layout()
plt.show()


print("Resumen estadístico (frecuencia pico):")
print(df_res['Frecuencia_pico_Hz'].describe())


k = max(1, int(0.1 * n_contr))
prim_mean = np.nanmean(df_res['Frecuencia_media_Hz'][:k])
ult_mean = np.nanmean(df_res['Frecuencia_media_Hz'][-k:])
print(f"\nFrecuencia media promedio (primer {k} contr.): {prim_mean:.2f} Hz")
print(f"Frecuencia media promedio (último {k} contr.): {ult_mean:.2f} Hz")
if prim_mean > ult_mean:
    print("Tendencia: disminución de la frecuencia media → indicativo de fatiga.")
elif prim_mean < ult_mean:
    print("Tendencia: aumento de la frecuencia media.")
else:
    print("Tendencia: sin cambio claro en frecuencia media.")
```

tabla de contracciones y frecuencias
<img width="889" height="415" alt="image" src="https://github.com/user-attachments/assets/5a33457f-c610-40cb-82a1-26935c4e4c22" />

graficas 
<img width="1232" height="754" alt="image" src="https://github.com/user-attachments/assets/3566be62-49c8-4417-b113-f17683bdda3d" />

graficas de contracciones espectros
<img width="1163" height="593" alt="image" src="https://github.com/user-attachments/assets/b7ca8ec0-e280-43a3-9a70-145d50b2e229" />

Resumen estadístico (frecuencia pico):
count    460.000000
mean      47.499650
std       14.324735
min       15.313936
25%       30.674847
50%       46.012270
75%       61.349693
max       76.687117
Name: Frecuencia_pico_Hz, dtype: float64

Frecuencia media promedio (primer 46 contr.): 48.44 Hz
Frecuencia media promedio (último 46 contr.): 46.98 Hz
Tendencia: disminución de la frecuencia media → indicativo de fatiga.

```python

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy.signal import butter, filtfilt

ruta = '/content/Captura_1_REAL.txt'
data = np.loadtxt(ruta, skiprows=1)

tiempo = data[:, 0]
voltaje = data[:, 1]
# frecuencia de muestreo
fs = 1 / np.mean(np.diff(tiempo))
print(f"Frecuencia de muestreo estimada: {fs:.2f} Hz")

# 3.  pasa banda (20–450 Hz)
lowcut, highcut, order = 20, 450, 4
b, a = butter(order, [lowcut/(fs/2), highcut/(fs/2)], btype='band')
voltaje_filtrado = filtfilt(b, a, voltaje)

# 4. Segmentado
n_contr = 460
segmentos = np.array_split(voltaje_filtrado, n_contr)

# 5. FFT por contracción + Pico espectral
picos = []
plt.figure(figsize=(13, 8))
for i, seg in enumerate(segmentos, start=1):

    N = len(seg)
    fft_vals = np.fft.fft(seg)
    fft_freq = np.fft.fftfreq(N, 1/fs)

    mask = fft_freq > 0
    frecs = fft_freq[mask]
    amplitud = np.abs(fft_vals[mask])

    # Calcular pico espectral
    pico = frecs[np.argmax(amplitud)]
    picos.append(pico)

    # Graficar contracciones: primera, media y última
    if i in [1, int(n_contr/2), n_contr]:
        plt.plot(frecs, amplitud, label=f"Contracción {i} (pico={pico:.1f} Hz)")

plt.xlim([0, 450])
plt.title("FFT de primeras vs últimas contracciones")
plt.xlabel("Frecuencia (Hz)")
plt.ylabel("Amplitud")
plt.legend()
plt.grid()
plt.show()

# Tabla de picos para el informe
df_picos = pd.DataFrame({"Contracción": range(1, n_contr+1),
                         "Pico espectral (Hz)": picos})

display(df_picos.head())

```
<img width="552" height="350" alt="image" src="https://github.com/user-attachments/assets/9c5fd3b1-57d1-45f6-b5c9-011bf411df29" />

<img width="164" height="112" alt="image" src="https://github.com/user-attachments/assets/dc9e1948-d9ed-4166-afa2-81154c9250d4" />

en la grafica temporra EMG filtrado se puede observar una señal que es oscilantes con picos de actividad correspondientes a las contracciones musculares se observa que al inicio los piscos uslesn ser mas definidos demayor amplitud hacie el final tienden a disminuir o vokverse un poco mas irregulares debido a la fatiga muscular 
en la grafica de escros FFT cada contraccion presenta una distribucion de energia sobre un rango de frecuencias, la primera de las contracciones muestran mayor contenido en frecuencuas altas de 80 - 120 HZ mienstras que las utlimas contracciones desplazan su pico hacia frecuencias mas bajas de 40 - 60 Hz este desplazamiento represneta un areduccion en la freciencia media del espectro que se asocia con la fatiga musculat esto ocurre porque las fibras musculares rapidas que son las de mayores frecuencias se agotan antes y la actividad electrica pada a depender mas de las fibras lentas.

El cálculo del pico espectral permitió cuantificar los cambios en la frecuencia dominante de cada contracción, el análisis mostró una disminución progresiva del pico espectral, se puede interpretar como evidencia de fatiga neuromuscular.

# Diagramas de flujo 
## Parte A 


## Parte B

## Parte C


# Bibliografía

De Luca, C. J. (2002). Surface electromyography: Detection and recording. DelSys Incorporated. Recuperado de https://www.delsys.com/

Merletti, R., & Parker, P. A. (2004). Electromyography: Physiology, engineering, and non-invasive applications. IEEE Press.

Konrad, P. (2005). The ABC of EMG: A practical introduction to kinesiological electromyography. Noraxon Inc.

Clancy, E. A., & Hogan, N. (1999). Relationship between electromyogram and muscle torque: Model formulation and experimental evaluation. IEEE Transactions on Biomedical Engineering, 46(6), 703–711.

González, R., & Jiménez, J. (2017). Procesamiento digital de señales biomédicas. Editorial Universidad Politécnica de Madrid.

De la Torre, A., & Moreno, J. C. (2018). Análisis de señales electromiográficas para la detección de fatiga muscular. Revista Iberoamericana de Ingeniería Biomédica, 9(1), 15–25.

Winter, D. A. (2009). Biomechanics and motor control of human movement (4th ed.). John Wiley & Sons.
