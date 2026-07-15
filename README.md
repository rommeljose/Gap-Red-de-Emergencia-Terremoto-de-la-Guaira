# Gap azimutal — Red Sísmica de Emergencia · Terremoto de La Guaira 2026

Consola interactiva para medir la **cobertura azimutal** (el *gap*) de la Red Sísmica de Emergencia
sobre las réplicas del **Terremoto de La Guaira** (doblete **M 7,2 + M 7,5**, 24-jun-2026, falla de
San Sebastián).

🔗 **En vivo:** https://rommeljose.github.io/Gap-Red-de-Emergencia-Terremoto-de-la-Guaira/

## Qué muestra

El *gap azimutal* es el mayor hueco angular, visto desde un sismo, en el que **no hay ninguna
estación**. Por encima de **180°** el evento cae *fuera* de la red y su profundidad deja de estar
restringida por los datos. La consola permite:

- **Mover GT01** entre **Gran Roque** (Los Roques, el punto de diseño) y **Paracotos** (donde se
  instaló el 14-jul-2026) y ver el efecto sobre la cobertura.
- **Encender / apagar cualquier estación** con un clic sobre el mapa (simular una caída de campo) y
  pulsar **Re-analizar** para recalcular.
- **Filtrar por magnitud** con el deslizador (por defecto **M ≥ 4**).
- **Acotar el ámbito** al eje litoral **Morón–Caraballeda** o a todo el catálogo.
- Elegir la réplica de análisis en el desplegable o hacer clic sobre cualquier evento del mapa.

El panel derecho compara **las dos posiciones de GT01** sobre todas las réplicas del filtro actual.

## Resultado principal

Sobre las **1 208 réplicas** del catálogo, mover GT01 de Gran Roque a Paracotos triplica las
réplicas que quedan *fuera de la red* (de 24 % a 67 %): Gran Roque era el **único anclaje al norte de
la ruptura**, que es submarina. Ningún punto en tierra puede cerrar ese flanco — es el argumento
cuantitativo para evaluar sismómetros de fondo oceánico (OBS).

## Datos

- **Estaciones:** 20 estaciones de banda ancha de la Red GFZ (Trillium Compact + DATA-CUBE³),
  14 instaladas al 14-jul-2026.
- **Réplicas:** 1 208 eventos del catálogo **FUNVISIS** vía servicio FDSN
  ([catalogosismicovenezuela.sigeos.org](https://catalogosismicovenezuela.sigeos.org)), descargados
  el 14-jul-2026. Los datos van **embebidos** en `index.html`: la página es autónoma, sin peticiones
  externas.

## Cómo funciona el cálculo

Para cada evento se calcula el azimut geodésico (*initial bearing*) hacia cada estación activa; el
gap es el mayor salto entre azimuts consecutivos ordenados. Todo se computa en el navegador.

## Créditos

- Análisis y diseño: **Lcdo. Físico Rommel Contreras** (AGHES)

---
Proyecto relacionado (mapa operativo de la red): https://rommeljose.github.io/Red_Emergencia_Vzla/
