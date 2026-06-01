# Rozpraszanie Rayleigha

To jest program na zadanie z fizyki. Liczy natężenie rozproszonego światła przez gaz. Są trzy zadania w pliku main.py.

## Co trzeba mieć

Python i biblioteka matplotlib. Jak nie ma matplotlib to pip install matplotlib.

## Jak uruchomić

Na końcu pliku main.py jest if __name__ == '__main__'. Domyślnie odpala się zadanie4. Jak chcesz inne zadanie to zakomentuj zadanie4 i odkomentuj zadanie2 albo zadanie3.

## Wzór

W programie jest funkcja natezenie. Używa wzoru z wykładu na rozpraszanie Rayleigha. Potrzebne są I0 (natężenie na początku), kąt rozproszenia, odległość r, długość fali lambda, współczynnik załamania n cząsteczki i średnica d.

## Cząsteczki w programie

azot, tlen, metan, dwutlenek węgla. Każda ma wpisane n i d w słowniku pierwiastki.

## Kolory w zadaniu 3

Można wpisać: czerwony, fioletowy, niebieski, zielony, zolty (tak jest w kodzie bez polskich znaków).

## Zadanie 2

Program pyta o I0, azot albo tlen, kąt i odległość. Potem liczy dla fal od 400 do 700 nm i robi wykres. Wykres się pokazuje w oknie jak odpalisz program normalnie na komputerze.

## Zadanie 3

Są ustalone wartości I0=1, azot, kąt 0.8, odległość 1. Podaje się dwa kolory i program mówi który ma większe natężenie.

## Zadanie 4

I0=1, kąt 1, odległość 1, lambda jak czerwony (7e-7). Wybiera się cząsteczkę z listy i program wypisuje natężenie. Liczy przez funkcję natezenie2 gdzie n jest na sztywno 1.00045.

## Pliki

main.py - cały program
README - ten plik
