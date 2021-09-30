# Simulador de modos propios v1.0
![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/img/loading_screen.bmp)



Esta aplicación permite evaluar el comportamiento modal de recintos modelados en 3D. Fue desarrollada mediante el Application Builder del programa COMSOL Multiphysics&reg; v5.6

------------


## Descarga e instalación
Existen dos alternativas para utilizar la aplicación. La primera de ellas es mediante el archivo *Simulador_modos_propios.mph*, el cual se ejecuta utilizando el software COMSOL Multiphysics® (versión 5.6 o superior). Este archivo contiene el diseño y la implementación de los métodos necesarios para ejecutar la aplicación. Se puede descargar desde el siguiente repositorio en GitHub: https://github.com/Ylio7/simulador-de-modos-propios. Las próximas versiones y actualizaciones serán publicadas en el mismo repositorio.

Por otra parte, si no se tiene instalado COMSOL Multiphysics®, se podrá utilizar la versión ejecutable para Windows que se descarga desde el siguiente enlace: https://bit.ly/3ifNOKw. Incluye el runtime environment de COMSOL Multiphysics® necesario para correr la aplicación. La instalación del runtime environment se efectúa la primera vez que se ejecute la aplicación. Se deberán aceptar los términos y condiciones y elegir la carpeta de instalación (se recomienda dejar la que viene por defecto).



## Herramientas
La aplicación inicia con el modelo geométrico por defecto junto con la tabla de sus frecuencias propias.
![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/001.png)
### Importar modelo
Permite importar modelos geométricos en formato .stl, .dwg, .dxf y otros de CAD 3D. Se recomienda que los modelos realizados en SketchUp sean exportados a formato .stl.
### SketchUp Online
Abre el sitio web https://app.sketchup.com/app que permite realizar modelos de salas de forma gratuita con las herramientas del software SketchUp, para ser luego importadas a la aplicación.
### Graficar geometría
Traza el modelo geométrico en el área de gráfico.
### Malla
Traza la malla de cálculo en el área de gráfico.
### Resoluciones
Permite aumentar la resolución de la malla y de los ángulos entre caras (este último exclusivamente para modelos .stl).
### Contornos
Permite seleccionar y ocultar contornos (caras). Útil para observar las zonas de presión e isocurvas dentro del recinto.
### Calcular
Efectúa el cálculo de las frecuencias propias en base a dos parámetros de entrada:
- Cantidad mínima de frecuencias a calcular: el valor por defecto se calcula para cubrir el entorno de la frecuencia de Schroeder.
- Calcular a partir de los: indica frecuencia mínima, aunque la misma podría ser aún menor según las dimensiones del recinto. Generalmente se recomienda dejar este valor en 20 Hz.

Una vez calculadas las frecuencias propias se muestran en la tabla a la derecha del gráfico.
### Graficar modos
Traza los mapas de presión e isocurvas y habilita los controles interactivos debajo del gráfico. Estos permiten seleccionar la frecuencia propia a mostrar, manejar con un control deslizable el comportamiento de las isocurvas y seleccionar la cantidad de niveles para subdividirlas.
### Exportar tabla
Exporta la tabla de frecuencias propias calculadas a un archivo .txt.
### Generar reporte
Confecciona un informe automático según los siguientes datos de entrada:
- Título
- Autor
- Empresa
- Fecha
- Versión
- Resumen

### Planilla de análisis
Abre la planilla Modos_COMSOL.xlsm que permite observar la distribución de modos y realizar un análisis según el criterio de Bonello.
### Frecuencia de Schroeder
En zona inferior de la aplicación aparecen los siguientes datos:
- Volumen del recinto: calculado automáticamente.
- Tiempo de reverberación a frecuencias medias Tmid : debe ser ingresado por el usuario.
- Frecuencia de Schroeder: con los datos del Volumen y el Tmid, la aplicación calcula la frecuencia de corte a partir de la cual se estima que el comportamiento ondulatorio del recinto deja de ser relevante. **Esta frecuencia debe tomarse a modo indicativo, ya que dependerá también de la morfología del recinto bajo análisis.**

## Ejemplo práctico
### Importando modelo geométrico
Procedemos a utilizar la herramienta *Importar modelo* > *Importar STL* y buscamos el archivo *conferencia.stl* dentro de la carpeta *models*. Al finalizar se genera la geometría:

![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/002.png)

