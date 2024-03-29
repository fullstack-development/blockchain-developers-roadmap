# Вопросы по Solidity

## Evm opcodes

1. Что такое opcodes?
    - Что означает цепочка ```Solidity → Байт-код → Opcodes```?
    - Для чего необходимо базовое понимание opcodes?
2. Известно, что opcodes условно делятся на несколько групп. Твоя задача, на каждую группу, привести в пример несколько opcodes и обозначить предназначение всей группы.
    - Управление стеком.
    - Арифметика
    - Операции среды
    - Управление памятью memory
    - Управление памятью storage
    - Управление program counter
    - Остановка процесса
3. За выполнение каждого opcode, требуется оплата за выполнение в сети. Оплата выражена в единицах, которые называются газ.
    - В чем разница между базовой стоимостью выполнения opcode и динамической?
    - Какой самый дорогой opcode? Сколько газа он требует?
4. Что делает следующий байт-код? Какой будет результат выполнения?
    > 6002600404600201

- [Evm opcodes](https://www.evm.codes/?fork=shanghai)
- [The Ethereum Virtual Machine — How does it work?](https://medium.com/mycrypto/the-ethereum-virtual-machine-how-does-it-work-9abac2b7c9e)

## Bitwise operators

1. Что такое бит и байт, в чем отличие?
2. Что такое знаковые и беззнаковые числа в контексте битов?
3. Какие бывают виды знаковых чисел? Какой вид самый используемый?
4. Как работают прямой, обратный и дополнительный код? Какие проблемы могут возникнуть в прямом и обратном коде?
5. Что такое битовые операции?
6. Какие существуют битовые операции?
7. Что такое логические вентили?
8. Какие действия можно выполнять с битами используя битовые операции?
9. Что такое битовые сдвиги?
10. Как работают арифметический, логический и циклический сдвиги? В чем отличия?
11. Где используются битовые операции и для чего?
12. Что происходит в этом коде? Как можно сделать то же самое по-другому?
    ```js
        function bitOperation(uint8 number, uint8 index) external pure returns (uint256) {
            return number & ~(1 << index);
        }
    ```

- [Двоичные числа](https://asm.kcup.tusur.ru/Library/chapter%201/1-1.html)
- [Как два байта переслать](https://pikabu.ru/story/kak_dva_bayta_pereslat_7070913)
- [Прямой, обратный и дополнительный код](https://microkontroller.ru/programmirovanie-mikrokontrollerov-avr/pryamoy-obratnyiy-dopolnitelnyiy-kod-dvoichnogo-chisla/)
- [Видео: как работают отрицательные числа](https://www.youtube.com/watch?v=BIYiuy8WWiU)
- [Bitwise operation](https://en.wikipedia.org/wiki/Bitwise_operation)
- [Видео: как работать с битами](https://www.youtube.com/watch?v=qewavPO6jcA)
- [Побитовые операции](https://neerc.ifmo.ru/wiki/index.php?title=%D0%9F%D0%BE%D0%B1%D0%B8%D1%82%D0%BE%D0%B2%D1%8B%D0%B5_%D0%BE%D0%BF%D0%B5%D1%80%D0%B0%D1%86%D0%B8%D0%B8)

## Yul

1. Что такое Yul? Как и для чего он используется?
2. Как работает область видимости переменных в **inline assembly** вставках? Рассказать как будет работать код на примере ниже.
    ```js
        assembly {
            let x := 3

            {
                let y := x
            }

            {
                let z := y
            }
        }
    ```

3. Какие есть типы данных в Yul, как объявляются переменные с этими типами?
4. Какие литералы допустимо использовать в коде Yul?
5. Рассказать про инструкции в Yul, в какой последовательности будет выполняться код ниже? Чему будет равен `x` если `a` = 3, `b` = 6?
    ```js
        let x := div(mul(a, b), add(a, b))
    ```

6. С помощью каких операторов выстраивается поток управления в Yul?
7. Как устроен тип памяти storage, какие два вида переменных существуют в storage?
    - Как работает упаковка слотов в storage? Как записывать и извлекать значения из упакованных слотов?
    - Как хранятся структуры в storage?
    - Как хранятся массивы с фиксированной длиной? Где хранится длина массива?
    - Как хранятся динамические массивы? Где хранится длина и как получить доступ к индексу массива? Как получить доступ к динамическому массиву вложенному в динамический массив?
    - Как хранятся mappings? Как получить доступ к элементу mapping? Как получит доступ к mapping вложенному в mapping? Как получить доступ к массиву вложенному в mapping?
    - Как хранятся массив байтов и строки? Какая есть особенность?
    - Какие есть инструкции для работы со storage в Yul?
8. Как устроен тип памяти memory? Для чего используется тип памяти memory?
    - Когда переменные инициализируются в memory и когда очищаются?
    - Какая есть особенность при работе с memory? Можно ли записывать что-то в первые 128 байт? Как они используются Solidity?
    - Как получить указатель на свободное место в memory?
    - Очищается ли memory автоматически при переключении с кода solidity на inline assembly и наоборот?
    - Какие есть инструкции для работы с memory в Yul?
    - Как хранятся структуры в memory?
    - Как хранятся массивы фиксированной длины и динамические массивы?
    - Как хранятся массивы байтов и строки?
    - Как работают инструкции `revert` и `return`?
    - Как работает `keccak256` в memory?
9. Как устроен тип памяти calldata?
    - Для чего используется тип данных calldata?
    - Почему работать с calldata дешевле по газу чем с memory?
    - Какие инструкции в Yul есть для работы с типом данных calldata?
    - Как в calldata хранятся массивы?
    - Как в calldata хранятся массивы байтов и строки?
    - Как сделать срез данных (array slice), для чего это нужно?
10. Как в Yul выполняется вызов смарт-контрактов?
    - Какие инструкции используются для вызова смарт-контрактов?
    - Как работает инструкция `call(g, a, v, in, insize, out, outsize)`?
    - Как обрабатываются возвращаемые данные?
11. Как работать с событиями в Yul?
    - Рассказать что происходит в функции `foo`:
        ```js
        contract EmitEvent {
            event SomeLog(uint256 indexed a, uint256 indexed b, bool c);

            function foo() external {
                assembly {
                    let signature := 0x39cf0823186c1f89c8975545aebaa16813bfc9511610e72d8cff59da81b23c72

                    let ptr := mload(0x40)
                    mstore(ptr, 1)

                    log3(0x80, 0x20, signature, 2, 3)
                }
            }
        }
        ```
12. Можно ли писать смарт-контракты на чистом Yul?

- [Docs: Yul](https://docs.soliditylang.org/en/latest/yul.html)
- [Docs: Layout of memory](https://docs.soliditylang.org/en/latest/internals/layout_in_memory.html)
- [Playlist: Mastering Solidity Assembly (YUL)](https://youtube.com/playlist?list=PL5hld-skrdFrxGUmmEbG1LBvYVyTE9M62&si=jwXH_rtSvoNfrDPg)
- [Article: Inline Assembly in Solidity: A Practical Starter’s Guide](https://medium.com/lumos-labs/inline-assembly-in-solidity-34d3ba2cfa7a)
- [Video: The Dark Arts of Yul](https://www.youtube.com/watch?v=ew3pfnb2_V8)