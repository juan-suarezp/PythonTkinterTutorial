# Matplotlib

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana con gráfica de matplotlib

"""
import math
import tkinter as tk
import matplotlib.pyplot as plt
from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg as FigureCanvas
from matplotlib.backends.backend_tkagg import NavigationToolbar2Tk as Toolbar
 
def make_plot():
    #Se crea la señal
    Vp =  float(var_ampl.get()) # Voltios 
    fre = float(var_frec.get()) # Hz
    w = 2*math.pi*fre # rad/s
    fi = float(var_fase.get()) # rad

    #Función
    def f1(t):
        return Vp*math.sin(w*t+fi)

    #Listas a graficar
    t = []
    v = []

    ciclos = 5 #Ciclos a graficar 
    puntos = 30 #Puntos por ciclo
    T = 1/fre #Periodo 
    deltat = T / puntos #Distancia entre puntos

    #Tiempo inicial
    ti = 0
    for i in range(puntos*ciclos+1):
        t.append(ti)
        v.append(f1(ti))
        ti = ti + deltat

    #Grafico
    #Frame para la gráfica
    framegrafica = tk.Frame(Ventana)
    framegrafica.grid(column=0, row=1, columnspan=3)
    figure = plt.figure(figsize=(5,4))
    canvas = FigureCanvas(figure, master=framegrafica)
    toolbar = Toolbar(canvas, framegrafica)
    toolbar.update()
    canvas.get_tk_widget().pack(expand=True, fill=tk.BOTH)
    sub_figure = figure.add_subplot(111)

    sub_figure.plot(t,v)


Ventana = tk.Tk() #Ventana principal
Ventana.title("Crear gráfica!")

Frame = tk.Frame(Ventana) #Frame para agregar los entry y el botón
Frame.grid(row=0, column=0)

#Amplitud
lbl_ampl = tk.Label(Frame, text="Amplitud [V]: ")
lbl_ampl.grid(column=0,row=0)

var_ampl = tk.StringVar(value='100')
ent_ampl = tk.Entry(Frame, textvariable = var_ampl)
ent_ampl.grid(column=1,row=0)

#Frecuencia
lbl_frec = tk.Label(Frame, text="Frecuencia [Hz]: ")
lbl_frec.grid(column=0,row=1)

var_frec = tk.StringVar(value='60')
ent_frec = tk.Entry(Frame, textvariable = var_frec)
ent_frec.grid(column=1,row=1)

#Fase inicial
lbl_fase = tk.Label(Frame,text="Fase inical [rad]: ")
lbl_fase.grid(column=0,row=2)

var_fase = tk.StringVar(value='0')
ent_fase = tk.Entry(Frame, textvariable = var_fase)
ent_fase.grid(column=1,row=2)

#Botón
boton = tk.Button(Frame, text="Graficar", command=make_plot)
boton.grid(column=2,row=1)

make_plot()

Ventana.mainloop()
```
