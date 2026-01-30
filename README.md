# Flask log - testing web app using flask and py

Flask project which uses HTML views.

## Functionality

### Authentification 
- Reistration
- Login/logout
- Routing security (login_required)
- Pwd hashing

### CRUD
- **Create** - New posts
- **Read** - Rad all or separate posts
- **Update** - Edit/update
- **Delete** - Delete

### Additional functionality
- User profiles
- User - post relationship
- Flash-messages for users
- Responsive design (Bootstrap 5)
- Form validation

## Project struture

```
/
│
├── app.py                 # Головний файл додатку
├── requirements.txt       # Залежності проекту
├── blog.db               # База даних SQLite (створюється автоматично)
│
└── templates/            # HTML шаблони
    ├── base.html         # Базовий шаблон
    ├── index.html        # Головна сторінка
    ├── register.html     # Реєстрація
    ├── login.html        # Вхід
    ├── new_post.html     # Створення поста
    ├── view_post.html    # Перегляд поста
    ├── edit_post.html    # Редагування поста
    └── profile.html      # Профіль користувача
```

## How to run

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Run app

```bash
python app.py
```

### 3. Open web browser

Open http://127.0.0.1:5000/

Deployed version into renderer: https://flaskportalpy.onrender.com/

## Tech stack

- **Flask** - web framework
- **Flask-SQLAlchemy** - ORM
- **SQLite** - BD
- **Werkzeug** - pwd hashing
- **Bootstrap 5** - CSS framework
- **Jinja2** - templates (build in into Flask)

## Main Flask conceptions

### 1. Routing
```python
@app.route('/')
def index():
    return render_template('index.html')
```

### 2. HTTP Methods
```python
@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        # Form handling
```

### 3. DB models
```python
class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(80), unique=True)
```

### 4. Sessions
```python
session['user_id'] = user.id
if 'user_id' in session:
    # User logged in
```

### 5. Decorators
```python
@login_required
def protected_route():
    # Only when logged in
```

### 6. Flash messages
```python
flash('Successful action!', 'success')
```

### 7. Templates and inheritance
```python
{% extends "base.html" %}
{% block content %}
    <!-- Content -->
{% endblock %}
```

## Possible improvements

- Додати пагінацію для постів
- Реалізувати коментарі до постів
- Додати можливість лайкати пости
- Реалізувати пошук постів
- Додати категорії/теги
- Завантаження зображень
- Email верифікація
- Відновлення паролю
- REST API
- Тести

## Security

⚠️ **ВАЖЛИВО**: Цей проект створений для навчання. Для production використання потрібно:

1. Змінити SECRET_KEY на надійний випадковий ключ
2. Використовувати PostgreSQL або MySQL замість SQLite
3. Додати HTTPS
4. Реалізувати rate limiting
5. Додати CSRF захист (Flask-WTF)
6. Валідацію на стороні сервера
7. Escaped output у шаблонах (Jinja2 робить це автоматично)

## Ліцензія

Навчальний проект - використовуйте вільно!
