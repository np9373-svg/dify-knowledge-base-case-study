# Импорт и запуск

## 1. Импорт Chatflow

1. Откройте Dify Studio.
2. Импортируйте [`app.yml`](app.yml) как DSL-файл.
3. Если используемая в экспорте chat-модель недоступна в вашем workspace, выберите доступную модель в LLM node.

## 2. Создание Knowledge Base

1. Создайте новую Knowledge Base.
2. Выберите Parent-Child как Chunk Structure.
3. Загрузите 15 Markdown-файлов из [`../knowledge-base/parents`](../knowledge-base/parents).
4. Используйте `@@CHILD@@` как разделитель дочерних чанков.
5. Выберите `text-embedding-3-small` или заранее проверенную совместимую embedding-модель.

## 3. Retrieval settings

- Vector Search;
- `Top K = 3`;
- Rerank Model: disabled;
- Score Threshold: disabled;
- Full-Text Search: disabled.

Скриншот фактической конфигурации: [`../assets/knowledge-settings.png`](../assets/knowledge-settings.png).

## 4. Подключение базы

После импорта экспортированный `dataset_id` не будет ссылаться на базу в другом workspace.

1. Откройте Knowledge Retrieval node.
2. Удалите недоступную ссылку на исходную базу, если Dify её показывает.
3. Подключите созданную Knowledge Base.
4. Убедитесь, что query берётся из `sys.query`.
5. Убедитесь, что в LLM node включён context из Knowledge Retrieval.

## 5. Проверка

1. Откройте Retrieval Testing и проверьте несколько вопросов без модели.
2. Запустите Chatflow Preview.
3. Пройдите короткий набор из [`../evaluation/test-cases.md`](../evaluation/test-cases.md).
4. Проверьте как сам ответ, так и отображение Citations.

## 6. Публикация

После проверки опубликуйте приложение. Текущая публичная версия проекта: [udify.app/chat/f6PaUk9HZesp0r7O](https://udify.app/chat/f6PaUk9HZesp0r7O).
