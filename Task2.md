# Задача "Исследование JVM через VisualVM"

Изучение использования памяти через VisualVM при загрузке новых классов и создании новых объектов на примере [проекта](https://github.com/Arsennikum/jvm-visualvm-experience)

**Метрики программы**:
![Метрики программы](https://github.com/A-Sakhmina/netology_javacore_jvm/blob/main/vusialvm_result.jpg)
**Результат вывода в консоль программы**:
![Результат вывода в консоль программы](https://github.com/A-Sakhmina/netology_javacore_jvm/blob/main/project_output.jpg)

## Скриншоты графиков с отметкой действий программы на таймлане.
**Heap**:
Наблюдаем относительно небольшое увеличение кучи при загрузке библиотек(увеличение идёт за счёт вызова метода `loadToMetaspaceAllFrom()`, 
в котором идёт инициализация экземпляров `Reflections`, `SubTypesScanner`, `Set`).
Далее наблюдаем значительное увеличение кучи за счёт создания новых объектов в большом количестве за счёт метода `createSimpleObjects`. 
В методе создаётся экземпляр `ArrayList` и большое количество(заданное пользователем) объектов `SimpleObject`.
![График heap](https://github.com/A-Sakhmina/netology_javacore_jvm/blob/main/heap.jpg)
**Metaspace**: 
Наблюдаем увеличение размера Metaspace при загрузки различных пакетов/библиотек(`io.vertx`, `io.netty`,`org.springframework`) и при первом создании объектов классса(внесение в **Metaspace** класса `SimpleObject`). В дальнейшем при создании новой партии объекта того же класса **Metaspace** не увеличивается. 
![График metaspace](https://github.com/A-Sakhmina/netology_javacore_jvm/blob/main/metaspace.jpg)
