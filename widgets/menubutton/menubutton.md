# Tkinter Menubutton
Permite agregar un botón que despliega un menú parecido a las pestañas que se crean con [Tkinter Menu](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/menu/menu.md).

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con menubutton

"""
#Importamos las librerías necesarias
import tkinter as tk

def fun1(): #Crea una nueva ventana
    m = tk.Tk()
    Lb = tk.Label(m, text = "Hello Option 1 clicked")
    Lb.pack()
    m.mainloop()
    
#Muestra un mensaje en la ventana principal
def fun2():
    label = tk.Label(ventana, text = "Hello Option 2 clicked")
    label.pack()

ventana = tk.Tk() #Ventana principal
ventana.geometry("200x200")

#Se crea el menubutton
mb = tk.Menubutton(ventana , text = "Menu", relief = "raised" )
mb.pack()

#Se crea el menú que va conectado al menubutton
mb.menu = tk.Menu(mb)
mb["menu"] = mb.menu

#Se agregan los comandos directamente
#Es posible agregar otros widgets como radiobuttons o checkbutton al menú
mb.menu.add_command(label='New Window',command = fun1)
mb.menu.add_command(label='Add Text',command = fun2)
mb.menu.add_command(label='Salir...', command = ventana.destroy)

ventana.mainloop()
```
El resultado es el siguiente:

![ventana menubutton](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/menubutton/ventanamenubutton.png)

Al seleccionar el botón, se despliega un menú como se observa en la siguiente imagen. Cada una de las tres opciones está conectada a una función; `New Window` está conectada a `fun1`, `Add Text` a `fun2` y `Salir...` a `ventana.detroy` que es un método predeterminado para cerrar la ventana principal.

![funcion menubutton](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/menubutton/funcionmenubutton.png)

Al principio se definen la `tk.Tk` y las funciones. Luego, se define el menubutton indicando la ventana que lo va a contener, el texto que va a mostrar y `relief` que modifica el aspecto o relieve del botón. Después, es necesario crear un menú (ver [Tkinter Menu](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/menu/menu.md)) para desplegar desde el menubutton. Para agregar las opciones se usa `mb.menu.add_command` al igual que con los Tkinter Menu.

[Aquí](https://www.tutorialspoint.com/python3/tk_menubutton.htm) para ver más opciones de Menubutton.
