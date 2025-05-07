---

# 💸 Flask-Banking App

Веб-приложение с поддержкой:

* регистрации и логина с 2FA (через SMS),
* распознавания лица при регистрации и переводе средств,
* Stripe-оплат и переводов между пользователями,
* управления счетом, депозитами и транзакциями,
* админ-функций.

---

## 📦 Зависимости

### Установка

Создайте виртуальное окружение и установите зависимости:

```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

Создайте файл `requirements.txt` и добавьте:

```txt
Flask
Flask_SQLAlchemy
stripe
bcrypt
Pillow
face_recognition
numpy
twilio
```

---

### Описание библиотек

| Библиотека        | Назначение                                               |
| ----------------- | -------------------------------------------------------- |
| Flask             | Веб-фреймворк для создания маршрутов, шаблонов, форм.    |
| Flask\_SQLAlchemy | ORM для работы с базой данных (в данном случае SQLite).  |
| stripe            | Интеграция с Stripe API (оплаты, переводы, аккаунты).    |
| bcrypt            | Хеширование паролей пользователей.                       |
| Pillow (PIL)      | Работа с изображениями (преобразование входного кадра).  |
| face\_recognition | Распознавание лиц на изображениях (на основе dlib).      |
| numpy             | Обработка изображений в массивы (для face\_recognition). |
| twilio            | Отправка SMS для двухфакторной аутентификации.           |
| Visual studio           | Обязательно нужно скачать вижуал студио инструменты с++ для работы библиотеки face_recognition      |
---

## 🛠️ Конфигурация

Создайте файл `.env` (рекомендуется) или укажите переменные в `app.config`:

```python
app.config['SECRET_KEY'] = 'your-secret-key'
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///path/to/bank.db'
app.config['UPLOAD_FOLDER'] = 'static/uploads'
app.config['ALLOWED_EXTENSIONS'] = {'png', 'jpg', 'jpeg'}
```

Настройте ключи:

* Stripe API (test keys):

  * `stripe.api_key = 'sk_test_...'`
  * `PUBLISHABLE_KEY = 'pk_test_...'`

* Twilio:

  * `TWILIO_ACCOUNT_SID`, `TWILIO_AUTH_TOKEN`, `TWILIO_PHONE_NUMBER`

---

## 🚀 Запуск

```bash
pip install requirements.txt
python main.py
```

Откройте [http://127.0.0.1:5000](http://127.0.0.1:5000)

---

## 🔐 Функциональность

### Регистрация

* Уникальные: логин, email, телефон.
* Распознавание лица (сохранение изображения).
* 2FA через SMS (Twilio).

### Вход

* Пароль + 2FA по SMS.

### Переводы

* Только при подтверждении лица.
* Используется Stripe PaymentIntent и Transfer API.

### Профиль

* Баланс, депозиты, история транзакций.

---

## 📂 Структура

* `main.py` — основной код.
* `templates/` — HTML-шаблоны (Jinja2).
* `static/uploads/` — изображения пользователей.
* `bank.db` — база данных SQLite.

---

## ❗Важно
* Убедитесь, что у вас установлены зависимости `dlib`, `cmake`, `face_recognition` — они могут требовать дополнительных пакетов (особенно на Windows).
---

