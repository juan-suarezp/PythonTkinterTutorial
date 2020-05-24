# Tkinter Messagebox
Permite crear ventanas predeterminadas con mensajes de error, pregunta, información o advertencia.

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con varios messagebox

"""
import tkinter as tk
# import tkinter.ttk as ttk

class Example(tk.Frame): #Ventana principal
    def __init__(self,main):
        super().__init__(main)
        self.initUI()


    def initUI(self):
        self.master.title("Message boxes") #Título de la ventana
        self.pack()

        #Botones con su respectiva función
        error = tk.Button(self, text="Error", command=self.Error)
        error.grid(padx=5, pady=5)
        warning = tk.Button(self, text="Warning", command=self.Warn)
        warning.grid(row=1, column=0)
        question = tk.Button(self, text="Question", command=self.Quest)
        question.grid(row=0, column=1)
        inform = tk.Button(self, text="Information", command=self.Info)
        inform.grid(row=1, column=1)


    def Error(self):
        tk.messagebox.showerror("Error", "Could not open file")

    def Warn(self):
        tk.messagebox.showwarning("Warning", "Deprecated function call")

    def Quest(self):
        tk.messagebox.askquestion("Question", "Are you sure to quit?")

    def Info(self):
        tk.messagebox.showinfo("Information", "Download completed")


def main():
    root = tk.Tk()
    root.geometry("300x150+300+300")
    ex = Example(root)
    ex.mainloop()


if __name__ == '__main__':
    main()
```
El resultado es el siguiente:

![ventana messagebox](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/messagebox/ventanamessagebox.png)

En este ejemplo se crea una clase para la interfaz, en la cual se definen cuatro botones (ver [Tkinter Button](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/button/button.md)), error, warning, question e inform; conectados a los métodos `Error`, `Warn`, `Quest` y `Info` respectivamente. Cada uno de estos métodos abre una ventana predeterminada de `tk.messagebox` diferente, así:

![funcion messagebox](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/messagebox/funcionmessagebox.png)

En cada uno de estos métodos, se define el título de la ventana y el mensaje que va a aparecer en la misma.
