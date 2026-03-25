
---

### 2. Модуль бизнес-логики (Logic)
**Назначение:** Реализует правила обработки задач (валидация, изменение статусов, фильтрация).

```markdown
# CONTRACT.md — Logic Module

## Назначение
Содержит бизнес-правила. Взаимодействует с модулем Storage через предоставленный API.

## Интерфейс

### `createTask(title)`
Создает новую задачу с валидацией.
- **Параметры:** `title` (string) — не менее 3 символов.
- **Возвращает:** `object` — созданную задачу с полями `id`, `title`, `status: 'pending'`.
- **Исключения:** `ValidationError` если заголовок пустой или короткий.

### `completeTask(id)`
Переводит задачу в статус `done`.
- **Параметры:** `id` (string)
- **Возвращает:** `object` — обновленную задачу.
- **Исключения:** `NotFoundError` если задача отсутствует.

### `getPendingTasks()`
Возвращает список незавершенных задач.
- **Параметры:** нет
- **Возвращает:** `array` — отфильтрованный список задач.

## Пример использования
```python
from logic import TaskLogic
logic = TaskLogic(storage_client)
task = logic.create_task("Write report")
logic.complete_task(task.id)
pending = logic.get_pending_tasks() # []