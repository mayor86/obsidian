
## Вопросы
1. Схема архитектуры не особа понятна
2. Компоненты внутреннего и внешнего мониторинга совпадают? Можно ли задеплоить только внутренний мониторинг или только внешний?
3. Подробнее описать процесс разбора видео? 
4. ТГ-бот? У нас есть отправка по БП? -- ЭТО НЕ ДЕЛАЕМ (ПОКА)
## Исходники от Майндсет
https://gitlab.samoletgroup.ru/bigdata/models/videoanalytics

### construction_decor_capacitor
airplane pwa (constructor-decor-app-pwa)
Описания нет

Фронт приложение capacitor, которое устанавливается на телефон и предает видео в общее хранилище через Resilio.

### construction_decor_pwa
Приложение фронтенда системы мониторинга строительства (внутренняя отделка, ОТиПБ).

### construction_decor_pwa_back
Приложение для приема видео по api (Python)
![[Pasted image 20240116110901.png|200x200]]
Функционал:
1. Передача списока зданий по api
2. Прием видео по api
3. Соединение раздробленных частей видиео


## Архитектура
Внешний мониторинг: [https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860641](https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860641 "https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860641")

Перечислены компоненты, но не все есть на общей схеме. Из-за этого архитектура проекта не особа понятна.

Внутренний мониторинг: [https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860246](https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860246 "https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860246")

## Развертывание
Проект внешнего мониторинга и внутреннего мониторинга взаимозависимы, поэтому необходимо вначале развернуть внешний мониторинг и следом внутренний. Поэтапная инструкция по развертыванию внешнего и внутреннего мониторинга, а так же всех вспомогательных сервисов: [https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=218008898](https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=218008898 "https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=218008898")

Есть большая инструкция, читается довольно сложно.

## Руководство пользователя
Внешний мониторинг
Панель администратора внешний мониторинг: [https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860655](https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860655 "https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860655")

Внутренний мониторинг
Админ панель
Панель админиcтратора внутренний мониторинг: [https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860437](https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860437 "https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860437")

Мобильное приложение
Интерфейс: [https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860380](https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860380 "https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=188860380")

## Resilio Sync

Приложение Sync необходимо для того, чтобы видеоснятое в приложении S.view скачивалось на сервер где в дальнейшем видео будет обработано искусственным интеллектом


Инструкция по регистрации телефона в Resilio: [https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=206025099](https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=206025099 "https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=206025099")

Инструкция по установки и настройке приложения Resilio Sync + S.view: [https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=206025175](https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=206025175 "https://wiki.samoletgroup.ru/pages/viewpage.action?pageId=206025175")


## Встреча с Глебом 16.01.2024 Итоги
1. Нужно научиться разворачивать приложение в разных облаках (Эту задачу выполняем, когда приложение будет полностью переписано под наш стек)
2. Переписываем поэтапно, Мобилка -> Веб -> Бэк -> Забираем ML (про ML пока вопрос, будем ли забирать)
3. Разработку будем вести в Yandex Cloud
4. Команда: Сейчас есть Владелец продукта, Дизайнер, Мобильный разработчик. Запросить у Ильи Воробьева
5. Проработать вопрос с перекидыванием каталогов в Yandex cloud
6. Делаем план в AT (черновик в Google docs)
7. Подумать как в поэтапной приемке делать авторизацию


Нужно подробнее описать Архитектуру решения (должен включать основные компоненты решения, инфраструктуру их развертывания с указанием стека технологий, которые используются).
1. Должна быть компонентная схема. На схеме должны быть указаны все компоненты и их взаимодействие между собой, которые мы используем:
Внешний мониторинг плюс Внутренний мониторинг
![[Pasted image 20240117103915.png|150x200]]

На схеме цветом разделить компоненты внешнего и внутреннего мониторинга.
2. Для компонент с исполняемым кодом указать название репозитория/проекта git откуда он собирается.
3. Для всех компонент указать, как они приземляются на инфраструктуру (Виртуалка, Контейнеры). Указать все компоненты инфраструктуры.
4. Для текущего деплоя ФСК в Yandex Cloud указать все сервисы Yandex Cloud, которые используются и ресурсы (CPU, RAM, Диск), выделенные под них.


## Поэтапное переписывание функционала под наш стек

![[Pasted image 20240201101852.png]]![[Pasted image 20240201101912.png]]
![[Pasted image 20240201101933.png]]