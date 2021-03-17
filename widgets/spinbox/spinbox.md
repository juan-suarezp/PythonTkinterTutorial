# Tkinter Spinbox
El widget spinbox permite guardar un grupo de opciones y seleccionar solo una de ellas. Es posible configurar el spinbox para que permita ingresar una opción por teclado.

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con spinbox

"""
#Importamos las librerías necesarias
import tkinter as tk

def mostrar():
    #Verifica si hay algún elemento seleccionado y lo muestra
    if spinbox.get() != "":
        print(spinbox.get())

ventana = tk.Tk() #Crea la ventana principal

#Insertar 20 elementos
lista = []
for i in range(20):
    lista.append("Elemento {}".format(i))

#Crear el widget spinbox
#State controla si se puede ingresar valores al spinbox por teclado
spinbox = tk.Spinbox(ventana, values=lista, state="readonly")
spinbox.pack()
        
#Se crea un botón y se conecta con la función
boton = tk.Button(ventana,text="Mostrar selección",command=mostrar
boton.pack()

ventana.mainloop()
```
El resultado es el siguiente:

![ventana spinbox](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/spinbox/ventanaspinbox.png)

Se crea un botón (ver [Tkinter Button](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/button/button.md)) que está conectado a la función `mostrar`. La función muestra en la terminal el elemento que está seleccionado en el spinbox, así:

![funcion spinbox](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/spinbox/funcionspinbox.png)

Después de crear la `tk.Tk`, se define el spinbox, la función y el botón. Para el spinbox se define el widget que lo va a contener y las opciones `values` y `state`. `values` indica la lista de opciones que va a guardar el spinbox, por esto, en el ejemplo los elementos se ingresan con `lista.append` antes de definir el widget. `state` indica el estado del spinbox, es decir, si está desactivado, si solo se puede seleccionar entre las opciones o si se puede ingresar una opción por teclado.

[Aquí](https://www.tutorialspoint.com/python3/tk_spinbox.htm) para ver más opciones de Spinbox.
