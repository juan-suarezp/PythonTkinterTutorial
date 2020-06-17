# Tkinter Checkbutton
Permite mostrar opciones como un botón de activación, el botón puede ir acompañado de texto o una imagen. Se usa cuando se puede seleccionar una o varias opciones a diferencia de [Tkinter Radiobutton](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/radiobutton/radiobutton.md).

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con checkbutton

"""
#Importamos las librerías necesarias
import tkinter as tk

def accion():
    v1 = variable1.get()
    v2 = variable2.get()
    if v1 == True and v2 == True:
        print("1 y 2 activados")
    elif v1 == True and v2 == False:
        print("1 activado y 2 desactivado")
    elif v1 == False and v2 == True:
        print("1 desactivado y 2 activado")
    else:
        print("1 y 2 desactivados")
        
ventana = tk.Tk() #Crea la ventana principal
        
variable1 = tk.BooleanVar() #Variables que guardan el estado de los checkbutton
variable2 = tk.BooleanVar()
#Crea los checkbutton y los conecta con la función y la variable respectiva
#La función se ejecuta cada que hay un cambio en el estado de los checkbutton
C1 = tk.Checkbutton(ventana,variable=variable1,text="1",height=5,width=20,
                    command=accion)
C2 = tk.Checkbutton(ventana,variable=variable2,text="2",height=5,width=20,
                    command=accion)
C1.pack()
C2.pack()

#Se crea un botón
#Ejecuta la función sin cambiar el estado de los checkbuton
boton = tk.Button(ventana, command=accion, text="Verificar")
boton.pack()

ventana.mainloop()
```
El resultado es el siguiente:

![ventana checkbutton](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/checkbutton/ventanacheckbutton.png)

El botón está conectado a la función `accion` (ver [Tkinter Button](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/button/button.md)), al igual que los checkbutton al cambiar de estado. La función muestra en la terminal el estado actual de los dos checkbutton como se observa a continuación:

![funcion checkbutton](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/checkbutton/funcioncheckbutton.png)

Después de crear la `tk.Tk` se define la función y los checkbutton. Para los checkbutton además de definir el widget que los va a contener, en este caso `ventana`, se definen las opciones `variable`, `text`, `command`, `height` y `width`. Las dos últimas definen el tamaño del chekbutton, `variable` guarda el estado actual del checkbutton `True` o `False`, `text` es el texto que acompaña el botón de activación y `command` permite llamar una función cuando cambia el estado del checkbutton.

[Aquí](https://www.tutorialspoint.com/python/tk_checkbutton.htm) para ver más opciones de Checkbutton.
