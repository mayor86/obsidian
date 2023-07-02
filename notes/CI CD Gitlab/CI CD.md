![[Pasted image 20230622225220.png]]

Главное достоинство CI/CD – непрерывная доставка, благодаря которой можно моментально отследить свежие изменения в коде, найти и устранить баги до того, как это сделают клиенты. Такой подход особенно эффективен при работе с микросервисной архитектурой.

CI/CD позволяет шаблонизировать процессы, чтобы освободить разработчиков от лишних деталей и дать им возможность заниматься своей непосредственной работой – писать качественный код. Когда в компанию приходит новый сотрудник, его нужно оперативно ввести в курс дела. Методика CI/CD незаменима и здесь, потому что в стандартизированной системе в разы проще разобраться.

JEZ HUMBLE:
1. Закоммитьте свои изменения
2. Запуште сборку
3. Проверьте свои изменения --> Если сейчас все сломалось, то ничего страшного, вы на фича-ветке (сломали только у себя) --> Откатываемся назад и ищем причину.
4. Подтяните в свою ветку свежие изменения из master и повторите сборку. --> Если сейчас все сломалось, то кто-то из коллег закоммитил что-то в мастер, что делает ваши изменения неактуальными --> Нужно подстроится под новый код, т.к. его выкатили первым.
5. Делаем Merge Request (вливаем изменения в master) --> Если сейчас все сломалось, то либо чиним за 5 мин, либо откатываем свой коммит.
6. Вы молодец, добавили ценность в ПРОД (считаем что CD прошел сразу)
![[Pasted image 20230622231228.png]]

**GitLab Runner** — это агент, который собственно и занимается выполнением инструкций из специального файла .gitlab-ci.yml.  
В отличие от Jenkins раннеры гитлаба написаны на Go, поэтому они очень маленькие и быстрые. И умеют запускать задачи совершенно различными способами: локально, в докер-контейнерах, в различных облаках или через ssh-коннект к какому либо серверу. Подробности, как всегда, [в документации](https://gitlab.com/gitlab-org/gitlab-ci-multi-runner)