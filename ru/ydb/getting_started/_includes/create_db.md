---
sourcePath: ru/ydb/overlay/getting_started/_includes/create_db.md
---
# Создание базы данных - Начало работы

{% include [create_db_overlay.md](create_db_overlay.md) %}

## Самостоятельное развертывание {#self-hosted}

YDB может быть развернута самостоятельно двумя способами:

- [С использованием Docker](../self_hosted/ydb_docker.md)
- [В Kubernetes](../../deploy/orchestrated/concepts.md)

По умолчанию в результате выполнения этих сценариев вы получите базу данных со следующими параметрами соединения:

- Эндпоинт: `grpc://localhost:2136`
- Имя базы данных: `/local`
- Аутентификация: не требуется

Подробная информация о базах данных находится в статье [Термины и определения - База данных](../../concepts/databases.md#database) в разделе "Концепции".