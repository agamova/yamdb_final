# Проект YaMDb
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). 
Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) 
может быть расширен администратором (например, можно добавить категорию «Изобразительное 
искусство» или «Ювелирка»).
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» 
могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — 
песня «Давеча» группы «Насекомые» и вторая сюита Баха.
Произведению может быть присвоен жанр (Genre) из списка предустановленных (например, «Сказка», 
«Рок» или «Артхаус»).Новые жанры может создавать только администратор.
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы (Review) 
и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских 
оценок формируется усреднённая оценка произведения — рейтинг (целое число). 
На одно произведение пользователь может оставить только один отзыв.


# Как запустить проект:
Клонировать репозиторий и перейти в него в командной строке:
git clone https://github.com/agamova/infra_sp2.git



В корне проекта создать файл .env:

`SECRET_KEY='YOUR_SECRET_KEY'`  
`ALLOWED_HOSTS='*'` 
`DB_ENGINE=django.db.backends.postgresql`
`DB_NAME=postgres`  
`POSTGRES_USER=postgres`  
`POSTGRES_PASSWORD=your_password`  
`DB_HOST=db`  
`DB_PORT=5432`


Выполнить:
`docker-compose up -d`



 Выполнить миграции, создать суперюзера и собрать статику:  

`docker-compose exec web python manage.py makemigrations`  
 `docker-compose exec web python manage.py migrate`  
 `docker-compose exec web python manage.py createsuperuser`  
 `docker-compose exec web python manage.py collectstatic`



Заполнить базу данными из csv файлов:
1 способ:  

`docker-compose exec web python manage.py loader_csv`

2 способ:  

`docker-compose exec web python manage.py loaddata fixtures.json`




Документация API YaMDb по адресу:
`http://127.0.0.1/redoc/`
