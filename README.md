try:
    import tkinter as tk
    import requests
    
except:
    import tkinter as tk
    import requests

DELAY = 7000

def update_cursor():
    if cursor["fg"] == "black":
        cursor.config(fg="#3ADF00")
    else:
        cursor.config(fg="black") 
    cursor.after(DELAY, update_cursor)

def update_cursor1():
    if cursor1["fg"] == "black":
        cursor1.config(fg="#DF0000")
    else:
        cursor1.config(fg="black")
        cursor1.after(DELAY, update_cursor1)

def leerligas():
    f = open("archivo.txt", "r")
    while(True):
        linea = f.readline()
        return linea
        if not linea:
            break
    f.close()


def leer():
    liga = leerligas()
    #liga = requests.get('http://multitenant.eficasia.com/cardif')
    cadena = str(liga)
    return cadena
    

root = tk.Tk()
root.geometry("280x710")
root.title("Cardif Test")
root.config(bg="black")

leer()
if ('200' in leer()):
    tk.Label(root, text="Servicio Atento:", fg="#3ADF00", bg="black", font=("Courier", 15)).pack(side=tk.LEFT)
    cursor = tk.Label(root, fg="#3ADF00", bg="black", text=" OK", font=("Courier", 15))
    cursor.pack(side=tk.LEFT)
    cursor.after(0, update_cursor)
    
else:        
    tk.Label(root, text="Servicio Atento:", fg="#3ADF00", bg="black", font=("Courier", 15)).pack(side=tk.LEFT)
    cursor1 = tk.Label(root, fg="#3ADF00", bg="black", text="Error", font=("Courier", 15))
    cursor1.pack(side=tk.LEFT)
    cursor1.after(0, update_cursor1)
    leerligas()


root.mainloop()





