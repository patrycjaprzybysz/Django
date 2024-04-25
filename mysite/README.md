1. w pierwszym kroku utworzyłam nowy folder roboczy i aktywowałam wirtualne srodowisko

``` 
C:\Users\patip\django> python -m venv env.patrycja.przybysz
```

2. nastepnie je aktywowalam

```
C:\Users\patip\django> env.patrycja.przybysz\Scripts\activate
```

3. sprawdziłam czy mam najnowsza wersje pip aby zainstalowac django

```
python -m pip install --upgrade pip
```
4. w folderze django utworzylam requirements.txt i dodałam do niego taki tekst:

```
Django~=3.2.10
```
to pozwoliło po wykonaniu komendy pip install -r requirements.txt zainstalowac Django

5. nastpenie tworze nowy projket 

```
django-admin.exe startproject mysite .
```
i modyfikuje ustawienia

6. po utworzeniu bazy danych uruchamia sie server 

```
python manage.py runserver
```
7. koljeno tworze bloga 

```
python manage.py startapp blog
```
odpowiednio wszytsko ustawiam i tworze model wpisu (post) oraz tabele dla modeli w bazie danych

8. w pliku blog/admin.py dodaje model post z poprzedniego kroku i tworze admina wprowadzajac login mail i haslo


na koniec dodaje posty na bloga

9. koljenym krokiem jest wdrozenie aplikacji. wysyłam ja na githuba i łącze z pythonanywhere.
 moj login na pythonanyware to patrycjaPrzybysz