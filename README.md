## Приложение "Список клиентов"
- Для проверки выполнить запросы в файле `TestRequests.http`
- Т.к. на данный момент нет подключения к базе данных, то список клиентов при запуске приложения всегда пуст

### Home Work №4
- Для тестирования необходимо:
  1. Запустить приложение
  2. Перейти по [ссылке](localhost:8080/clients)
  3. Добавить клиента
  4. Нажать кнопку изменить
  5. В открывшемся окне заполнить форму
  6. Нажать обновить информацию

### Home Work №5
1. Добавлена зависимость для генерации документации в swagger
2. Добавлено поле `gender` для клиента
3. Рализовано подключение к базе данных
4. Подготовлен `Dockerfile` для создания образа и запуска базы данных в контейнере
5. Реализован функционал фильтрации клиентов по полю `gender`

### Home Work №6
1. Добавлены новые сущности "Продукт\Услуга" и "Покупка"
2. Реализован сервис для работы с новыми сущностями
3. Релизованы контроллеры для работы с новыми сущностями
4. Продукт\Услуга успешно создаются
5. Покупка успешно совершается, но не могу получить ответ в JSON

**ВОПРОС! Помогите найти ошибку! При соверении покупки `POST v1/purchase` получаю ответ 500, 
предположительно не получается вернуть ответ в формате JSON. При этом в базе данных покупка создается, 
все связи проставляются корректно. Что реализовано неправильно?**

- Вопрос решен добавлением строки `spring.jackson.serialization.FAIL_ON_EMPTY_BEANS=false` в файл `aplication.properties`

### Home Work №8
1. Реализовано логирование процесса выполнения операций
2. Подключено к сервису `ClientServiceImpl` для всех методов путем использования аннотации `@LogExecution`
3. Реализовано логирование получения ошибок в процессе выполнения операции
4. Подключено к сервису `ClientServiceImpl` для всех методов путем использования аннотации `@LogException`
5. Для тестирования в методе удаления пользователя был реализован выброс `RuntimeException` в случае, если пользователь с переданным `id` не был найден в базе данных

>**Вопрос** 
> 
>Можно ли реализовать анномацию так, чтобы ее можно было повесить на класс и логирование шло на все методы этого класса? Пробовал в анноотации `Target` прописывать `ElementType.TYPE` - не помогло. 
> 
>Или такое возможно только в реализации, которую вы дополнительно прикрепили к семинару, где указываются пакеты? 
