"""Importer modules"""
#Importer Tkinter
from tkinter import*
#Importer random
from random import*


#Créer la fenêtre
window=Tk()


"""Personaliser la fenêtre"""
#Renommer la fenêtre
window.title("Jeu")
#Taille de la fenêtre
window.geometry("1103x530")
#Taille minimale de la fenêtre
window.minsize(943,530)
window.maxsize(943,530)
#Icon de la fenêtre
window.iconbitmap("icon.ico")
#Couleur de fond
window.config(background='#4065A4')


"""Barre de menu"""
#Créer la barre de menu
menu_bar = Menu(window)
window.config(menu=menu_bar)
#Menu "Fichier"
menu_file = Menu(menu_bar, tearoff=0)
menu_bar.add_cascade(menu=menu_file, label="Fichier")
#Sous menu Quitter
def quit():
    window.destroy()
menu_file.add_command(label="Quitter",command=quit)


calculation_left_frame=Frame(window, bg='#4065A4')


result=IntVar
total=0


total_label=Label(calculation_left_frame, text="Tu as " + str(total) + " bonnes réponses", bg='#4065A4', fg='white', font=('AR BLANCA', 20))
performs_label=Label(calculation_left_frame, text="Effectue", bg='#4065A4', fg='white', font=('AR BLANCA', 20))
calculation_label=Label(calculation_left_frame, bg='#4065A4', fg='white', font=('AR BLANCA', 20))
var_entry=IntVar
calculation_entry=Entry(calculation_left_frame, bg='#4065A4', fg='white', font=('Arial', 20), width=18)
exact_label=Label(calculation_left_frame, text="C'est exact !", bg='#4065A4', fg='white', font=('AR BLANCA', 20))
false_label=Label(calculation_left_frame, text="C'est faux, recommence !", bg='#4065A4', fg='white', font=('AR BLANCA', 20))


fond=PhotoImage(file="background.png")
label_fond=Label(window, image=fond)
fond_victoire=PhotoImage(file="background victoire.png")
label_fond_victoire=Label(window, image=fond_victoire)

def calcul():
    #Nombre 1
    list_number1=[2,3,4,5,6,7,8,9]
    shuffle(list_number1)
    number1=list_number1[0]
    #Nombre 2
    list_number2=[2,3,4,5,6,7,8,9]
    shuffle(list_number2)
    number2=list_number2[0]
    result=number1*number2
    calculation_label=Label(calculation_left_frame, bg='#4065A4', fg='white', font=('AR BLANCA', 20), text=str(number1)+"X"+str(number2))
    calculation_label.grid(row=2, column=0, sticky=W, ipadx=100)
    if our_result==result:
        total_label.destroy()
        total=total+1
        total_label.grid(row=0, column=0, sticky=W, ipadx=50)
        false_label.destroy()
        exact_label.grid(row=5, column=0, sticky=W, ipadx=70)
    else:
        exact_label.destroy()
        false_label.grid(row=5, column=0, sticky=W)
    if total==5:
        label_fond.destroy()
        label_fond_victoire.pack(side=RIGHT)
        total=0


calcul_button=Button(calculation_left_frame, bg='#4065A4', fg='white', font=('AR BLANCA',20), text="nouveau calcul", width=12, command=calcul)


def valid ():
    our_result=calculation_entry.get()

valid_button=Button(calculation_left_frame, bg='#4065A4', fg='white', font=('AR BLANCA',20), text="valider", width=12, command=valid)


def play():
    calcul_button.grid(row=6, column=0, sticky=W, ipadx=53, pady=20)
    performs_label.grid(row=1, column=0, sticky=W, padx=80)
    calculation_entry.grid(row=3, column=0, sticky=W)
    total_label.grid(row=0, column=0, sticky=W, ipadx=0)
    label_fond.pack(side=RIGHT)
    calculation_left_frame.pack(side=LEFT, padx=90)
    valid_button.grid(row=4, column=0, sticky=W, ipadx=53, pady=20)
    our_result=IntVar
    total=0
    play_button.destroy()



play_button=Button(window, text="Play", bg='#B00000', fg='white', font=('AR BLANCA', 30),width=10, command=play)
play_button.pack(expand=YES)

#Afficher la fenêtre
window.mainloop()
