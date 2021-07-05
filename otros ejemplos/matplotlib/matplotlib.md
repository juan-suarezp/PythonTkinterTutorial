# Matplotlib
Este es un ejemplo que muestra cómo agregar gráficas de matplotlib a una GUI de tkinter.

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana con gráfica de matplotlib

"""
import math
import tkinter as tk
# Para trabajar con tkinter y matplotlib 
from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg as FigureCanvas
from matplotlib.backends.backend_tkagg import NavigationToolbar2Tk as Toolbar
from matplotlib.figure import Figure
 
def make_plot():
    # Se crea la señal
    Vp =  float(var_ampl.get()) # Voltios 
    fre = float(var_frec.get()) # Hz
    w = 2*math.pi*fre # rad/s
    fi = float(var_fase.get()) # rad

    # Función a graficar
    def f1(t):
        return Vp*math.sin(w*t+fi)

    # Listas con datos a graficar
    t = []
    v = []

    ciclos = 5 # Ciclos a graficar 
    puntos = 30 # Puntos por ciclo
    T = 1/fre # Periodo 
    deltat = T / puntos # Distancia entre puntos

    
    ti = 0 # Tiempo inicial
    # Calculo las parejas de puntos    
    for i in range(puntos*ciclos+1):
        t.append(ti)
        v.append(f1(ti))
        ti = ti + deltat

    # Se crean los objetos para mostrar la figura en tkinter
    # Cada vez que se da clic al botón "Graficar"    
    # Frame para la gráfica
    fr_grafica = tk.Frame(ventana) # se crea un nuevo frame dentro de la ventana
    fr_grafica.grid(row=1, column=0) # se ubica el nuevo frame 
    
    figure = Figure(figsize=(5,4)) # figura de matplotlib
    fig_canvas = FigureCanvas(figure, master=fr_grafica)
    fig_canvas.draw()
    #Configuración para que ocupe todo el espacio a lo ancho y alto
    fig_canvas.get_tk_widget().pack(side=tk.TOP, fill=tk.BOTH, expand=1)
    fig_canvas._tkcanvas.pack(side=tk.TOP, fill=tk.BOTH, expand=1)

    # Barra de herramientas de la figura 
    toolbar = Toolbar(fig_canvas, fr_grafica)
    toolbar.update()

    # Grafico 
    sub_figure = figure.add_subplot(111)
    sub_figure.plot(t,v)



# Construcción de la ventana y sus controles
ventana = tk.Tk() #Ventana principal
ventana.title("Crear gráfica!")

# Frame para agregar los entry y el botón
fr_datos_entrada = tk.Frame(ventana) 
fr_datos_entrada.grid(row=0, column=0)

# Amplitud
lbl_ampl = tk.Label(fr_datos_entrada, text="Amplitud [V]: ")
lbl_ampl.grid(column=0,row=0)

var_ampl = tk.StringVar(value='100')
ent_ampl = tk.Entry(fr_datos_entrada, textvariable = var_ampl)
ent_ampl.grid(column=1,row=0)

# Frecuencia
lbl_frec = tk.Label(fr_datos_entrada, text="Frecuencia [Hz]: ")
lbl_frec.grid(column=0,row=1)

var_frec = tk.StringVar(value='60')
ent_frec = tk.Entry(fr_datos_entrada, textvariable = var_frec)
ent_frec.grid(column=1,row=1)

# Fase inicial
lbl_fase = tk.Label(fr_datos_entrada,text="Fase inical [rad]: ")
lbl_fase.grid(column=0,row=2)

var_fase = tk.StringVar(value='0')
ent_fase = tk.Entry(fr_datos_entrada, textvariable = var_fase)
ent_fase.grid(column=1,row=2)

# Botón graficar
boton = tk.Button(fr_datos_entrada, text="Graficar", command=make_plot)
boton.grid(column=2,row=1)

# Llamo la función donde creo el resto de objetos y calculo los puntos 
make_plot()

# Opcional
# Para mantener la ventana de un tamaño fijo
# Fuente: https://stackoverflow.com/questions/10448882/how-do-i-set-a-minimum-window-size-in-tkinter
ventana.update()
ventana.minsize(ventana.winfo_width(), ventana.winfo_height())
ventana.maxsize(ventana.winfo_width(), ventana.winfo_height())

# Ejecuto la aplicación
ventana.mainloop()
```
El resultado es el siguiente:

![ventana matplotlib](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/otros%20ejemplos/matplotlib/ventanamatplotlib.png)

La ventana permite ingresar la amplitud en V, la frecuencia en Hz y la fase inicial en Rad. Al llenar todos los campos, con el botón graficar se actualiza la gráfica con los parámetros actuales ingresados.

A continuación se explica el código por partes:

```python
import math
import tkinter as tk
# Para trabajar con tkinter y matplotlib 
from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg as FigureCanvas
from matplotlib.backends.backend_tkagg import NavigationToolbar2Tk as Toolbar
from matplotlib.figure import Figure
```
Aquí se importan los módulos necesarios como math y tkinter. Los últimos tres son necesarios para agregar la gráfica a la interfaz.

```python
def make_plot():
    # Se crea la señal
    Vp =  float(var_ampl.get()) # Voltios 
    fre = float(var_frec.get()) # Hz
    w = 2*math.pi*fre # rad/s
    fi = float(var_fase.get()) # rad

    # Función a graficar
    def f1(t):
        return Vp*math.sin(w*t+fi)

    # Listas con datos a graficar
    t = []
    v = []

    ciclos = 5 # Ciclos a graficar 
    puntos = 30 # Puntos por ciclo
    T = 1/fre # Periodo 
    deltat = T / puntos # Distancia entre puntos

    
    ti = 0 # Tiempo inicial
    # Calculo las parejas de puntos    
    for i in range(puntos*ciclos+1):
        t.append(ti)
        v.append(f1(ti))
        ti = ti + deltat

    # Se crean los objetos para mostrar la figura en tkinter
    # Cada vez que se da clic al botón "Graficar"    
    # Frame para la gráfica
    fr_grafica = tk.Frame(ventana) # se crea un nuevo frame dentro de la ventana
    fr_grafica.grid(row=1, column=0) # se ubica el nuevo frame 
    
    figure = Figure(figsize=(5,4)) # figura de matplotlib
    fig_canvas = FigureCanvas(figure, master=fr_grafica)
    fig_canvas.draw()
    #Configuración para que ocupe todo el espacio a lo ancho y alto
    fig_canvas.get_tk_widget().pack(side=tk.TOP, fill=tk.BOTH, expand=1)
    fig_canvas._tkcanvas.pack(side=tk.TOP, fill=tk.BOTH, expand=1)

    # Barra de herramientas de la figura 
    toolbar = Toolbar(fig_canvas, fr_grafica)
    toolbar.update()

    # Grafico 
    sub_figure = figure.add_subplot(111)
    sub_figure.plot(t,v)
```
Como su nombre `make_plot` lo indica, se define una función que crea la gráfica y la agrega a la interfaz. La función no tiene parámetros de entrada debido a que las variables para graficar las obtiene a partir de los valores ingresados en los entry (ver [Tkinter Entry](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/entry/entry.md)). Esto se hace en las primeras líneas de la función, por ejemplo para `Vp`, por medio de `float(var_ampl.get())` se obtiene el valor de la amplitud ingresado en el entry correspondiente de la interfaz. Así mismo para la frecuencia `fre` y la fase inicial `fi`.

Con los tres valores obtenidos de los entry, es posible hallar las listas de tiempo y tensión; para esto se define la función `f1` que retorna la función sinusoidal, la cantidad de ciclos a gráficar, el número de puntos por ciclo y el periodo, para finalmente hallar la separación entre puntos. Con esta información y la función `f1` se llenan las listas de tiempo y tensión que se van a graficar.

Finalmente, se crea un objeto tipo figura de matplotlib y un frame (ver [Tkinter Frame](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/frame/frame.md)) que servirá como widget para agregar la gráfica a la interfaz. Luego se crea un objeto tipo FigureCanvas que usa los dos objetos anteriores para crear y agregar la gráfica a la interfaz. Finalmente, se crea y se agrega también una barra de herramientas `toolbar`.

Cabe resaltar que se crea una "subfigura" del objeto tipo figura de matplotlib y finalmente es en este objeto que se ejecuta el comando `plot(t,v)` y demás cambios que se quieran realizar a la gráfica, como por ejemplo cambiar el título, los títulos de los ejes, etc.

```python
# Construcción de la ventana y sus controles
ventana = tk.Tk() #Ventana principal
ventana.title("Crear gráfica!")

# Frame para agregar los entry y el botón
fr_datos_entrada = tk.Frame(ventana) 
fr_datos_entrada.grid(row=0, column=0)

# Amplitud
lbl_ampl = tk.Label(fr_datos_entrada, text="Amplitud [V]: ")
lbl_ampl.grid(column=0,row=0)

var_ampl = tk.StringVar(value='100')
ent_ampl = tk.Entry(fr_datos_entrada, textvariable = var_ampl)
ent_ampl.grid(column=1,row=0)

# Frecuencia
lbl_frec = tk.Label(fr_datos_entrada, text="Frecuencia [Hz]: ")
lbl_frec.grid(column=0,row=1)

var_frec = tk.StringVar(value='60')
ent_frec = tk.Entry(fr_datos_entrada, textvariable = var_frec)
ent_frec.grid(column=1,row=1)

# Fase inicial
lbl_fase = tk.Label(fr_datos_entrada,text="Fase inical [rad]: ")
lbl_fase.grid(column=0,row=2)

var_fase = tk.StringVar(value='0')
ent_fase = tk.Entry(fr_datos_entrada, textvariable = var_fase)
ent_fase.grid(column=1,row=2)

# Botón graficar
boton = tk.Button(fr_datos_entrada, text="Graficar", command=make_plot)
boton.grid(column=2,row=1)

# Llamo la función donde creo el resto de objetos y calculo los puntos 
make_plot()

# Opcional
# Para mantener la ventana de un tamaño fijo
# Fuente: https://stackoverflow.com/questions/10448882/how-do-i-set-a-minimum-window-size-in-tkinter
ventana.update()
ventana.minsize(ventana.winfo_width(), ventana.winfo_height())
ventana.maxsize(ventana.winfo_width(), ventana.winfo_height())

# Ejecuto la aplicación
ventana.mainloop()
```
En el final del código se define la ventana principal y los widgets que están en ella. Se usan widgets como label (ver [Tkinter Label](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/label/label.md)), entry (ver [Tkinter Entry](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/entry/entry.md)), button (ver [Tkinter Button](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/button/button.md)) y frame (ver [Tkinter Frame](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/frame/frame.md)).
