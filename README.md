### Диаграмма структуры функциональных возможностей
Диаграмма описывает возможное применение проектируемого приложения: клиент-серверной системы для заказа такси.
Основными пользователями приложения являются: пассажиры (клиенты сервиса), водители и менеджеры, собирающие статистику.
```mermaid
mindmap
    (Клиент-серверное приложение заказа такси)
        [Заказ такси]
            Выбор опций
                {{С детским креслом}}
            Выбор тарифа
                {{Эконом}}
                {{Комфорт}}
                {{Престиж}}
            Выбор точки назначения
            Дополнительные настройки
        [Построение маршрута]
            К пассажиру
            К месту назначения
            Поиск ближайшей машины
        [Поиск пассажира]
            Поиск пассажира в соответствии с опциями
        [Анализ статистики]
            Статистика поездок
            Статистика использования приложения
            Анализ отзывов клиентов
```

### Диаграмма пути пользователя в системе
Диаграмма описывает взаимодействие пользователей с системой во время оформления и выполнения заказа.
Пользоваьель - Человек, заказывающий такси через приложение.
Водитель - осуществляющий заказ водитель.
```mermaid
journey
    title Путь пользователя в клиент-серверной системе
    section Авторизация в системе
        Указать номер телефона: 5 : Пользователь
        Получить код по sms: 3 : Пользователь
        Войти в систему: 7 : Пользователь
    section Заказ такси
        Выбрать тариф: 5 : Пользователь
        Выбрать опции: 5 : Пользователь
        Выбрать место назначения: 5 : Пользователь
        Ожидать такси : 4 : Пользователь
    section Обработка заказа
        Получить заказ: 4 : Водитель
        Получить маршрут: 5 : Водитель
        Подъехать к месту назначения: 5 : Водитель
        Забрать пассажира: 5 : Водитель
        Доставить пассажира к месту назначения: 5 : Водитель
    section Завершение заказа
        Оплатить заказ: 3 : Пользователь
        Оставить отзыв о водителе: 5 : Пользователь
```
### Квадрант-граф
Диаграмма описывает, какие задачи нужно выполнить в рамках реализации MVP приложения, а также их приоритет. Все задачи распределены по диаграмме в зависимости от их приоритета и сложности.
Hello world!
```mermaid
quadrantChart
    title Приоритет разработки функционала
    x-axis "Низкий приоритет" --> "Высокий приоритет"
    y-axis "Низкая сложность" --> "Высокая сложность"
    quadrant-1 "Реализация обязательна"
    quadrant-2 "Нужно отбросить"
    quadrant-3 "Можно реализовать"
    quadrant-4 "Требуется тщательный анализ"
    "Создание авторизации": [0.85, 0.7]
    "Разработка сервиса уведомлений": [0.48, 0.9]
    "Разработка web-интерфейса": [0.55, 0.8]
    "Разработка мобильного приложения": [0.75, 0.75]
    "Создание отчетов": [0.3, 0.3]
    "Email-уведомления об акциях": [0.4, 0.2]
    "Система отзывов": [0.7, 0.3]
    "Отслеживание машин в реальном времени": [0.7, 0.86]
    "Разработка сервиса заказов": [0.845, 0.43]
    "ИИ чат поддержки": [0.2, 0.8]
    "Прямая трансляция из автомобиля": [0.2, 0.85]
```
### Граф коммитов
На диаграмме приведен возможный граф коммитов во время разработки сервиса.
Мажорные релизы помечены квадратом.
```mermaid
gitGraph
    commit id: "Init commit"
    branch develop
    checkout develop
    commit id: "Add endpoints"
    commit id: "Add services" 
    commit id: "Add db connection"
    commit id: "Add business logic for order creation"
    commit id: "Add business logic for order patching"
    commit id: "Setup config"
    commit id: "Fixes"
    checkout main
    merge develop tag: "v_1.0.0"
    checkout develop
    commit id: "Add pay service integration"
    commit id: "Add dockerfile"
    commit id: "Update config for gitlab ci/cd"
    checkout main
    merge develop tag: "v_1.1.0" type: HIGHLIGHT
    checkout develop
    branch feature/add_support_for_http2
    checkout feature/add_support_for_http2
    commit id: "Add support for http2"
    commit id: "Fix config"
    checkout develop
    merge feature/add_support_for_http2
    checkout main
    merge develop tag: "v_1.1.1"
```