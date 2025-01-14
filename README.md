# Информационная система контроля и слежения за автомобилем

Информационная система контроля и слежения за автомобилем позволяет получать данные с датчиков автомобиля, контролирвоать автомобиль, генерирвоать аналитику по состоягию автомобиля

## 1. Структура функциональных возможностей (Mind Map)

```mermaid
mindmap
  root(ИC контроля и слежения за автомобилем)
    Пользователи
      Клиенты
        Регистрация
        Авторизация
        Слежение за автомобилем
        Контроль автомобиля
        Просмотр аналитики
      Администраторы
        Модерация системы
    Слежение за автомобилем
      Просмотр данных автомобиля
      Просмотр карты с местоположением автомобиля
      Просмотр истории перемещения автомобиля
    Контроль автомобиля
      Ввод команды управления
      Выполнение команды автомобилем
      Просмотр результатов выполнения команды
    Аналитика
      Обработка данных
      Генерация отчета
      Генерация уведомлений
    Авторизация и аутентификация
      Создание аккаунта
      Вход в аккаунт
    Архитектура
      Клиент-серверная
      Микросервисы
    Используемые технологии
      Spring
      Java
      React Native
      HTML, CSS, JS
      PostgeSQL
      Redis
    Задачи проектирования
      Дизайн системы
      Моделирование данных
      Проектирование API
      Оценка производительности
```

## 2. Диаграмма путешествия пользователя (User Journey Diagram)

```mermaid
journey
  title Общий путь пользователя при взаимодействии с ИС
  section Вход в аккаунт
    Пользователь открывает приложение: 5: Пользователь
    Пользователь выполняет авторизацию: 4: Пользователь
  section Слежение за автомобилем
    Пользователь выбирает датчики для слежения: 5: Пользователь
    Клиент отправляет запрос на сервер: 5: Клиент
    Сервер получает данные сенсоров от автомобиля: 4: Сервер
    Клиент отображает данные на странице: 4: Клиент
    Пользователь ознакамливается с данными автомобиля: 5: Пользователь
  section Контроль за автомобилем
    Пользователь вводит команду управления автомобилем: 5: Пользователь
    Сервер контролирует выполнение команды автомобилем: 4: Сервер
    Клиент отображает данные на странице: 4: Клиент
    Пользователь ознакамливается с результатами выполнения команды: 5: Пользователь
  section Просмотр аналитики
    Пользователь заходит в раздел аналитики: 5: Пользователь
    Клиент отправляет запрос на сервер: 5: Клиент
    Сервер генерирует данные по аналитике: 4: Сервер
    Клиент рисует графики и отображает раздел: 5: Клиент
    Пользователь ознакамливается с аналитикой по визитке: 7: Пользователь
```

## 3. Квадрант-граф (Quadrant Chart)

```mermaid
quadrantChart
    title Приоритеты разработки функционала
    x-axis "Низкий приоритет" --> "Высокий приоритет"
    y-axis "Низкая сложность" --> "Высокая сложность"
    quadrant-1 "Реализовать немедленно"
    quadrant-2 "Планировать в ближайшее время"
    quadrant-3 "Возможно, стоит отказаться"
    quadrant-4 "Требует тщательного анализа"
    
    "Генерация отчетов": [0.7, 0.7]
    "Дизайн пользовательского интерфейса": [0.55, 0.8]
    "Завершение разработки API сервисов": [0.8, 0.9]

    "Обратная связь": [0.2, 0.6]
    "Сохранение истории команд автомобиля": [0.3, 0.9]
    "Оптимизация запросов к базе данных": [0.2, 0.7]

    "Рассылка email-уведомлений": [0.2, 0.2]
    "Добавление избранных команд управления": [0.3, 0.3]

    "Авторизация": [0.6, 0.2]
    "Интеграция с ИИ": [0.8, 0.4]
```

## 4. Git-граф

```mermaid
gitGraph
  commit id: "Инициализация репозитория"
  branch client
  checkout client
  commit id: "Создан клиентский модуль"
  commit id: "Реализован интерфейс для регистрации пользователей"
  commit id: "Добавлен экран для отслеживания автомобиля"
  checkout main
  merge client
  branch server
  checkout server
  commit id: "Создан серверный модуль"
  commit id: "Реализована база данных для хранения данных автомобилей"
  commit id: "Реализован API для получения данных о местоположении"
  commit id: "Реализована интеграция с картографическим сервисом"
  branch server-auth
  checkout server-auth
  commit id: "Реализована авторизация и аутентификация"
  checkout server
  merge server-auth
  checkout main
  merge server
  branch integration
  checkout integration
  commit id: "Интеграция клиента и сервера через API"
  commit id: "Тестирование системы"
  branch monitoring
  checkout monitoring
  commit id: "Добавлены модули для контроля состояния автомобиля"
  checkout integration
  merge monitoring
  commit id: "Добавлен раздел уведомлений о состоянии автомобиля"
  checkout integration
  commit id: "Оптимизация запросов к базе данных"
  checkout integration
  commit id: "Финальная сборка"
  checkout main
  merge integration
```