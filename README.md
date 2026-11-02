# awesome-quantgol

Lista curada de recursos para pronósticos de goles en fútbol: fuentes de datos, modelos estadísticos, librerías y herramientas de evaluación. Es el material de referencia del proyecto QuantGol.

## Índice

- [Fuentes de datos](#fuentes-de-datos)
- [Modelos estadísticos](#modelos-estadísticos)
- [Librerías Python](#librerías-python)
- [Evaluación y calibración](#evaluación-y-calibración)
- [Notas](#notas)

## Fuentes de datos

- [API-Football](https://www.api-football.com/) - resultados, estadísticas y calendarios de muchas ligas. Plan gratuito con límite de peticiones.
- [Football-Data.co.uk](https://www.football-data.co.uk/) - históricos de resultados de ligas europeas en CSV. Gratuito.
- [football-data.org](https://www.football-data.org/) - API de resultados y tablas. Plan gratuito limitado a un número reducido de ligas.
- [OpenFootAPI](https://openfootapi.com/) - API de datos de fútbol.
- [Highlightly](https://highlightly.net/) - API de partidos y estadísticas. Plan gratuito con límites.

## Modelos estadísticos

- Modelo de Poisson para goles: cada equipo se modela como una variable de Poisson con una tasa de goles esperada. Base de la mayoría de los modelos de goles.
- Dixon & Coles (1997): extensión del modelo de Poisson que corrige la subestimación de marcadores bajos (0-0, 1-0, 0-1, 1-1). Artículo: *Modelling Association Football Scores and Inefficiencies in the Football Betting Market*, Journal of the Royal Statistical Society, Series C.
- Cuadrícula de goles: matriz de probabilidades de cada marcador posible, de la que se derivan Over/Under y ambos marcan (BTTS).

## Librerías Python

- [NumPy](https://numpy.org/) - cálculo numérico y matrices.
- [pandas](https://pandas.pydata.org/) - manejo de datos históricos de partidos.
- [SciPy](https://scipy.org/) - funciones de probabilidad, incluida Poisson.
- [statsmodels](https://www.statsmodels.org/) - modelos estadísticos y regresiones.

## Evaluación y calibración

- **Brier score:** mide el error de las probabilidades predichas frente al resultado real. Cuanto menor, mejor.
- **Log loss:** penaliza fuertemente las predicciones muy seguras que fallan.
- **Curva de calibración:** compara la probabilidad predicha con la frecuencia real de aciertos.
- **Historial de aciertos:** conteo de jugadas acertadas sobre el total, reportado en cifras absolutas.

## Notas

- Los planes gratuitos de estas APIs cambian con frecuencia. Revisa los límites antes de usarlas.
- Esta lista no incluye casas de apuestas ni comparaciones de cuotas.
- Si quieres añadir un recurso, abre un *issue* o un *pull request* con el nombre, el enlace y una descripción corta.
