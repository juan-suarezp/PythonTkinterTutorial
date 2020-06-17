# Eventos

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana con eventos simples

"""
import tkinter as tk 

def Fun1(event): #Un click
    print("Single Click") 

def Fun2(event): #Doble click                
    print("Double Click")


Ventana = tk.Tk()
Ventana.title("Titulo ventana")
Ventana.geometry("320x100")

Boton = tk.Button(Ventana, text='Mouse Clicks')
Boton.pack()

#bind agrega conecta los eventos a los widgets
Boton.bind('<Button-1>', Fun1)
Boton.bind('<Double-1>', Fun2) 

Ventana.mainloop()

#Para ver más eventos:
#https://effbot.org/tkinterbook/tkinter-events-and-bindings.htm
```
