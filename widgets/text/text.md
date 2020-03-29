# Tkinter Text
El widget text permite editar y mostrar texto (también imágenes). Permite editar el formato del texto, como por ejemplo la fuente, el color o el tamaño de letra.

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con text

"""
#Importamos las librerías necesarias
import tkinter as tk
import os

ventana = tk.Tk() #Crea la ventana principal

cwd = os.getcwd() #Ruta actual del archivo
#Crea un widget text
text1 = tk.Text(ventana, height=31, width=53, state=tk.DISABLED)
#Crea la imagen de tk
foto = tk.PhotoImage(file=os.path.join(cwd,"Shakespeare.gif"))

text1.image_create(tk.END, image=foto) #Inserta la imagen en el text

text1.pack(side=tk.LEFT) #Ubica el text a la izquierda de la ventana

#Crea otro widget text y una barra de desplazamiento
text2 = tk.Text(ventana, height=31, width=45)
scroll = tk.Scrollbar(ventana, command=text2.yview)
text2.configure(yscrollcommand=scroll.set)

#Etiqueta el formato para los textos que se van a insertar en el widget
text2.tag_configure('big', font=('Verdana', 20, 'bold'))
text2.tag_configure('color', foreground='#476042',
                    font=('Tempus Sans ITC', 12, 'bold'))

#Inserta el texto
text2.insert(tk.END,'\nWilliam Shakespeare\n', 'big')

texto2 = """
William Shakespeare fue un dramaturgo, poeta y actor inglés.
Conocido en ocasiones como el Bardo de Avon,
Shakespeare es considerado el escritor más
importante en lengua inglesa y uno de los más
célebres de la literatura universal."""
text2.insert(tk.END, texto2, 'color')

text2.pack(side=tk.LEFT) #Ubica el otro text a la derecha
scroll.pack(side=tk.RIGHT, fill=tk.Y)

ventana.mainloop()
```
El resultado es el siguiente:

![ventana text](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/text/ventanatext.png)

En este ejemplo hay dos text, text1 y 2. También hay una barra de desplazamiento (ver [Tkinter Scrollbar](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/scrollbar/scrollbar.md)) para el text2.

Para Text 1 (el de la izquierda):
- Se define el widget que lo va a contener y las opciones `height`, `width` y `state`. `height` y `width` indican la geometría del text y  `state` indican si es posible ingresar más texto, en este caso `tk.DISABLED` no permite realizar cambios en el text.
- El text1 va a mostrar una [imagen](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/text/Shakespeare.gif), que se crea con `foto = tk.PhotoImage(file=os.path.join(cwd,"Shakespeare.gif"))` (cwd es la ruta del directorio actual de trabajo, por lo que la imagen debe estar guardada en este directorio o donde esté guardado el archivo .py) y se inserta con `text1.image_create(tk.END, image=foto)`.

Para Text2 (el de la derecha):
- Se define el widget que lo va a contener y las opciones `height` y `width` para indicar su geometría.
- El text2 va a mostrar texto, para esto se definen dos etiquetas, por ejemplo `text2.tag_configure('big', font=('Verdana', 20, 'bold'))`, que indican el formato de un texto a insertar y con `text2.insert(ubicación en el text, texto a insertar, etiqueta formato)` se inserta el texto al widget.

[Aquí](https://www.tutorialspoint.com/python3/tk_text.htm) para ver más opciones de Text.
