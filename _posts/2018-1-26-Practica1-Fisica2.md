---
layout: post
title: Práctica 1 - Física 2 Calores específicos
---

Esta práctica consistirá en determinar los calores específicos de diferentes sustancias. El material proporcionado es el siguiente:
* Agitador magnético con un vaso de precipitado
* Fuente de alimentación con un barra metálica para aplicar calor
* Termómetro
* Diferentes sustancias en unos recipientes metálicos
* Cronómetro

<img src="../images/fuente_de_alimentación.jpg" width="49%">
<img src="../images/removedor.jpg" width="49%">
<img src="../images/sustancias.jpg" width="64%">
<img src="../images/termometro.jpg" width="35%">

Los objetivos de la prática para las sustancias de Cobre, Hierro, Aluminio y Agua:
* Determinar el error cometido al medir la temperatura, la energía aportada y las masas.
* Gráfica de calor y temperatura
* Razonar el comportamiento de la curva
* Determinar la pendiente mediante un ajuste por mínimos cuadrados, y determinar su error cuadrático médio.
* Determinar el error de los calores absolutos con sus errores absolutos. Comparar estas medidas con los valores reales.

### Determinar el calor específico

Nuestra situación es la siguiente, tenemos una fuente de alimentación que nos proporciona un calor, y medimos como varía la temperatura de diferentes sustancias. Pero, ¿Cómo determinamos el calor específico?

La **capacidad calorífica** \\(C_e\\) se define como

$$

C_e = \frac{Q}{m \cdot \Delta T}

$$

Siendo:
* **Q**: Es la tranferencia de energía en forma calorífica entre el sistema y su entorno y otro sistema, es decir, el calor que le proporcionamos al material con nuestra fuente de alimentación. **Se mide en calorias** (cal). \\(1 cal \Rightarrow 4.18 J\\)
* **m** la masa del sistema. Se mide en gramos (g).
* \\( \Delta T \\): El incremento de temperatura del sistema. La temperatura se mide en Kelvins (K).
* \\(C_e\\): El calor específico. Se mide en \\([C_e] = \frac{[C]}{[m]} = \frac{[Cal]}{[g \cdot K]}\\)

Por otro lado, en la fuente de alimentación, se define **potencia instantanea** cómo:

$$

P = V \cdot I

$$

Siendo:
* **P** es la potencia instantanea, medida en vatios. \\( [W] = \frac{[E]}{[t]}\\)
* **V** es el voltaje, medida en voltios (V).
* **I** es el amperaje, medida en amperios (A).

Igualmente se define la **potencia calorífica**, que es la cantidad de calor que libera por unidad de tiempo, como:

$$

P = \frac{E}{t}

$$

Siendo:
* **P** es la potencia instántanea, medida en vatios. \\( [W] = \frac{[E]}{[t]}\\)
* **E** es la energía proporcionada en Julios (J).
* **t** es el tiempo, en segundos (s).

Juntando lo anterior, podemos igualar las potencias instantaneas para conseguir la potencia calorífica:

$$

E = P \cdot t = V \cdot I \cdot t

$$

El calor es una forma de trabajo, es decir que podemos igualar la potencia calorífica (E) con el Calor proporcionado (Q). **Tenemos que tener cuidado porque la potencia calorífica(E) está expresada en Julios y el Calor (Q) está expresado en calorias (Cal)**. Dicho esto, igualamos las expresiones de potencia calorífica y <a name="defCalor" style="text-decoration: none;">calor</a>:

$$

E \Rightarrow Julios
\qquad
Q \Rightarrow Cal

$$

$$

Q = E \cdot \frac{1}{4.18} = V \cdot I \cdot t \cdot \frac{1}{4.18}

\\

m \cdot C_e \cdot \Delta T = V \cdot I \cdot t \cdot \frac{1}{4.18}

$$

Y finalemente llegamos a que:

$$

