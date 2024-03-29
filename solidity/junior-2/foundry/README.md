# Вопросы по Foundry

## Общие вопросы

1. Что такое Foundry? Для чего используют forge, anvil, cast?
2. Чем Foundry отличается от Hardhat?
3. Как forge управляет зависимостями библиотек в проекте?
    - Что такое remapping dependencies?
4. Как можно дебажить вместе с Foundry?
5. Какими способами можно деплоить контракты с Foundry?

## Тестирование

1. Как в Foundry реализовать процесс тестирования контракта? Что такое Forge Std библиотека? Для чего она нужна?
2. Какие префиксы бывают у имен тестовых функций?
3. Будет ли протестирована функция если указать ее видимость как internal или private?
4. Можно ли использовать вспомогательные контракты для хранения функций и переменных применяемые при тестировании? Как это сделать?
5. Что делает функция setUp()? Она обязательная?
6. Что такое cheatcodes и для чего они нужны? Назови cheatcode для каждой ситуации:
    - Вызов функции от имени другого адреса?
    - Проверить, что функция возвратить ошибку?
    - Проверить, что функция генерирует ивент? Расскажи про boolean параметры в cheatcode vm.expectEmit(topic1, topic2, topic3, topic4). Что за topic и для чего они нужны?
7. Как работают cheatcodes vm.roll и vm.warp?
8. Поддерживает ли Foundry Fork testing? Какие есть способы?
9. Что такое Fuzz Testing? Для чего это может быть полезно?
10. Что такое Invariant Testing?
11. Что такое Differential Testing?
12. Как тестировать подписи сообщений?

- [Foundry documentation](https://book.getfoundry.sh/)