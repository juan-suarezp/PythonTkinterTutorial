# Ejemplo Proyecto
En este ejemplo se crea una interfaz que permite seleccionar una carpeta para listar los [archivos .lis](https://github.com/juan-suarezp/PythonTkinterTutorial/tree/master/otros%20ejemplos/proyecto) (cir0, cir1 y cir2) que hay en ella. Finalmente, es posible seleccionar uno de estos archivos para graficar en la interfaz.

`Nota:` para descargar los archivos .lis, ingresar al archivo que quiere descargar.

![imagen archivo](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/otros%20ejemplos/proyecto/imagenarchivo.png)

Dar click derecho al botón `Raw` y después "guardar como..." o "guardar enlace como...". Esto permite descargar los archivos.

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana que procesa archivos .lis de ATP

"""
#Importo las librerías necesarias
import os
import math
import tkinter as tk
import matplotlib.pyplot as plt
from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg as FigureCanvas
from matplotlib.backends.backend_tkagg import NavigationToolbar2Tk as Toolbar


class main(tk.Tk):
    """
    Esta es la clase principal
    
    """
    def __init__(self, parent):
        tk.Tk.__init__(self, parent)
        self.initUI()


    def initUI(self):
        """
        Define la ventana y los widgets. Conecta los botones con los métodos
        
        """
        self.grid()
        
        #Botones
        botonCarpeta = tk.Button(self, text="Seleccionar Carpeta",
                                 command=self.getDirectory)
        botonCarpeta.grid(column=0, row=0)
        botonGraficar = tk.Button(self, text="Graficar",
                                  command=self.Graficar)
        botonGraficar.grid(column=1, row=3, sticky="w")
        
        #Label
        self.VarLabelRuta = tk.StringVar()
        self.VarLabelRuta.set("Ruta archivo:")
        self.labelRuta = tk.Label(self, textvariable=self.VarLabelRuta)
        self.labelRuta.grid(column=1, row=0, sticky="w")
        
        #Frame para lista y barra de desplazamiento
        framelista = tk.Frame(self)
        framelista.grid(column=0, row=1, rowspan=3, sticky="NESW")
        #Barra de desplazamiento con orientación vertical
        scrollbar = tk.Scrollbar(framelista, orient=tk.VERTICAL)
        scrollbar.pack(side=tk.RIGHT, fill=tk.Y) #Ubicarla a la derecha
        #Crear la lista y vincular con la barra de desplazamiento
        self.listbox = tk.Listbox(framelista, yscrollcommand=scrollbar.set,
                                  selectmode="single", height=29, width=32)
        scrollbar.config(command=self.listbox.yview)
        #Comando cuando se selecciona un objeto de la lista
        self.listbox.bind("<<ListboxSelect>>", self.SelArchivo)
        self.listbox.pack(expand=True, fill=tk.BOTH)
        
        #Crea las gráficas
        #Frame para la gráfica 1
        framegrafica1 = tk.Frame(self)
        framegrafica1.grid(column=1, row=1, columnspan=2, sticky="NESW")
        self.figure1 = plt.figure(num=1, figsize=(6,2))
        self.canvas1 = FigureCanvas(self.figure1, master=framegrafica1)
        toolbar1 = Toolbar(self.canvas1, framegrafica1)
        toolbar1.update()
        self.canvas1.get_tk_widget().pack(expand=True, fill=tk.BOTH)
        
        #Frame para la gráfica 2
        framegrafica2 = tk.Frame(self)
        framegrafica2.grid(column=1, row=2, columnspan=2, sticky="NESW")
        self.figure2 = plt.figure(num=2, figsize=(6,2))
        self.canvas2 = FigureCanvas(self.figure2, master=framegrafica2)
        toolbar2 = Toolbar(self.canvas2, framegrafica2)
        toolbar2.update()
        self.canvas2.get_tk_widget().pack(expand=True, fill=tk.BOTH)
        
        #Cambiar tamaño de filas y columnas de la grid con cambio en ventana
        self.grid_columnconfigure(0, weight=0) #Columna 0 no cambia de tamaño
        self.grid_columnconfigure(1, weight=1)
        self.grid_columnconfigure(2, weight=1)
        self.grid_rowconfigure(0, weight=0) #Fila 0 no cambia de tamaño
        self.grid_rowconfigure(1, weight=1)
        self.grid_rowconfigure(2, weight=1)
        self.grid_rowconfigure(3, weight=1)
        
        
    def getDirectory(self):
        """
        Obtiene y muestra la ruta de la carpeta seleccionada en el diálogo,
        también lista los archivos .lis que hay en la carpeta
        
        """
        self.cwd = os.getcwd() #Ubicación actual
        #Crea el diálogo para seleccionar carpeta
        self.carpeta = tk.filedialog.askdirectory(parent=self,
                                                  initialdir=self.cwd,
                                                  title='Seleccionar carpeta')
        #Borra los nombres de archivos que se están mostrando en la lista
        self.listbox.delete(0, self.listbox.size())
        
        #Evalúa si seleccionó una carpeta
        if len(self.carpeta) > 1:
            #Cambia el texto en el label de la ruta
            self.VarLabelRuta.set("Ruta archivo: "+self.carpeta)
            #Lista de los archivos .lis en la carpeta seleccionada
            self.listArchivos = os.listdir(self.carpeta)
            for i in self.listArchivos:
                if ".lis" in i:
                    self.listbox.insert(tk.END, i)
                    
                    
    def SelArchivo(self, lista):
        """
        Obtiene y muestra la ruta del archivo seleccionado de la lista
        
        """
        try:   
            #Nombre del archivo seleccionado
            text = lista.widget.get(lista.widget.curselection()[0])
            
            self.ruta = os.path.join(self.carpeta, text) #Ruta del archivo
            
            #Cambia el texto en el label de la ruta
            self.VarLabelRuta.set("Ruta archivo: "+self.ruta)
        except:
            pass

        
    def valorRMS(self, lista):
        """
        Recibe una lista con valores numéricos y calcula el valor RMS
        discreto
        
        """
        total = 0
        for i in lista:
            total = total + i**2
        return math.sqrt(total/len(lista))
    
    
    def Graficar(self):
        """
        Si hay un archivo .lis seleccionado lo procesa y muestra la gráfica en
        la interfaz
        
        """
        try:
            file = open(self.ruta, encoding="ISO-8859-1") #Abre el archivo
            
        #Lee las primeras líneas y obtiene información de cuantas señales hay 
            for line in file:
                if "Column headings for the" in line:
                    numVar = int(line[24:27])
                    datos = []
                    for i in range(numVar+1):
                        datos.append([])
                if "      0" in line[0:7]:
                    lista_tmp = line.split()
                    for i in range(1,len(lista_tmp)):
                        datos[i-1].append(float(lista_tmp[i]))
                    break
            
            #Lee los datos de las señales y guarda la información en listas 
            for line in file:
                if "\n" == line:
                    break
                if not("  % % % % % %" in line or "  Done dumping" in line):
                    lista_tmp = line.split()
                    for i in range(1,len(lista_tmp)):
                        datos[i-1].append(float(lista_tmp[i]))
                else:
                    continue
                
            file.close()
            
            t = datos[0] #tiempo
            v = datos[1] #Voltaje
            
            #Encontrar número de datos en un periodo n
            for i in range(len(v)):
                if v[i] >= 0 and v[i+1] < 0:
                    i1 = i
                    break
            
            for i in range(i+1,len(v)):
                if v[i] >= 0 and v[i+1] < 0:
                    i2 = i
                    break    
    
            Vrms = [] #Valores RMS discretos
            n = int((i2-i1)/2)
            
            for i in range(0,len(v)):
                if i>=n:
                    Vrms.append(self.valorRMS(v[i-n:i]))
            
            #Grafica la señal
            ax1 = self.figure1.add_subplot(111)
            #Descarta la gráfica anterior
            ax1.cla()
            ax1.plot(t, v, label="Voltage signal")
            ax1.plot(t[n:], Vrms, label="Voltage RMS")
            ax1.set_title("Voltage vs Time")
            ax1.set_xlabel("Time (s)") #
            ax1.set_ylabel("Voltage (V)")
            ax1.grid(True)
            ax1.legend(loc="best")
            self.canvas1.draw()
            
            #Encuentra tiempo caída de tensión
            Vref = max(Vrms)
            for i in range(len(Vrms)):
                if Vrms[i] <= Vref *0.9:
                    y1 = i
                    break
            
            for i in range(i+1,len(Vrms)):
                if Vrms[i] >= Vref*0.9:
                    y2 = i
                    break
            
            #Grafica la parte de la caída en la señal
            ax2 = self.figure2.add_subplot(111)
            #Descarta la gráfica anterior
            ax2.cla()
            ax2.plot(t[y1-n*2:y2+n*3], v[y1-n*2:y2+n*3],
                     label="Voltage signal")
            ax2.plot(t[n+y1-n*2:y2+n*3+n], Vrms[y1-n*2:y2+n*3],
                     label="Voltage RMS")
            ax2.set_title("Voltage vs Time")
            ax2.set_xlabel("Time (s)") #
            ax2.set_ylabel("Voltage(V)")
            ax2.grid(True)
            ax2.legend(loc="best")
            self.canvas2.draw()
        except:
            pass

        
ventana = main(None)
ventana.minsize(width=645, height=494) #Tamaño inicial y mínimo de la ventana
ventana.mainloop()
```
