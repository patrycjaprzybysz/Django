## Instrukcja instalacji i uruchomienia Django Blog w oparciu o tutorial https://tutorial.djangogirls.org/pl/

#### 1. Tworzenie nowego środowiska wirtualnego

``` 
C:\Users\patip\django> python -m venv env.patrycja.przybysz
```

![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/615958dd-adc5-4624-8ee1-b26ce920346f)

#### 2. aktywacja środowiska
```
C:\Users\patip\django> env.patrycja.przybysz\Scripts\activate
```

#### 3. Aktualizacja pip

```
python -m pip install --upgrade pip
```
#### 4. Instalacja wymaganych bibliotek

Utwórz plik requirements.txt w folderze Django i dodaj do niego następującą zawartość:
```
Django~=3.2.10
```
Następnie wykonaj polecenie:
```
 pip install -r requirements.txt zainstalowac Django
```

#### 5. Tworzenie nowego projektu Django 
![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/673a2063-216f-4412-8eac-b5ac87da4cff)

```
django-admin.exe startproject mysite .
```
Następnie dostosuj ustawienia projektu, takie jak strefa czasowa, język, dozwolone hosty i ustawienia statyczne.

#### 6. Migracja bazy danych i uruchomienie serwera
```
python manage.py migrate
```

```
python manage.py runserver
```
![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/ee108c87-023f-4dd1-a2d1-35c9165f6884)

#### 7. Tworzenie aplikacji bloga

```
python manage.py startapp blog
```
![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/fdc8963c-3d11-4953-850e-f9b11390ecc5)

Po ustwieniach utworzyłam model wpisu (post) oraz tabele dla modeli w bazie danych

#### 8. Dodawanie modelu do panelu administracyjnego

Edytuj plik blog/admin.py, aby dodać model post. Następnie utwórz konto administratora, podając adres e-mail i hasło.

![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/63db2355-597f-4e43-81a0-75bd57676e25)

![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/f9aa0a53-43b5-4ee9-b80b-a0d9779398a5)


#### 9. Dodawanie wpisów na bloga
![image](https://github.com/patrycjaprzybysz/ISI/assets/100605325/07811e00-9902-42be-9fe8-f666446e82ff)


#### 10.Wdrożenie aplikacji na PythonAnywhere

Wdrożenie aplikacji na PythonAnywhere
https://patrycjaprzybysz.pythonanywhere.com/

   
