Система управления дорожным движением
Веб-приложение для мониторинга и управления дорожным движением с функциями отчетности о происшествиях в реальном времени.

📋 Оглавление
Функциональность
Технологический стек
Требования к системе
Установка и настройка
Структура проекта
API документация
Разработка
🚀 Функциональность
Мониторинг дорожного движения в реальном времени
Система отчетности о происшествиях
Интерактивная карта с использованием Яндекс.Карт
Аутентификация пользователей
Отслеживание статуса происшествий
Адаптивный дизайн для всех устройств
💻 Технологический стек
Бэкенд
Django 4.2+
PostgreSQL
Django REST Framework
Python 3.11+
Фронтенд
React 18
Vite
Tailwind CSS
Material UI (@mui/material)
Яндекс Карты (@pbe/react-yandex-maps)
🛠 Требования к системе
Python 3.11 или выше
Node.js 16+ и npm
PostgreSQL 12+
Git
📥 Установка и настройка
1. Клонирование репозитория
git clone [url-репозитория]
cd traffic_flow_assistant
2. Настройка базы данных PostgreSQL
# Создание базы данных
psql -U postgres
CREATE DATABASE traffic_flow_db;
CREATE USER traffic_flow_user WITH PASSWORD 'ваш_пароль';
GRANT ALL PRIVILEGES ON DATABASE traffic_flow_db TO traffic_flow_user;
\q
3. Настройка бэкенда
# Создание и активация виртуального окружения
python -m venv venv
source venv/bin/activate  # Для Windows: venv\Scripts\activate
# Установка зависимостей
cd traffic_flow_app
pip install -r requirements.txt
# Создание .env файла
echo "DEBUG=True
SECRET_KEY=ваш_секретный_ключ
DATABASE_URL=postgresql://traffic_flow_user:ваш_пароль@localhost:5432/traffic_flow_db" > .env
# Применение миграций
python manage.py migrate
# Создание суперпользователя
python manage.py createsuperuser
# Запуск сервера разработки
python manage.py runserver
4. Настройка фронтенда
# Переход в директорию фронтенда
cd traffic_flow_frontend
# Установка зависимостей
npm install
# Создание .env файла
echo "VITE_API_URL=http://localhost:8000/api
VITE_YANDEX_MAPS_API_KEY=ваш_ключ_яндекс_карт" > .env
# Запуск сервера разработки
npm run dev
📁 Структура проекта
traffic_flow_assistant/
├── traffic_flow_app/          # Бэкенд приложение
│   ├── manage.py
│   ├── requirements.txt
│   └── traffic_flow_app/
│       ├── settings.py
│       ├── urls.py
│       └── wsgi.py
└── traffic_flow_frontend/     # Фронтенд приложение
    ├── src/
    │   ├── Components/
    │   ├── Services/
    │   ├── pages/
    │   └── App.jsx
    ├── package.json
    └── vite.config.js
📡 API документация
Основные эндпоинты
Происшествия
GET /api/incidents/ - Получение списка происшествий
POST /api/incidents/ - Создание нового происшествия
GET /api/incidents/{id}/ - Получение информации о конкретном происшествии
Локации
GET /api/report-location/ - Получение списка локаций
POST /api/report-location/ - Добавление новой локации
💡 Разработка
Запуск тестов
# Бэкенд тесты
python manage.py test
# Фронтенд тесты
npm run test
Линтинг
# Бэкенд
flake8 .
# Фронтенд
npm run lint
Сборка для продакшена
# Бэкенд
python manage.py collectstatic
# Фронтенд
npm run build
🔧 Решение проблем
Частые проблемы и их решения
Ошибка подключения к базе данных

Проверьте правильность учетных данных в .env
Убедитесь, что PostgreSQL запущен
Проблемы с npm

Попробуйте удалить node_modules и package-lock.json
Выполните npm cache clean --force
Повторите npm install
Ошибки CORS

Проверьте настройки CORS в settings.py
Убедитесь, что URL фронтенда добавлен в CORS_ALLOWED_ORIGINS
📱 Использование приложения
Откройте браузер и перейдите по адресу http://localhost:5173
Войдите в систему, используя свои учетные данные
На главной странице вы увидите карту с отмеченными происшествиями
Для добавления нового происшествия используйте соответствующую форму
Для просмотра детальной информации кликните на маркер на карте
🔐 Безопасность
Регулярно обновляйте зависимости
Используйте надежные пароли
Держите SECRET_KEY в безопасности
Не коммитьте .env файлы в репозиторий
