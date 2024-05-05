### 1. w pierwszym kroku utworzyłam nowy folder roboczy i aktywowałam wirtualne srodowisko

``` 
C:\Users\patip\django> python -m venv env.patrycja.przybysz
```

![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/615958dd-adc5-4624-8ee1-b26ce920346f)


```
C:\Users\patip\django> env.patrycja.przybysz\Scripts\activate
```

### 3. sprawdziłam czy mam najnowsza wersje pip aby zainstalowac django

```
python -m pip install --upgrade pip
```
### 4. w folderze django utworzylam requirements.txt i dodałam do niego taki tekst:

```
Django~=3.2.10
```
to pozwoliło po wykonaniu komendy pip install -r requirements.txt zainstalowac Django

### 5. nastpenie utworzyłam nowy projket 
![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/673a2063-216f-4412-8eac-b5ac87da4cff)

```
django-admin.exe startproject mysite .
```
i zmodyfikowałam ustawienia takie jak time_zone, language, allowed_host, static

### 6. utworzyłam bazę danych i uruchomiłam serwer
```
python manage.py migrate
```

```
python manage.py runserver
```
![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/ee108c87-023f-4dd1-a2d1-35c9165f6884)

### 7. Stworzyłam bloga

```
python manage.py startapp blog
```
![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/fdc8963c-3d11-4953-850e-f9b11390ecc5)

Po ustwieniach utworzyłam model wpisu (post) oraz tabele dla modeli w bazie danych

### 8. w pliku blog/admin.py dodałam model post z poprzedniego kroku i utworzyłam admina wprowadzajac login mail i haslo
![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/63db2355-597f-4e43-81a0-75bd57676e25)

![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/f9aa0a53-43b5-4ee9-b80b-a0d9779398a5)


#### dodałam posty na bloga
![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/07811e00-9902-42be-9fe8-f666446e82ff)


### 9. Wdrożyłam aplikacje na pythonanyware 
https://patrycjaprzybysz.pythonanywhere.com/

   
