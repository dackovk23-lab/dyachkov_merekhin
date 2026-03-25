# CONTRACT.md — Storage Module

## Назначение
Абстракция над файловым хранилищем. Предоставляет методы CRUD для объектов Task.

## Интерфейс

### `save(task)`
Сохраняет задачу в хранилище.
- **Параметры:** `task` (object) — объект задачи с полями `id`, `title`, `status`.
- **Возвращает:** `boolean` — успех операции.
- **Исключения:** `StorageError` при ошибке записи в файл.

### `getById(id)`
Возвращает задачу по идентификатору.
- **Параметры:** `id` (string) — уникальный идентификатор.
- **Возвращает:** `object | null` — объект задачи или null.

### `list()`
Возвращает список всех задач.
- **Параметры:** нет
- **Возвращает:** `array` — массив объектов Task.

### `delete(id)`
Удаляет задачу.
- **Параметры:** `id` (string)
- **Возвращает:** `boolean`

## Пример использования
```javascript
const storage = require('storage');
storage.save({ id: "1", title: "Buy milk", status: "pending" });
const task = storage.getById("1");
console.log(task.title); // Buy milk