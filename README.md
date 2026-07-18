# Gap azimutal — Red Sísmica de Emergencia · Terremoto de La Guaira 2026

Consola web interactiva para medir la **cobertura azimutal** (el *gap*) de la Red Sísmica de
Emergencia sobre las réplicas del **Terremoto de La Guaira** (doblete **M 7,2 + M 7,5**,
24-jun-2026, sistema de fallas Boconó–San Sebastián).

🔗 **En vivo:** https://rommeljose.github.io/Gap-Red-de-Emergencia-Terremoto-de-la-Guaira/

![Estado](https://img.shields.io/badge/red-18%2F20%20instaladas-0f8f84) ![Datos](https://img.shields.io/badge/réplicas-1208%20FUNVISIS-33474f) ![Autónoma](https://img.shields.io/badge/sin%20dependencias-página%20única-c37f14)

---

## Qué es el *gap* azimutal y por qué importa

Para **localizar** un sismo se cruzan las lecturas de varias estaciones. Si todas quedan hacia el
mismo lado del evento, los cruces se vuelven rasantes y la solución se estira: la epicentral se corre
y, sobre todo, **la profundidad queda mal resuelta**.

El *gap azimutal* es el **mayor hueco angular** entre dos estaciones consecutivas, visto desde el
evento. Se lee así:

| Gap | Lectura |
|---|---|
| **< 120°** | Bien rodeado. Meta de una red de réplicas. |
| **120–180°** | Aceptable; la profundidad empieza a degradarse. |
| **> 180°** | El evento cae **fuera de la red**: todas las estaciones en un mismo semiplano. |

El umbral de **180°** no es una convención más: es el punto en que el evento deja de estar *dentro*
del polígono de estaciones.

## Qué permite la consola

- **Ubicar GT01** en **Gran Roque** (Los Roques, punto de reserva al norte) o en **Puerto Maya**
  (su nueva asignación, sobre la costa central) y ver el efecto sobre la cobertura.
- **Encender / apagar cualquier estación** con un clic sobre el mapa —para simular una caída de
  campo o un escenario hipotético— y pulsar **Re-analizar**.
- **Filtrar por magnitud** con el deslizador (las réplicas se dibujan con **radio ∝ magnitud**).
- **Acotar el ámbito** al eje litoral **Morón–Caraballeda** o a todo el catálogo.
- **Analizar cualquier réplica**: elígela en el desplegable o haz clic sobre ella en el mapa; la
  **cuña roja** marca su gap y hacia dónde se abre.
- Alternar entre la **red completa (20)** y **solo las instaladas**. Las estaciones **por instalar**
  se dibujan con borde punteado y rótulo.

El panel derecho compara **las dos posiciones de GT01** (Gran Roque vs. Puerto Maya) sobre todas las
réplicas del filtro actual.

El mapa incluye la **silueta de la costa** venezolana y las **islas oceánicas** (Los Roques, Las
Aves, La Orchila), para que se vea de un golpe lo que sostiene el análisis: las estaciones están en
tierra y la mayoría de las réplicas caen **mar adentro**.

## Resultado principal

Con las **18 estaciones instaladas** (al 17-jul-2026) y sobre las 1 208 réplicas del catálogo:

| Con las 18 instaladas | GT01 en Gran Roque | GT01 en Puerto Maya |
|---|---|---|
| Gap mediano | 102,6° | 162,9° |
| Réplicas fuera de la red (> 180°) | 88 (7 %) | 147 (12 %) |
| Réplicas **bien rodeadas** (< 120°) | **992 (82 %)** | **193 (16 %)** |
| Dirección media del hueco | Sursuroeste | Norte |

Al completarse el flanco occidental (GT11, GT17, GT18, GT19, GT20), la reubicación de
GT01 pesa poco en el conteo de «fuera de la red», pero **mucho en la calidad**: las réplicas bien
rodeadas caen del **82 % al 16 %**, y el hueco residual apunta al **norte**. Gran Roque es el único punto de tierra
firme al norte de la ruptura; ninguna estación en tierra puede cerrar ese flanco marino — es el
argumento cuantitativo para evaluar **sismómetros de fondo oceánico (OBS)**.

> A este análisis geométrico se suma una observación del **Dr. Antoine Mocquet** (U. Nantes), incluida
> en la página: con casi todas las estaciones al sur de la falla, las localizaciones pueden **sesgarse
> hacia el sur** (error tierra adentro); una estación al norte permite **chequear ese sesgo**.

## Datos y método

- **Estaciones:** 20 de banda ancha de la Red GFZ (Nanometrics Trillium Compact + registrador DiGOS
  DATA-CUBE³), aportadas por el **Helmholtz-Zentrum Potsdam (GFZ)**. 18 instaladas al 17-jul-2026.
- **Réplicas:** 1 208 eventos del catálogo **FUNVISIS** vía servicio FDSN
  ([catalogosismicovenezuela.sigeos.org](https://catalogosismicovenezuela.sigeos.org)), instantánea
  del 14-jul-2026.
- **Costa e islas:** contorno nacional de Venezuela (simplificado) + Natural Earth (islas menores).
- **Cálculo:** para cada evento se computa el azimut geodésico (*initial bearing*) hacia cada
  estación activa; el gap es el mayor salto entre azimuts consecutivos ordenados. Todo se ejecuta
  **en el navegador**.

## Detalles técnicos

- **Página única y autónoma:** todo (datos, geometría de costa, lógica) va **embebido** en
  `index.html`. No hace ninguna petición de red — funciona sin conexión y sin backend.
- **Instantánea, no servicio en vivo:** los datos están congelados en la fecha de exportación; se
  actualizan regenerando el bloque embebido y volviendo a desplegar.
- **Tema claro/oscuro** automático (sigue el del sistema, con conmutador).
- **Sin librerías externas:** render en Canvas 2D, vanilla JS.

### Cómo se regeneran los datos

Los datos provienen de la fuente de verdad del proyecto operativo
([`Red_Emergencia_Vzla`](https://github.com/rommeljose/Red_Emergencia_Vzla)):
`data/estaciones.geojson` (posición y estado de cada estación) y `data/replicas.geojson` (catálogo
FUNVISIS). Cuando cambian —una instalación nueva, una reubicación, o un catálogo más reciente— se
re-exporta el `const DATA` embebido y se hace `git push` (GitHub Pages redepliega en ~1–8 min).

## Despliegue

`index.html` en la raíz; GitHub Pages publica desde `main`. Cualquier `git push` actualiza el sitio.

## Créditos

Análisis y diseño: **Lcdo. Físico Rommel Contreras** (AGHES).
Incluye una observación del Dr. Antoine Mocquet (U. Nantes). Datos: FUNVISIS · Natural Earth · GEM.

---
Proyecto operativo relacionado (mapa e instalación de la red):
https://rommeljose.github.io/Red_Emergencia_Vzla/
