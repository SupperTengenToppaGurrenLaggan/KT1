# Ktor-server

API предоставляет следующие endpoints:

GET /items - Получить все элементы

GET /items/{id} - Получить элемент по ID

POST /items - Создать новый элемент

DELETE /items/{id} - Удалить элемент по ID

 Технологии
Kotlin - Язык программирования

Ktor - Фреймворк для построения асинхронных серверов

Netty - Серверный движок

Kotlinx Serialization - Сериализация JSON

🛠 Установка и запуск
Требования
JDK 11 или выше

Kotlin 1.6+

Сборка и запуск
Клонируйте репозиторий

Соберите проект:

bash
./gradlew build
Запустите сервер:

bash
./gradlew run
Или запустите напрямую через main функцию в IDE.

Сервер будет доступен по адресу: http://localhost:8080

 Использование API
Получить все элементы
bash
curl -X GET http://localhost:8080/items
Ответ:

json
[
  {"id": 1, "name": "First item"},
  {"id": 2, "name": "Second item"}
]
Получить элемент по ID
bash
curl -X GET http://localhost:8080/items/1
Ответ:

json
{"id": 1, "name": "First item"}
Создать новый элемент
bash
curl -X POST "http://localhost:8080/items?name=New%20Item"
Ответ:

json
{"id": 3, "name": "New Item"}
Удалить элемент
bash
curl -X DELETE http://localhost:8080/items/1
Ответ:

text
Item deleted
 Структура проекта
text
src/
└── main/
    └── kotlin/
        └── com/
            └── example/
                └── Main.kt - Основной файл приложения
 Модель данных
kotlin
@Serializable
data class Item(val id: Int, val name: String)
 Конфигурация
Порт: 8080

Хост: 0.0.0.0 (доступен извне)

Content-Type: application/json

 Коды ответов
200 OK - Успешный запрос

201 Created - Элемент создан

400 Bad Request - Неверный запрос

404 Not Found - Элемент не найден

 Примечания
Данные хранятся в памяти и сбрасываются при перезапуске сервера

ID генерируются автоматически как максимальный существующий ID + 1

Для создания элемента требуется query-параметр name