C_e = \frac{V \cdot I \cdot t}{4.18} \cdot \frac{1}{m \cdot \Delta T} = \frac{V \cdot I \cdot t}{4.18} \cdot \frac{1}{m \cdot (T_{final} - T_{inicial})}
$$

Para calcular el calor específico necesitaremos el voltaje, la intensidad, el tiempo, la masa y la variación de temperatura, es decir, todas las variables son conocidas.
### Cálculo de errores

Para calcular el error que se comete en las medidas hay que ver el error absoluto de los diferentes aparatos:
* El termómetro da una lectura de 3 dígitos, expresado con 1 decimal, por lo que su error absoluto será de \\(\pm 0.1 ºC\\)
* La fuente de alimentación tiene dos medidas, el voltaje y el amperaje. **En el volteje** la lectura es de 3 dígitos, expresado con 1 decimal, por lo que su error absoluto será de \\(\pm 0.1 V\\). **En el amperaje** la lectura es de 3 dígitos, expresado con 2 decimales, por lo que su error absoluto será de \\(\pm 0.01 A\\).
* El cronometro tiene 2 dígitos para minutos, 2 para segundos y 2 para centisegundos. Por lo que el error absoluto será de \\(\pm 0.01 s\\).
* El vaso de precipitado tiene una medida cada 50 mL, por lo que el error absoluto será de \\(\pm 50 mL\\). Esto en el caso del agua.
* En el caso de las otras sustacias, sus masas tienen también un error que está expresada en el mismo: El **aluminio** \\(\pm 0.1 g\\), el **cobre** \\(\pm 0.1 g\\) y el **hierro** \\(\pm 0.1 g\\).

El error absoluto de una función que dependen de varias magnitudes independientes \\(x_1, x_2, x_3, ...\\) de una función: \\(y = f(x_1, x_2, x_3, ...)\\),  se calcularía así:

$$

\Delta y = \Bigg \lvert \frac{\delta y}{\delta x_1} \Bigg \lvert \Delta x_1  + \Bigg \lvert \frac{\delta y}{\delta x_2} \Bigg \lvert \Delta x_2 + ...

$$

Para calcular el error absoluto del calor específico se haría así:

$$

C_e = \frac{V \cdot I \cdot t}{4.18} \cdot \frac{1}{m \cdot (T_{final} - T_{inicial})}

\\

\Delta C_e = \Bigg \lvert \frac{\delta C_e}{\delta V} \Bigg \lvert \Delta V +
\Bigg \lvert \frac{\delta C_e}{\delta I} \Bigg \lvert \Delta I +
\Bigg \lvert \frac{\delta C_e}{\delta t} \Bigg \lvert \Delta t +
\Bigg \lvert \frac{\delta C_e}{\delta m} \Bigg \lvert \Delta m +
\Bigg \lvert \frac{\delta C_e}{\delta T} \Bigg \lvert \Delta T

\\
= \Bigg \lvert \frac{I \cdot t}{4.18 \cdot m \cdot (T_{final} - T_{inicial})}\Bigg \lvert \Delta V +
\Bigg \lvert \frac{V \cdot t}{4.18 \cdot m \cdot (T_{final} - T_{inicial})}\Bigg \lvert \Delta I
\\+
\Bigg \lvert \frac{V \cdot I}{4.18 \cdot m \cdot (T_{final} - T_{inicial})}\Bigg \lvert \Delta t +
\Bigg \lvert \frac{V \cdot I \cdot t}{4.18 \cdot m^2 \cdot (T_{final} - T_{inicial})}\Bigg \lvert \Delta m + 0
$$

