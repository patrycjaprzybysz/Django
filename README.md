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


#### 10. Wdrożenie aplikacji na PythonAnywhere

Aplikacje można znaleźć pod adresem:
https://patrycjaprzybysz.pythonanywhere.com/

#### 11. utworzenie pliku blog/view.py 

w pliku tym tworzymy widoki na naszej stronie

```
from django.shortcuts import render
from django.utils import timezone
from .models import Post
from django.shortcuts import render, get_object_or_404
from .forms import PostForm
from django.shortcuts import redirect

def post_list(request):
    posts = Post.objects.filter(published_date__lte=timezone.now()).order_by('published_date')
    return render(request, 'blog/post_list.html', {'posts': posts})

def post_detail(request, pk):
    post = get_object_or_404(Post, pk=pk)
    return render(request, 'blog/post_detail.html', {'post': post})


def post_new(request):
    if request.method == "POST":
        form = PostForm(request.POST)
        if form.is_valid():
            post = form.save(commit=False)
            post.author = request.user
            post.published_date = timezone.now()
            post.save()
            return redirect('post_detail', pk=post.pk)
    else:
        form = PostForm()
    return render(request, 'blog/post_edit.html', {'form': form})

def post_edit(request, pk):
    post = get_object_or_404(Post, pk=pk)
    if request.method == "POST":
        form = PostForm(request.POST, instance=post)
        if form.is_valid():
            post = form.save(commit=False)
            post.author = request.user
            post.published_date = timezone.now()
            post.save()
            return redirect('post_detail', pk=post.pk)
    else:
        form = PostForm(instance=post)
    return render(request, 'blog/post_edit.html', {'form': form})
```

#### 12. Utworzenie plików html 

* blog/templates/blog/post_detail.html

```
{% extends 'blog/base.html' %}

{% block content %}
    <div class="post">
        {% if post.published_date %}
            <div class="date">
                {{ post.published_date }}
            </div>
        {% endif %}
       {% if user.is_authenticated %}
     <a class="btn btn-default" href="{% url 'post_edit' pk=post.pk %}"><span class="glyphicon glyphicon-pencil"></span></a>
{% endif %}
        <h1>{{ post.title }}</h1>
        <p>{{ post.text|linebreaksbr }}</p>
    </div>
{% endblock %}
```

*blog/templates/blog/base.html

```
{% load static %}
<html>
    <head>
        <title>Django Girls blog</title>
        <link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
        <link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css">
        <link href='//fonts.googleapis.com/css?family=Lobster&subset=latin,latin-ext' rel='stylesheet' type='text/css'>
        <link rel="stylesheet" href="{% static 'css/blog.css' %}">
    </head>
    <body>
        <div class="page-header">
           {% if user.is_authenticated %}
    <a href="{% url 'post_new' %}" class="top-menu"><span class="glyphicon glyphicon-plus"></span></a>
{% endif %}
            <h1><a href="/">Django Girls Blog</a></h1>
        </div>
        <div class="content container">
            <div class="row">
                <div class="col-md-8">
                    {% block content %}
                    {% endblock %}
                </div>
            </div>
        </div>
    </body>
</html>
```

* blog/templates/blog/post_edit.html

```
{% extends 'blog/base.html' %}

{% block content %}
    <h2>New post</h2>
    <form method="POST" class="post-form">{% csrf_token %}
        {{ form.as_p }}
        <button type="submit" class="save btn btn-default">Save</button>
    </form>
{% endblock %}
```

* blog/templates/blog/post_list.html

```

{% extends 'blog/base.html' %}

{% block content %}
    {% for post in posts %}
        <div class="post">
            <div class="date">
                {{ post.published_date }}
            </div>
            <h1><a href="{% url 'post_detail' pk=post.pk %}">{{ post.title }}</a></h1>
            <p>{{ post.text|linebreaksbr }}</p>
        </div>
    {% endfor %}
{% endblock %}
```
