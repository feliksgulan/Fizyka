# Fizyka
Projekt zaliczeniowy 

import math
from math import cos
import matplotlib.pyplot as plt

class Czastka:
    nazwa: str
    d: float
    n: float

  def __init__(self, n, d, nazwa):
        self.n = n
        self.d = d
        self.nazwa = nazwa

pierwiastki = {
    "azot": Czastka(1.000298,3.6*10**-10 ,"azot"),
    "tlen": Czastka(1.000271, 3.46*10**-10, "tlen"),
    "metan": Czastka(1.000444, 3.8*10**-10, "metan"),
    "dwutlenek węgla": Czastka(1.00045, 3.3*10**-10, "dwutlenek węgla")
}

kolory= {
    "czerwony":7*10**-7,
    "fioletowy":4*10**-7,
    "niebieski":4.5*10**-7,
    "zielony":5.5*10**-7,
    "zolty":5.8*10**-7
}


def natezenie(czastka: Czastka, natezenie_poczatkowe: float, kat_rozproszenia: float, r: float,
              dlugosc_lambda: float):
    a=(1+cos(kat_rozproszenia)**2)/(2*(r**2))
    b= natezenie_poczatkowe*((2*math.pi/dlugosc_lambda)**4)
    c= ((czastka.n**2-1)/(czastka.n)**2+2)**2
    d= (czastka.d/2)**6
    return a*b*c*d

def natezenie2(czastka: Czastka, natezenie_poczatkowe: float, kat_rozproszenia: float, r: float,
              dlugosc_lambda: float):
    n=1.00045
    a=(1+cos(kat_rozproszenia)**2)/(2*(r**2))
    b= natezenie_poczatkowe*((2*math.pi/dlugosc_lambda)**4)
    c= ((n**2-1)/(n)**2+2)**2
    d= (czastka.d/2)**6
    return a*b*c*d

def zadanie2():
    while True:
        try:
            I0 = float(input("Podaj natężenie początkowe: "))
            if I0 >= 0:
                break
            else:
                print("Błąd! Musisz podać liczbę dodatnia.")
        except ValueError:
            print("Błąd! Musisz podać liczbę.")
    while True:
        czastka_input = input("podaj czasteczke azot, tlen")
        if czastka_input == "azot" or czastka_input == "tlen":
            czastka = pierwiastki[czastka_input]
            break
        else:
            print("wybierz tlen lub azot")
    while True:
        try:
            kat_rozproszenia = float(input("Podaj kąt: "))
            if kat_rozproszenia >= 0:
                break
            else:
                print("Błąd! Musisz podać dodatni kąt.")
        except ValueError:
            print("Błąd! Musisz podać liczbę.")
    while True:
        try:
            odleglosc = float(input("Podaj odległość: "))
            if odleglosc >= 0:
                break
            else:
                print("Błąd! Musisz podać liczbę dodatnia.")
        except ValueError:
            print("Błąd! Musisz podać liczbę.")
    results = []
    lambdas = []
    for i in range(400, 701):
        dl_lambda = i * (10 ** -9)
        lambdas.append(i)
        results.append(natezenie(czastka, I0, kat_rozproszenia, odleglosc, dl_lambda))

   print(results)
    fig, ax = plt.subplots(figsize=(9,5))
    ax.plot(lambdas, results, color="blue")
    ax.set_xlabel("długość fali [nm]")
    ax.set_ylabel("natężenie rozproszone I [W/m**2]")
    ax.set_title("Rozpraszanie Rayleigha")
    plt.show()
def zadanie3():
    I0 = 1
    pierwiastek=pierwiastki["azot"]
    kat_rozproszenia=0.8
    odleglosc=1
    while True:
        kolor1_input = input("podaj pierwszy kolor")
        if kolor1_input in kolory:
            kolor1 = kolory[kolor1_input]
            break
        else:
            print("Kultura, nie ma takiego koloru!")
    while True:
        kolor2_input = input("podaj drugi kolor")
        if kolor2_input in kolory:
            kolor2 = kolory[kolor2_input]
            break
        else:
            print("Kultura, nie ma takiego koloru!")

  I1 = natezenie(pierwiastek,I0,kat_rozproszenia,odleglosc,kolor1)
  I2 = natezenie(pierwiastek,I0,kat_rozproszenia,odleglosc,kolor2)
    print(I1, I2)
    if I1>=I2:
        print(f"Większa wartość dla {kolor1_input}")
    else:
        print(f"Większa wartość dla {kolor2_input}")
def zadanie4():
    I0= 1
    kat=1
    odleglosc=1
    dlambda= 7*10**-7
    while True:
        czastka_input = input("podaj czasteczke")
        if czastka_input in pierwiastki:
            czastka = pierwiastki[czastka_input]
            break
        else:
            print("wybierz dostępną cząsteczke")
    nat = natezenie2(czastka,I0,kat,odleglosc,dlambda)
    print(f"Natężenie {nat}")

if __name__ == '__main__':
    zadanie4()
    # zadanie3()
    # zadanie2()
