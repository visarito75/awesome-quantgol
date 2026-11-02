# awesome-quantgol

Lista curada de recursos para pronósticos de goles en fútbol: fuentes de datos, modelos estadísticos, librerías y
herramientas de evaluación. Es el material de referencia del proyecto QuantGol.

## Índice

- [Fuentes de datos](#fuentes-de-datos)
- [Datos históricos para descargar](#datos-históricos-para-descargar)
- [Modelos estadísticos](#modelos-estadísticos)
- [Librerías Python](#librerías-python)
- [Evaluación y calibración](#evaluación-y-calibración)
- [Notas](#notas)

## Fuentes de datos

- [API-Football](https://www.api-football.com/) - calendario, resultados y estadísticas por partido (tiros, córners,
  tarjetas, posesión) de cientos de ligas. Plan gratuito: 100 peticiones al día.
- [OpenFootAPI](https://openfootapi.com/) - marcadores al momento y resultados. Plan gratuito: 5.000 consultas al mes.
- [Highlightly](https://highlightly.net/) - estadísticas por partido (incluidas ocasiones claras), eventos con
  goleadores y alineaciones, también de ligas sudamericanas. Plan gratuito: 100 consultas al día.
- [football-data.org](https://www.football-data.org/) - resultados, tablas y goleadores. El plan gratuito cubre unas
  pocas competiciones (las grandes ligas europeas, Brasil y la Champions).
- [Football-Data.co.uk](https://www.football-data.co.uk/) - históricos en CSV de ligas europeas desde los años 90, con
  tiros, córners, tarjetas y árbitro en muchas divisiones. Gratuito.
- [ClubElo](http://clubelo.com/) - fuerza Elo diaria de los clubes europeos, con historial. Gratuito, sin clave.
- [Open-Meteo](https://open-meteo.com/) - clima histórico y previsión por coordenadas (lluvia, viento, temperatura).
  Gratuito para uso no comercial, sin clave.

## Datos históricos para descargar

- [transfermarkt-datasets](https://github.com/dcaribou/transfermarkt-datasets) - partidos, alineaciones, goles por
  jugador, entrenadores, traspasos y valores de mercado de unas 65 competiciones (sobre todo europeas). También en
  Kaggle como [player-scores](https://www.kaggle.com/datasets/davidcariboo/player-scores). Actualización pausada en
  julio de 2026.
- [openfootball/south-america](https://github.com/openfootball/south-america) - resultados y marcador al descanso de
  Argentina, Brasil, Colombia, Libertadores y Sudamericana. Solo resultados, sin estadísticas; algunas temporadas
  están incompletas.

## Modelos estadísticos

- **Modelo de Poisson para goles:** cada equipo se modela como una variable de Poisson con una tasa de goles esperada.
  Es la base de la mayoría de los modelos de goles.
- **Dixon y Coles (1997):** extensión del modelo de Poisson que corrige los marcadores bajos (0-0, 1-0, 0-1, 1-1) y da
  más peso a los partidos recientes. Artículo: *Modelling Association Football Scores and Inefficiencies in the
  Football Betting Market*, Journal of the Royal Statistical Society, Series C (Applied Statistics), 46(2), 265–280.
- **Regresión de Poisson con variables:** la tasa de goles se explica con variables del partido (forma, tiros, descanso,
  árbitro, altura, valor de la plantilla…). Cada variable nueva se acepta solo si mejora la predicción fuera de muestra.
- **Matriz de marcadores:** probabilidad de cada marcador posible, de la que salen Más/Menos de cada línea, ambos marcan
  y los goles de cada equipo.
- **Binomial negativa:** para córners y tarjetas, que varían más de lo que supone Poisson.

## Librerías Python

- [NumPy](https://numpy.org/) - cálculo numérico y matrices.
- [pandas](https://pandas.pydata.org/) - manejo de datos históricos de partidos.
- [SciPy](https://scipy.org/) - distribuciones de probabilidad (Poisson, binomial negativa).
- [scikit-learn](https://scikit-learn.org/) - regresión de Poisson (`PoissonRegressor`) y validación.
- [LightGBM](https://lightgbm.readthedocs.io/) - modelos de gradient boosting con pérdida de Poisson.
- [statsmodels](https://www.statsmodels.org/) - modelos estadísticos clásicos (GLM de Poisson con resumen de
  coeficientes).
- [penaltyblog](https://github.com/martineastwood/penaltyblog) - modelos de goles listos (Poisson, Dixon-Coles y otros)
  y herramientas para datos de fútbol.

## Evaluación y calibración

- **Aciertos de cada 100:** de cada 100 partidos, cuántos acertó (por ejemplo, el lado de Más/Menos 2,5). Siempre con
  el pronóstico hecho antes del partido.
- **Brier score:** error de las probabilidades frente al resultado real. Cuanto menor, mejor.
- **Log loss y devianza de Poisson:** castigan mucho las predicciones muy seguras que fallan. La devianza mide el
  error de los goles esperados de cada equipo.
- **Curva de calibración:** compara la probabilidad predicha con lo que pasó de verdad (de los pronósticos al 75 %,
  ¿se cumplieron unos 75 de cada 100?).
- **Validación walk-forward:** se entrena con el pasado y se prueba mes a mes con partidos que el modelo no vio.

## Notas

- Los planes gratuitos de estas APIs cambian con frecuencia. Revisa los límites antes de usarlas.
- Esta lista no incluye casas de apuestas ni comparaciones de cuotas. Algunas fuentes (Football-Data.co.uk, Highlightly)
  también publican cuotas; aquí solo se recomiendan para datos de partidos y estadísticas.
- Revisa la licencia de cada conjunto de datos antes de redistribuirlo.
- Si quieres añadir un recurso, abre un *issue* o un *pull request* con el nombre, el enlace y una descripción corta.
