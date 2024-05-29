# Социальная сеть для путешественников

**Функциональные требования:**
1. Публикация постов с фотографиями, кратким описанием и ссылкой на конкретное место назначения
2. Возможность оценивать и комментировать посты других пользователей
3. Подписка на других пользователей для отслеживания их активности
4. Поиск популярных мест для путешествий и просмотр постов из этих мест в виде «Топ мест» по странам и городам
5. Обмен приватными сообщениями с другими пользователями
6. Просмотр лент других пользователей
 
**Нефункциональные требования:**

Посты и файлы:
  * Максимальная размерность фотографий: 10 MB (аналогично Instagram).
  * Максимальная длина описания поста: 500 символов (аналогично Twitter).
  * Формат хранения геоданных: GeoJSON (аналогично OpenStreetMap).
  * Ограничения на типы файлов: только изображения в формате JPEG, PNG, GIF.

Оценки и комментарии:
  * Оценка: 5-балльная шкала (аналогично TripAdvisor).
  * Комментарии: максимальная длина 200 символов (аналогично Facebook).

Подписка на пользователей:
  * Максимальное количество подписок: 1000 пользователей (аналогично Twitter).

Поиск популярных мест:
  * Алгоритм ранжирования: комбинация популярности мест, оценок пользователей и расстояния от местоположения пользователя (аналогично Google Maps).

Обмен сообщениями:
  * Максимальная длина сообщения: 1000 символов (аналогично WhatsApp).

Просмотр лент других пользователей:
  * Тип ленты: infinite scrolling (аналогично Instagram).

Доступность:
  * Система должна быть доступна для пользователей из стран СНГ.

Масштабируемость:
  * Ожидаемая скорость роста пользовательской базы: 1-2% в месяц в первые два года после достижения 10 000 000 пользователей, с дальнейшим замедлением.
  * Примерное количество единовременных соединений - 10 000 000 * 10% = 1 000 000
  * Средняя нагрузка: ~2000 RPS (10 000 000 * 15 / 86400 = 1736). Средний пользователь социальных сетей в среднем совершает около 15 запросов в день (основываясь на данных Facebook, Twitter, Instagram).
  * Пиковая нагрузка: ~5000 RPS (приблизительно взят коэффициент x2.5, что больше соответствующей величины для международных приложений, так как страны СНГ находятся в близких часовых поясах).
  * Средний размер запроса ~2.1 KB. Большинство изображений будут меньше лимита в 10 MB, в диапазоне 500 KB - 1 MB. Средний размер GET-запроса с учетом мета-данных - от 1 до 5 KB (просмотр постов, пролистывание ленты). Средний размер POST-запроса с учетом мета-данных - 200-300 B для постов, 100-150 B для комментариев, 500-700 B для личных сообщений. Предположим, что примерное соотношение запросов будет: 70% GET, 20% POST, 10% изображения. Взяв это соотношения и средние значения для всех типов запросов, получим примерно такую формулу: avg_request_size = (0.7 * 3 KB) + (0.2 * 300 B) + (0.1 * 750 KB) ≈ 2.1 KB.
  * Средний траффик, таким образом, составит 2000 * 2.1 = 4200 KB/s, а пиковый 5000 * 2.1 = 10500 KB/s.

Надежность:
  * 99,9% (реалистичное значение для уровня доступности большинства веб-приложений, не слишком сильно уступающее надежности передовых социальных сетей вроде Facebook, Twitter и Instagram).

Удобство использования:
  * Adaptive Design для мобильных устройств и desktop-браузеров.
  * Ожидаемая скорость загрузки контента на мобильных устройствах: 2 секунды.

Производительность:
  * Ожидаемое время ответа системы на запросы пользователей: 1 секунда.
