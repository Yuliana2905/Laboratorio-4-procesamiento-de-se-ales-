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
