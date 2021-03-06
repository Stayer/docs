#### Квоты {#quotas}
Вид ограничения | Значение
----- | -----
Количество балансировщиков в одном облаке | 2
Количество целевых групп в одном облаке | 2

#### Лимиты {#limits}
Вид ограничения | Значение
----- | -----
Количество ресурсов в целевой группе | 254
Количество портов обработчика | 10
Количество проверок состояния на подключенную целевую группу | 1
Протокол проверок состояния | TCP, HTTP

#### Прочие ограничения {#other-restrictions}
В одной целевой группе могут находиться целевые ресурсы только из одной облачной сети. 

В пределах одной зоны доступности в целевую группу могут входить ресурсы, подключенные к одной подсети.

Можно создать балансировщик без обработчика.

Целевые ресурсы должны принимать соединения на том же порту, что и обработчик.

Один целевой ресурс нельзя подключать к разным балансировщикам.

Проверки состояния передаются из диапазона адресов `198.18.235.0/24`.

Количество одновременных подключений к балансировщику соответствует [лимиту](../vpc/concepts/limits.md) в 50000 TCP/UDP-соединений.