Siendo:
* \\(\Delta V\\) el error del voltaje de la fuente de alimentación, \\(\Delta V = \pm 0.1 V\\).
* \\(\Delta I\\) el error del amperaje de la fuente de alimentación, \\(\Delta I = \pm 0.01 A\\).
* \\(\Delta t\\) el error del cronómetro, \\(\Delta t = \pm 0.01 s\\).
* \\(\Delta m\\) el error de la masa, varía dependiendo de la sustancia que estemos trabajando.
* V es el voltaje, nosotros usaremos un **voltaje de 11 V**.
* I es el amperaje, nosotros usaremos un **amperaje de 2.9A**.
* t es el tiempo transcurrido en el experimento, medido en segundos.
* m es la masa del objeto que estemos estudiando, medido en gramos.
* \\(T_{final}\\) ó \\(T_{inicial} \\) es la temperatura inicial y final, medido en Kelvins.

### Agua
#### Planteamiento
Primero vamos a empezar con el agua. Los pasos seguidos han sido:
1. Primero cogemos el vaso de precipitado y lo llenamos de **agua del grifo**. Lo llenamos con unos **400 ml**.
2. Introducimos la barra metálica de la fuente de alimentación y el termómetro.
3. Encendemos el agitador para asegurarnos de que la temperatura será constante en todo el recipiente.
2. Encendemos la **fuente de alimentación** y la ponemos a **11 Voltios a 2.90 Amperios**.
3. Tomamos los valores de temperatura cada **30 segundos**.

En las primeras iteraciones del experimento pudimos notar que el agua varía de temperatura muy lenta, del órden de 0.3ºC/0.5ºC. Por lo que tomar valores cada 30 segundos sería más que suficiente. Además, tendremos que tener el experimento el tiempo suficiente cómo para que la variación de temperatura sea grande, esta variación debería de ser de 20ºC a 50ºC para tener una gama amplia de datos.

La temperatura del agua del grifo inicialmente es de 23.3ºC, y el agua empieza a hervir a los 90ºC. Con lo que un buen volumen de datos sería llegar a los 40ºC/ 50ºC.

#### Realización

Al realizar la prueba, **cogimos datos durante 870 segundos desde una temperatura inicial de 23.3ºC hasta los 35.7ºC**. Los datos obtenidos se encuentran [aquí](../data/aguaexp.json). Su gráfica de temperatura frente a tiempo sería la siguiente:

<div id="agua_chart" style="width: 900px; height: 500px"></div>

La gráfica de Calor frente a temperatura, utilizando <a href="#defCalor">esta expresión</a>, sería la siguiente:

<div id="agua2_chart" style="width: 900px; height: 500px"></div>

Las curvas no son excesivamente rectas, empezando con un poco menos de inclinación y luego ya siendo más constantes. **La inclinación del inicio** se debe a que el calentador está todavía calentando el metal y eso hace que la inclinacón sea menor y no tan constante como en la demás parte de la recta. **Esto se solucionaría eliminando los primeros valores**, pues no determinan bien la variación de temperatura. Además nos encontramos con otro problema y es que  la curva no es excesivamente recta, cuando **debería de ser lineal**. El problema se debe a que el volumen de datos obtenidos es un poco escaso, con lo que **deberían de ser más datos**.


### Cobre
#### Planteamiento
#### Realización

<div id="cobre_chart" style="width: 900px; height: 500px"></div>

### Aluminio
#### Planteamiento
#### Realización

<div id="aluminio_chart" style="width: 900px; height: 500px"></div>

### Hierro
#### Planteamiento
#### Realizacion

<div id="hierro_chart" style="width: 900px; height: 500px"></div>

### Bibliografía
* https://es.wikipedia.org/wiki/Calor_espec%C3%ADfico

* https://developers.google.com/chart/interactive/docs/gallery/linechart#examples

* https://es.wikipedia.org/wiki/Potencia_(f%C3%ADsica)

