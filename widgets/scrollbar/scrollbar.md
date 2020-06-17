# Tkinter Scrollbar
Permite agregar una barra de desplazamiento para moverse en dos direcciones en un widget.

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con scrollbar

"""
#Importamos las librerías necesarias
import tkinter as tk

def mostrar():
    #Verifica si hay algún elemento seleccionado y lo muestra
    if len(listbox.curselection()) != 0:
        seleccion=''
        for ind in listbox.curselection():
            seleccion = seleccion+listbox.get(ind)+"\n"
        print(seleccion)

ventana = tk.Tk() #Crea la ventana principal

#Se crea un frame
frame = tk.Frame(ventana)
frame.pack()

# Crear una barra de deslizamiento con orientación vertical
scrollbar1 = tk.Scrollbar(frame, orient=tk.VERTICAL)
# Ubicarla a la derecha.
scrollbar1.pack(side=tk.RIGHT, fill=tk.Y)

#Crear la lista y vincular con la barra de deslizamiento.
listbox = tk.Listbox(frame, yscrollcommand=scrollbar1.set, selectmode="single")
scrollbar1.config(command=listbox.yview)

# Insertar 20 elementos
for i in range(20):
    listbox.insert(i, "Elemento {}".format(i))

listbox.pack()
        
#Se crea un botón y se conecta con la función
boton = tk.Button(ventana,text="Mostrar selección",command=mostrar)
boton.pack()

ventana.mainloop()
```
El resultado es el siguiente:

![ventana scrollbar](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/scrollbar/ventanascrollbar.png)

Este ejemplo muestra cómo configurar la scrollbar para mover hacia arriba o abajo un widget, en este caso, una listbox.

Se crea un frame (ver [Tkinter Frame](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/frame/frame.md)) para contener una scrollbar y una listbox (ver [Tkinter Listbox](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/listbox/listbox.md)). Además, se crea un botón (ver [Tkinter Button](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/button/button.md)) que está conectado a la función `mostrar`. La función muestra en la terminal los elementos que están seleccionados de la lista, así:

![funcion scrollbar](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/scrollbar/funcionscrollbar.png)

Después de crear la `tk.Tk`, se define el frame, la scrollbar, la listbox, la función y el botón. Para la scrollbar se indica el widget que la va a contener y `orient` que define la orientación de la barra. Al momento de definir la listbox se debe indicar `yscrollcommand=scrollbar1.set` y con `scrollbar1.config(command=listbox.yview)` (notar que ambos son en el eje y) se configura para que la scrollbar funcione en la listbox.

[Aquí](https://www.tutorialspoint.com/python3/tk_scrollbar.htm) para ver más opciones de Scrollbar.
