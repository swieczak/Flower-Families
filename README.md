# Flower-Families

 ![sansewieria gwinejska](https://github.com/swieczak/Flower-Families/blob/main/sansewieria.PNG)

**Opis programu**

Program Flower Families ma za zadanie rozpoznać do jakiej rodziny należy zadana roślina.
Użytkownik podaje narzucone z góry parametry rośliny, a program wyświetla, do jakiej rodziny
taksonomicznej prawdopodobnie należy sprawdzany osobnik.
Program korzysta z autorskiej bazy danych różnych osobników poszczególnych gatunków roślin
należących do sześciu różnych rodzin w taksonomii.

**Instrukcja obsługi**

Program jest w postaci skryptu .py, który należy uruchomić w dowolnym edytorze języka
Python. Przykładowe wartości dla szukanej rośliny należy wpisywać bezpośrednio w kodzie
skryptu, przed jego uruchomieniem.

**Wymagania i zabezpieczenia**

Wymagana jest wersja jezyka Python co najmniej 3.0 oraz możliwość uruchomienia dowolnego
edytora skryptu Python.
Warunkiem prawidłowego działania skryptu jest załadowanie pliku FlowerFamily.csv, który
zawiera bazę osobników roślin. W przypadku nieznalezienia pliku skrypt nie wykona dalszych
operacji.
Należy wprowadzać do skryptu poprawne do przetworzenia i wiarygodne dane, czyli liczby
zmiennoprzecinkowe nieujemne. W przypadku parametru *stalkquantity* oraz *leafdensity* liczby
powinny być wyłącznie naturalne.

**Opis działania zbioru miękkiego**

Klasyfikator zbioru miękkiego polega na stworzeniu zbioru, w którym określona klasa rózniących
się między sobą obiektów posiada dane na ich temat zapisane w systemie binarnym.
Dla numerycznej bazy zawierającej informacje na temat konkretnych parametrów mierzonych
roślin brane pod uwagę będą wyliczone średnie wartości dla poszczególnych rodzin. W następnym
kroku porównuje się otrzymane szczególne średnie do średnich ogólnych całego zbioru
danych. Algorytm decyduje o przypisaniu danej klasie produktu wartość 1 dla danego parametru,
gdy jego średnia wartość przewyższa średnia ogólna parametru. W przypadku niższej
średniej niż dla ogólnego zbioru, przypisywana jest wartość 0.

**Opis działania naiwnego klasyfikatora Bayesa**

Naiwny klasyfikator Bayesa jest prostym klasyfikatorem probabilistycznym. Oparty jest o
prawdopodobieństwo warunkowe, bazuje na twierdzeniu Bayesa. Algorytm Bayesa przetwarza pozostałe parametry, bez owłosienia i postrzępienia liści. Bierze
pod uwagę tylko te rodziny, które nie zostały wyeliminowane przez algorytm zbioru miękkiego.

**Przykład obliczeniowy**

 ![](https://github.com/swieczak/Flower-Families/blob/main/tab1.PNG)
 
 Powyżej widzimy próbkę pobraną z przygotowanej bazy danych. Wyświetlamy jedynie kolumny
*fraying* oraz *hairness*, ponieważ tylko one będą nam potrzebne podczas omawiania
części opartej na algorytmie zbiorów miękkich.
Na samym początku uśredniamy wszystkie informacje dotyczące postrzępienia i ulistnienia danej grupy roślin. Następnie wyliczamy w każdym rzędzie sumę ważoną.
 
 ![](https://github.com/swieczak/Flower-Families/blob/main/tab2.PNG)
 
 W ten sposób zauważamy, że poszukiwanym typem rośliny moga byc *Aracea* oraz *Violaceae*
(ponieważ posiadają one najwyższą wartość S sposród wszystkich) i taką informację
przesyłamy do dalszej części programu.
 
 ![](https://github.com/swieczak/Flower-Families/blob/main/tab3.PNG)
 
Przed przystąpieniem do klasyfikacji przygotowujemy zbiór danych opierający się na całej bazie,
jednak zawierający wyłącznie próbki o typie zwróconym przez SoftSet.
Na wstępie wyliczamy średnią oraz odchylenie standardowe każdego atrybutu dla każdego
typu.
 
 ![](https://github.com/swieczak/Flower-Families/blob/main/tab4.PNG)
 
 W kolejnym kroku dla każdego typu w zbiorze danych wyliczana jest wartość funkcji Gaussa. Algorytm zwraca typ o najwyższym wyniku końcowym.
W tym przypadku przewidzianą klasą jest *Aracea*.
