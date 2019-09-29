<h2>
Predecir Consumos (Series de Tiempo) con Machine Learning (ARIMA) en R</h2>
<div>
<div>
<h3>
Planteamiento del problema</h3>
A partir de los registros de consumo de un canal de datos recolectados durante 60 días, se busca predecir el consumo de los próximos 30 días.<br />
Los registros se pueden descargar en el siguiente enlace (<a href="https://drive.google.com/file/d/1e8XsB-3tcJUgiq_Upp7VQSRo2stjquO3/view?usp=sharing" target="_blank">canal.csv</a>) y fueron obtenidos de un objeto RRD (Round Robin Database) con las siguientes características:&nbsp;unidad bit/s, escala 8, intervalo 24:00:00.<br />
<h3>
Teoría - Series de Tiempo</h3>
<h4>
Quiz Series de Tiempo</h4>
<div>
Este quiz pretende evaluar su nivel conocimiento sobre las Series de Tiempo antes de iniciar la unidad de teoría.</div>
<div>
<iframe frameborder="0" height="300" marginheight="0" marginwidth="0" src="https://docs.google.com/forms/d/e/1FAIpQLSfSKdYeBvFrgsGHEQmfUBV533qmKL7nKFljPaPREbC8WaJbLA/viewform?embedded=true" width="100%">Cargando…</iframe></div>
<div>
<br /></div>
<div class="separator" style="clear: both; text-align: center;">
<iframe allowfullscreen="" class="YOUTUBE-iframe-video" data-thumbnail-src="https://i.ytimg.com/vi/8DbRntj0urA/0.jpg" frameborder="0" height="266" src="https://www.youtube.com/embed/8DbRntj0urA?feature=player_embedded" width="320"></iframe></div>
<div>
<br /></div>
<h4>
Definición</h4>
"Una serie de tiempo es una secuencia de observaciones, medidas en determinados momentos del tiempo, ordenados cronológicamente y espaciados entre sí de manera uniforme, así los datos usualmente son dependientes entre sí."(Ver&nbsp;<a href="https://drive.google.com/file/d/1MMt9eN82QRzN1X3boRvMhWu0MRdqkDev/view?usp=sharing" target="_blank">Introducción a Series de Tiempo</a>)<br />
<h4>
Componentes de una Serie Temporal</h4>
<div class="separator" style="clear: both; text-align: center;">
</div>
<div class="separator" style="clear: both; text-align: center;">
</div>
<div class="separator" style="clear: both; text-align: center;">
</div>
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;"><a href="https://4.bp.blogspot.com/-shL-PLJEAl4/XMrvxHSA1BI/AAAAAAAAMwE/E1U8H6XNoLQ_zpDjQ0q5Mq_2auixH113wCLcBGAs/s1600/decomposition.png" imageanchor="1" style="margin-left: auto; margin-right: auto;"><img border="0" data-original-height="568" data-original-width="760" src="https://4.bp.blogspot.com/-shL-PLJEAl4/XMrvxHSA1BI/AAAAAAAAMwE/E1U8H6XNoLQ_zpDjQ0q5Mq_2auixH113wCLcBGAs/s1600/decomposition.png" /></a></td></tr>
<tr><td class="tr-caption" style="text-align: center;">Gráfica: Componentes de la Serie de Tiempo del Consumo del Canal de Datos</td></tr>
</tbody></table>
"El análisis clásico de las series temporales se basa en la suposición de que los valores que toma la variable de observación es la consecuencia de tres componentes, cuya actuación conjunta da como resultado los valores medidos, estos componentes son:<br />
<iframe allowfullscreen="allowfullscreen" frameborder="0" height="195" src="https://h5p.org/h5p/embed/589252" width="100%"></iframe><script charset="UTF-8" src="https://h5p.org/sites/all/modules/h5p/library/js/h5p-resizer.js"></script>

<br />
<h4>
Clasificación de las Series Temporales</h4>
<div>
<b>Estacionarias:</b>&nbsp;"Una serie es estacionaria cuando es estable a lo largo del tiempo, cumpliendo tres criterios:<br />
<iframe allowfullscreen="allowfullscreen" frameborder="0" height="400" src="https://h5p.org/h5p/embed/589270" width="100%"></iframe><br />
<b>No Estacionarias:</b>&nbsp;Son series en las cuales la tendencia y/o variabilidad cambian en el tiempo. Los cambios en la media determinan una tendencia a crecer o decrecer a largo plazo, por lo que la serie no oscila alrededor de un valor constante.</div>
<h3>
Teoría - Algoritmos de Machine Learning</h3>
"La gran mayoría de algoritmos de Machine Learning, se engloban en tres grupos principales:<br />
<iframe allowfullscreen="allowfullscreen" frameborder="0" height="195" src="https://h5p.org/h5p/embed/589282" width="100%"></iframe><script charset="UTF-8" src="https://h5p.org/sites/all/modules/h5p/library/js/h5p-resizer.js"></script>

<br />
<h3>
Predecir Series de Tiempo con ARIMA</h3>
<div>
En el problema planteado se conocen los registros de una serie de tiempo y se busca predecir sus registros futuros, razón por la cual se utilizará un algoritmo de aprendizaje supervisado de Machine Learning denominado ARIMA (autoregressive integrated moving average (autorregresivo integrado de promedio móvil)).</div>
