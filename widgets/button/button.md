# Tkinter Button
Permite agregar botones a la GUI. Estos botones pueden mostrar una imagen o texto que indiquen su función y normalmente se conectan a una función o método que es llamado cuando el botón es presionado.

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con botón que abre una ventana de mensaje

"""
#Importamos las librerías necesarias
import tkinter as tk

def accion():
    tk.messagebox.showinfo("Título","Mensaje") #Crea la ventana del mensaje

ventana = tk.Tk() #Crea la ventana principal
ventana.geometry("200x200") #Tamaño de la ventana en pixeles
    
#Crea el botón y lo conecta con la función
boton = tk.Button(ventana,text="Realizar acción",command=accion)
boton.place(x=100,y=100) #Lo ubica en la ventana principal (pixeles)
#boton.pack(side="bottom") #(Arriba, abajo, derecha, izquierda)
#boton.grid(row=0, column=0) #(Fila y columna)

ventana.mainloop()
```

El resultado es el siguiente:

![ventana button](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/button/ventanabutton.png)

Al presionar el botón se ejecuta la función `accion` que abre la siguiente ventana:

![ventana mensaje](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/button/mensajebutton.png)

Esta es una ventana predeterminada de tkinter que permite cambiar el título y el mensaje que aparece en ella.

La ventana principal se crea con `tk.Tk` y se cambia su tamaño con `ventana.geometry`. Luego, se crea el botón con `tk.Button` indicando el widget que lo va a contener, en nuestro caso `ventana`. En este ejemplo se usan las opciones `text` y `command`, la primera permite mostrar texto en el botón y la segunda permite conectar el botón con alguna función o método al ser presionado. Finalmente, se agrega el botón con `boton.place`; como se observa en el archivo [readme](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/README.md), es posible agregar el widget con los métodos `pack` o `grid` que están comentados en este ejemplo.

[Aquí](https://www.tutorialspoint.com/python3/tk_button.htm) para ver más opciones de Button.