<script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
<script type="text/javascript">
      google.charts.load('current', {'packages':['line']});
      google.charts.setOnLoadCallback(drawAgua);
      google.charts.setOnLoadCallback(drawAluminio);
      google.charts.setOnLoadCallback(drawCobre);
      google.charts.setOnLoadCallback(drawHierro);

      function drawAgua() {
        var request = new XMLHttpRequest();
        request.open("GET", "../data/aguaexp.json", true);
        request.send(null);
        request.onreadystatechange = function () {
          if (request.readyState == 4 && request.status == "200") {
              var my_JSON_object = JSON.parse(request.responseText);

              // Datos de la gráfica de temperatura frente a tiempo
              var data = new google.visualization.DataTable();
              data.addColumn('number', 'Tiempo (s)');
              data.addColumn('number', 'Temperatura (ºC)');

              my_JSON_object.datos.forEach(function(element){
                  data.addRow([element.tiempo, element.temperatura]);
              });

              //Datos de la gráfica de calor frente a temperatura

              var data2 = new google.visualization.DataTable();
              data2.addColumn('number', 'Calor (cal)');
              data2.addColumn('number', 'Temperatura (ºC)');

              my_JSON_object.datos.forEach(function(element){
                  data2.addRow([7.63 * element.tiempo, element.temperatura]);
              });

              var options = {
                title: 'Company Performance',
                curveType: 'function',
                legend: { position: 'bottom' }
              };

              var chart = new google.charts.Line(document.getElementById('agua_chart'));
              var chart2 = new google.charts.Line(document.getElementById('agua2_chart'));

              chart.draw(data, options);
              chart2.draw(data2, options);
          }
        };
      }

      function drawAluminio() {
        var request = new XMLHttpRequest();
        request.open("GET", "../data/aluminioexp.json", true);
        request.send(null);
        request.onreadystatechange = function () {
          if (request.readyState == 4 && request.status == "200") {
              var my_JSON_object = JSON.parse(request.responseText);

              var data = new google.visualization.DataTable();
              data.addColumn('number', 'Tiempo (s)');
              data.addColumn('number', 'Temperatura (ºC)');

              my_JSON_object.datos.forEach(function(element){
                  data.addRow([element.tiempo, element.temperatura]);
              });

              var options = {
                title: 'Company Performance',
                curveType: 'function',
                legend: { position: 'bottom' }
              };

              var chart = new google.charts.Line(document.getElementById('aluminio_chart'));

              chart.draw(data, options);
          }
        };
      }

      function drawCobre() {
        var request = new XMLHttpRequest();
        request.open("GET", "../data/cobreexp.json", true);
        request.send(null);
        request.onreadystatechange = function () {
          if (request.readyState == 4 && request.status == "200") {
              var my_JSON_object = JSON.parse(request.responseText);

              var data = new google.visualization.DataTable();
              data.addColumn('number', 'Tiempo (s)');
              data.addColumn('number', 'Temperatura (ºC)');

              my_JSON_object.datos.forEach(function(element){
                  data.addRow([element.tiempo, element.temperatura]);
              });

              var options = {
                title: 'Company Performance',
                curveType: 'function',
                legend: { position: 'bottom' }
              };

              var chart = new google.charts.Line(document.getElementById('cobre_chart'));

              chart.draw(data, options);
          }
        };
      }

      function drawHierro() {
        var request = new XMLHttpRequest();
        request.open("GET", "../data/hierroexp.json", true);
        request.send(null);
        request.onreadystatechange = function () {
          if (request.readyState == 4 && request.status == "200") {
              var my_JSON_object = JSON.parse(request.responseText);

              var data = new google.visualization.DataTable();
              data.addColumn('number', 'Tiempo (s)');
              data.addColumn('number', 'Temperatura (ºC)');

              my_JSON_object.datos.forEach(function(element){
                  data.addRow([element.tiempo, element.temperatura]);
              });

              var options = {
                title: 'Company Performance',
                curveType: 'function',
                legend: { position: 'bottom' }
              };

              var chart = new google.charts.Line(document.getElementById('hierro_chart'));

              chart.draw(data, options);
          }
        };
      }

</script>