Al inspeccionar el modelo se verifica una baja calidad en la morfología de las superficies curvas. Para mejorar esto se debe utilizar la herramienta *Resoluciones*. Debido a que el archivo importado es .*stl*, es posible aumentar la resolución angular entre caras. Seleccionar la opción* Extra alta* y verificar que las curvas han sido mejoradas considerablemente.

![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/003.png)

La resolución de la malla también puede aumentarse (lo que incrementará el tiempo de cálculo). Generalmente deberá utilizarse la opción *Normal* que viene por defecto.

![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/004.png)

**Cabe destacar que el ajuste de estas resoluciones no es obligatorio, dependerá exclusivamente de la complejidad del modelo**. El cálculo puede efectuarse directamente luego de importar el modelo ya que la aplicación utilizará las resoluciones por defecto (*Normal*).

Con el mouse es posible interactuar con la geometría. Con el botón izquierdo se rota la vista y con el derecho se desplaza el plano actual. Manteniendo apretado el botón central y moviendo el mouse hacia arriba y abajo se logra hacer zoom-in y zoom-out. Estas acciones también pueden llevarse a cabo con los controles superiores del panel gráfico.
### Cálculo
Una vez importado el modelo se deberá ingresar el valor del Tmid. Para este ejemplo utilizaremos el valor de 0.90 segundos, por lo que la frecuencia de Schroeder será de 96.6 Hz.

A continuación, hacemos clic en *Calcular* y vemos que la aplicación recomienda obtener, al menos, 45 frecuencias para alcanzar a cubrir la frecuencia de Schroeder . Sin modificar estos valores, procedemos a calcular.

![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/005.png)

Una vez finalizado, observamos que se han generado el gráfico de modos y la tabla de resultados con las frecuencias propias, la cual llega hasta los 105 Hz, por lo que alcanza a cubrir la frecuencia de Schroeder. Para inspeccionar dentro de la sala, hay que ocultar algunas caras utilizando la herramienta *Contornos*. Luego, volvemos a *Graficar modos* para continuar con la inspección.

![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/006.png)

Ajustamos la vista, seleccionamos la frecuencia de 49.3 Hz, una división de niveles de 20 e interactuamos con el control deslizable para observar el comportamiento de las isocurvas.

![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/007.png)

Finalmente, procedemos a realizar el estudio de distribución de modos y el análisis según el criterio de Bonello. Para esto, copiamos el contenido de la tabla de resultados al portapapeles con la herramienta indicada en la barra superior de la tabla. Luego, clic en *Planilla de análisis* . Una vez abierta, clic en el botón *Importar Datos* para importar las frecuencias. A continuación, nombramos la sala como *Conferencia* y observamos en la hoja *Evaluación* los siguientes resultados:

![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/008.png)

Según se aprecia, el estudio alcanza hasta la banda de tercio de octava de 100 Hz, debido al corte por la frecuencia de Schroeder. En este ejemplo, la distribución de modos cumple con el criterio de Bonello.
## SketchUp Online
Es recomendable realizar los modelos utilizando el programa de dibujo SketchUp, fundamentalmente por su sencillez y rapidez. El mismo permite exportar los modelos al formato .stl para ser luego importados a la aplicación.

En caso de no contar con este programa, existe una versión online que permite diseñar y modelar salas de manera gratuita. Al hacer clic se abrirá la pagina de inicio de sesión. Se podrá crear una cuenta de Trimble o conectarse con una cuenta de Google o Apple.

![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/009.png)

Una vez creado nuestro usuario, aparecerá la pantalla de inicio en donde se mostrarán los modelos realizados. Para comenzar uno nuevo, clic en Crear nuevo. También permite abrir un archivo .skp almacenado en el ordenador.

![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/010.png)

Una vez modelada la sala, es buena práctica seleccionar todas las caras, hacer clic derecho y elegir la opción *Crear grupo*. De este modo, haciendo nuevamente clic derecho y seleccionando la opción* Información de la entidad*, deberá informarnos del volumen de la sala. En caso contrario, habrá que revisar el modelo ya que el mismo no se ha cerrado, lo que producirá errores al intentar importarlo en la aplicación.

![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/011.png)
![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/012.png)

Finalmente, para guardar el modelo en el ordenador se debe hacer clic en el menú desplegable y elegir la opción *Descargar* > *STL*. Este archivo es el que se importará a la aplicación.

![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/013.png)

## Contacto
Ing. Agustín Ylio Arias

[agustin.arias@outlook.com](mailto:agustin.arias@outlook.com)

https://github.com/Ylio7

https://www.linkedin.com/in/agustin-ylio-arias/
