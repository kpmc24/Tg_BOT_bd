# Tg_BOT_bd
```markdown
# Project Manager Bot

Telegram-бот для управления проектами с хранением данных в SQLite.

## Файлы

- `main.py` — Telegram-бот (логика взаимодействия с пользователем)
- `logic.py` — класс `DB_Manager` для работы с базой данных SQLite
- `config.py` — конфигурация (`TOKEN`, `DATABASE`)

## Требования

- Python 3
- `pytelegrambotapi` (`telebot`)
- `sqlite3` (стандартная библиотека)

## Настройка

В `config.py` должны быть определены:
- `TOKEN` — токен Telegram-бота
- `DATABASE` — путь к файлу базы данных SQLite

## Инициализация базы данных

Перед запуском бота выполнить `logic.py`:

```
python logic.py
```

Создаются таблицы: `projects`, `skills`, `project_skills`, `status`, и заполняются значения по умолчанию.

Навыки: `Python`, `SQL`, `API`, `Telegram`.

Статусы:
- На этапе проектирования
- В процессе разработки
- Разработан. Готов к использованию.
- Обновлен
- Завершен. Не поддерживается

## Запуск

```
python main.py
```

## Команды бота

- `/start` — приветствие и список команд
- `/info` — список доступных команд
- `/new_project` — добавить проект (название → ссылка → статус)
- `/skills` — добавить навык проекту
- `/projects` — список проектов с inline-кнопками для просмотра информации
- `/update_projects` — изменить проект (имя, описание, ссылка, статус)
- `/delete` — удалить проект

Также при вводе имени существующего проекта бот выводит информацию о нём.

## Отмена

На шагах выбора из клавиатуры доступна кнопка `Отмена 🚫`.

## Вывод информации о проекте

```
Project name: ...
Description: ...
Link: ...
Status: ...
Skills: ...
```

Если навыки не добавлены — `Навыки пока не добавлены`.

## Методы `DB_Manager`

- `create_tables()` — создание таблиц
- `default_insert()` — вставка навыков и статусов по умолчанию
- `insert_project(data)` — добавить проект
- `insert_skill(user_id, project_name, skill)` — привязать навык к проекту
- `get_statuses()` — список статусов
- `get_status_id(status_name)` — ID статуса
- `get_projects(user_id)` — проекты пользователя
- `get_project_id(project_name, user_id)` — ID проекта
- `get_skills()` — список навыков
- `get_project_skills(project_name)` — навыки проекта (строка через запятую)
- `get_project_info(user_id, project_name)` — имя, описание, ссылка, статус
- `update_projects(param, data)` — обновить поле проекта
- `delete_project(user_id, project_id)` — удалить проект
- `delete_skill(project_id, skill_id)` — удалить навык
```
