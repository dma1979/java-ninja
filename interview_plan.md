# Список тем, с которыми стоит ознакомиться или освежить в памяти перед собеседованием 
* основы Java;
* ООП;
* Java core;
* структура данных;
* многопоточность;
* сборка мусора;
* базы данных;
* фреймворки;
* сетевые протоколы;
* устройство JVM;
* архитектура;
* паттерны;
* алгоритмические задачи;

##Основы Java

### В чем важность метода main()?
Этот метод является отправной точкой приложения.
Виртуальная машина Java запускается путем создания начального класса, который задается зависимым от реализации способом, используя загрузчик класса начальной загрузки (§5.3.1). Затем виртуальная машина Java связывает исходный класс, инициализирует его и вызывает метод открытого класса void main(String[]). Вызов этого метода управляет всем дальнейшим выполнением. Выполнение инструкций виртуальной машины Java, составляющих основной метод, может вызвать связывание (и, следовательно, создание) дополнительных классов и интерфейсов, а также вызов дополнительных методов.

### В чем разница между переменными path и classpath?
PATH - это строка, содержащая пути к исполняемым файлам.

CLASSPATH содержит пути к папкам, в которых VM будет искать файлы *.class, *.jar и другие, которые ей нужны. 
Альтернатива - запускать приложение с ключом -cp, после которого идет нужный этому приложению CLASSPATH.

### Какие есть модификаторы доступа?
В Java используются следующие модификаторы доступа:

public: публичный, общедоступный класс или член класса. Поля и методы, объявленные с модификатором public, видны другим классам из текущего пакета и из внешних пакетов.

private: закрытый класс или член класса, противоположность модификатору public. Закрытый класс или член класса доступен только из кода в том же классе.

protected: такой класс или член класса доступен из любого места в текущем классе или пакете или в производных классах, даже если они находятся в других пакетах

Модификатор по умолчанию. Отсутствие модификатора у поля или метода класса предполагает применение к нему модификатора по умолчанию. Такие поля или методы видны всем классам в текущем пакете.


### Что такое классы-оболочки?
Классы-оболочки Java являются Объектным представлением восьми примитивных типов в Java. 
Все классы-оболочки в Java являются неизменными и final.

### В чем разница между equals () и ==?
== - оператор, а equals() - метод. Операторы обычно используются для сравнения примитивных типов, и поэтому == используется для сравнения адресов памяти, а метод equals() используется для сравнения объектов.

### Что такое JIT-компилятор?
Just In Time compiler, также известный как JIT compiler, используется для повышения производительности в Java. Он включен по умолчанию. Это компиляция, выполняемая во время выполнения, а не раньше. 

* Когда мы скомпилируем нашу Java-программу (например, с помощью команды javac ), мы получим исходный код, скомпилированный в двоичное представление нашего кода - байт-код JVM ** . Этот байт-код проще и компактнее, чем наш исходный код, но обычные процессоры на наших компьютерах не могут его выполнить.

* Чтобы иметь возможность запускать Java-программу, JVM интерпретирует байт-код ** .

* Поскольку интерпретаторы обычно работают намного медленнее, чем собственный код, выполняемый на реальном процессоре, JVM может запустить другой компилятор, который теперь скомпилирует наш байт-код в машинный код, который может запускаться процессором. 
  Этот так называемый компилятор "точно в срок" намного сложнее, чем компилятор javac , и он выполняет комплексную оптимизацию для генерации высококачественного машинного кода.

### В чем заключаются особенности языка программирования Java?
* Простой
* Интерпретируемый
* Распределенный
* Надежный
* Безопасный
* Машинонезависимый
* Объектно-ориентированный
* Высокопроизводительный
* Многопоточный
* Динамичный
* Не зависящий от архитектуры компьютера

### Что такое статический импорт?
При объявлении статического импорта статические члены импортируются из классов, что позволяет им быть использованными без указания имени содержащего их класса.
Java _static import_ позволяет импортировать статические методы и переменные классы. Статический импорт java улучшает читабельность и качество.

### Что такое Enum?
Enum — специальный "класс", представляющзий собой ограниченный список именованных констант.

### Что такое композиция?
Композиция является одним из методов проектирования, который реализовывает отношение типа has-a в классах. 
Мы можем использовать наследование в Java или композицию для повторного использования кода. 

_Композиция_ в Java достигается за счет использования переменных экземпляра, который ссылается на другие объекты.
Композиция даёт возможность переиспользовать код без расширения существующего класса, как это происходит в случае с наследованием.


##Java core
###Как устроена HashMap?
###Чем отличается LinkedList от ArrayList?
###Разница между String, StringBuffer и StringBuilder?
###Разница между интерфейсом Runnable и Callable?
###Разница между TreeSet и TreeMap?
###Напишите программу на Java, чтобы проверить, является ли число простым или нет?
###Как проверить, содержит ли связанный список цикл в Java?
###Написать Java-программу для обратного преобразования String без использования API?
###Разница между переходным процессом и изменчивым в Java?
###Разница между абстрактным классом и интерфейсом?

##ООП
###Что такое перегрузка методов в ООП или Java?
###Какой метод скрытия используется в Java?
###Является ли Java чистым объектно-ориентированным языком?
###Каковы правила перегрузки и переопределения методов в Java?
###Какова разница между перегрузкой метода и переопределением?
###Можем ли мы предотвратить переопределение метода без использования модификатора final?
###Что такое ковариантный метод переопределения в Java?
###Можем ли мы изменить возвращаемый тип метода на подкласс при переопределении?
###Как вы вызываете суперклассовую версию метода переопределения в подклассе?
###В чем разница между абстракцией и полиморфизмом в Java?

##Структуры данных
###Чем дерево отличается от графа?
###Что такое АВЛ-деревья?
###Чем стек отличается от очереди?
###Какие классы в Java реализуют стек или очередь?
###Чем LinkedList отличается от ArrayList?
###Что такое HashSet?
###Чем HashSet отличается от TreeSet?
###Как работает HashMap?
###Найдите средний элемент односвязного списока за один проход.
###Как реализовать бинарное дерево поиска?

##Многопоточность

###Что такое поток?
Поток с точки зрения объектной модели Java — это объект класса, наследующего класс Thread или реализующего интерфейс Runnable.
Поток в Java представлен в виде экземпляра класса java.lang.Thread и экземпляры класса Thread в Java сами по себе не являются потоками. 
Это лишь своего рода API для низкоуровневых потоков, которыми управляет JVM и операционная система.

Существует 2 типа потоков: демоны и не демоны. Демон-потоки — это фоновые потоки (служебные), выполняющие какую-то работу в фоне.

###В чем разница между потоком и процессом?
Процесс — это совокупность кода и данных, разделяющих общее виртуальное адресное пространство.
Процесс не может существовать без потоков, поэтому если существует процесс, в нём существует хотя бы один поток.

Процессы и потоки связаны друг с другом, но при этом имеют существенные различия. 
Процесс — экземпляр программы во время выполнения, независимый объект, которому выделены системные ресурсы (например, процессорное время и память). 
Поток — определенный способ выполнения процесса.

###Как реализовать потоки?
* _extends Thread_: cоздать своего наследника от Thread
* _implements Runnable_: далее  передать его в конструктор Thread при создании экземпляра класса.

###Когда нужно использовать Runnable vs Thread?
Если вы хотите реализовать или расширить любой другой класс, то интерфейс Runnable является наиболее предпочтительным, в противном случае, если вы не хотите, чтобы какой-либо другой класс расширялся или реализовывался, то предпочтителен класс Thread .

Когда вы создаете класс _extends Thread_, каждый из ваших потоков создает уникальный объект и связывается с ним. 
Когда вы _implements Runnable_, он совместно использует один и тот же объект для нескольких потоков.

* Что-то, что может работать внутри потока (Runnable).
* Что-то, что может запустить новый поток (Thread).

###В чем разница между методами start() и run() класса Thread?
Thread. start() запускает поток, который вызывает метод run() , в то время как Runnable. run() просто вызывает метод run() в текущем потоке.

###Что такое модель памяти Java?
Java-модель памяти, используемая внутри JVM, делит память на стеки потоков (thread stack) и кучу (heap).

Каждый поток, работающий в виртуальной машине Java, имеет свой собственный стек. 
Стек содержит информацию о том, какие методы вызвал поток, чтобы достичь текущей точки выполнения.
Стек потока содержит все локальные переменные для каждого выполняемого метода (всех методов в стеке вызовов). 
Поток может получить доступ только к своему стеку. 
Локальные переменные, невидимы для всех других потоков, кроме потока, который их создал. 
Даже если два потока выполняют один и тот же код, они всё равно будут создавать локальные переменные этого кода в своих собственных стеках. 
Таким образом, каждый поток имеет свою версию каждой локальной переменной.

Куча содержит все объекты, созданные в вашем приложении Java, независимо от того, какой поток создал объект. 
К этому относятся и версии объектов примитивных типов (например, Byte, Integer, Long и т.д.). 
Неважно, был ли объект создан и присвоен локальной переменной или создан как переменная-член другого объекта, он хранится в куче.

###Что такое volatile?
Модификатор volatile накладывает некоторые дополнительные условия на чтение/запись переменной. Важно понять две вещи о volatile переменных:
* Операции чтения/записи volatile переменной являются атомарными.
* Результат операции записи значения в volatile переменную одним потоком, становится виден всем другим потокам, которые используют эту переменную для чтения из нее значения.

###Что такое изменчивая переменная в Java?
Переменная, объявленная с ключевым словом _volatile_, имеет два основных качества, которые делают ее особенной.
* Если у нас есть переменная volatile, она не может быть кэширована в кеш-память компьютера (микропроцессора) каким-либо потоком. Доступ всегда происходил из основной памяти.
* Если есть операция записи, выполняющая изменчивую переменную, и внезапно запрашивается операция чтения, гарантируется, что операция записи будет завершена до операции чтения. 

###Что такое потокобезопасность? Vector – это потокобезопасный класс?
Потокобезопасность просто означает, что он может использоваться из нескольких потоков одновременно, не вызывая проблем.
Когда класс тщательно синхронизирован для защиты данных, мы называем его потокобезопасным или Thread-Safe.

###Что происходит, когда в потоке возникает исключение?
Если для ThreadGroup установлен обработчик исключений, то JVM передает ему исключение.

##Сборка мусора
###Какова структура Java Heap? Что такое пространство Perm Gen в куче?
###Как определить незначительную и основную сборку мусора в Java?
###В чем разница между сборщиками мусора ParNew и DefNew Young Generation?
###Как вы обнаружите, что сборщик мусора привел к вызову System.gc ()?
###В чем разница между последовательным и пропускным сборщиками мусора?
###Когда объект получает право на сборку мусора в Java?
###Что такое метод finalize в Java? Когда сборщик мусора вызывает метод finalize?
###Как отслеживать действия по сбору мусора?
###Можно ли принудительно запустить сборщик мусора в любое время?
###Происходит ли сборка мусора в постоянном пространстве генерации в JVM?

##JVM
###Что такое куча и стек?
###Как хранятся объекты в JVM?
###Что такое string pool?
###Что обеспечивает принцип happens before?
###Как работает сборщик мусора?
###В чем разница между потоком пользователя и потоком демона?
###Что такое OutOfMemoryError в Java?
###Можно/нужно ли обрабатывать ошибки JVM?
###В чем разница между ошибкой и исключением?
###Объясните что такое JDK, JRE и JVM.

##Архитектура
###Когда нужно использовать микросервисы, а когда монолит?
###Использовали ли вы eureka или consul?
###В чем разница между Hibernate и JDBC?
###Каковы преимущества использования Hibernate перед JDBC?
###Выгодно ли использование среды Spring для разработчиков Java?
###Если у вас есть приложение Java с подключением к базе данных, которое необходимо улучшить, как бы вы его улучшили?
###Как избежать тупика базы данных?
###Что такое шардинг и насколько он полезен?
###Что такое масштабируемость?
###Что такое балансировка нагрузки?

##Паттерны
###Примеры паттернов ы Spring
###Immutable
###Singleton
###Prototype
###Builder 
###Proxy
###Abstract factory
###Strategy
###Visitor
###Wrapper

##Базы данных
###Реляционные и нереляционные БД – в чем разница? Что и когда использовать?
###Как строится запрос SQL?
###Какие виды join-ов существуют?
###Чем having отличается от where?
###Были ли у вас в практике случаи оптимизации запросов?
###Приходилось ли смотреть план выполнения запроса?
###Что такое entity manager?
###Что такое persistence context?
###Что такое JPQL и чем он отличается от SQL?
###Что означает полиморфизм в запросах JPQL и как его «выключить»?

##Spring Framework
###Transactional – как она работает? Что в ней можно дополнительно настроить?
###Назовите различные модули фреймворка Spring.
###Перечислите некоторые важные аннотации в конфигурации Spring на основе аннотаций.
###Объясните Bean в Spring и перечислите различные области применения Spring bean.
###Объясните роль DispatcherServlet и ContextLoaderListener.
###В чем разница между внедрением конструктора и внедрением установщика?
###Как обрабатывать исключения в Spring MVC Framework?
###Какие важные аннотации Spring вы использовали?
###Как интегрировать Spring и Hibernate Frameworks?
###Назовите типы управления транзакциями, которые поддерживает Spring.

##Сетевые протоколы
###Что такое IP-адрес?
###Что такое веб-сервис?
###Какие существуют типы веб-сервисов?
###В чем отличие host и domain?
###Какие методы в HTTP вы знаете?
###Чем отличаются методы GET, POST и HEAD?
###Что такое REST?
###Зачем нужен класс Calendar в Java?
###Как преобразовать дату в Java к нужному формату?
###Отличие классов Socket и URL?


## Популярные вопросы
### Как работает Java?
JDK (Java Development Kit) – набор необходимых инструментов, позволяющих развернуть Java на любой платформе, программировать и компилировать код.

JRE (Java Runtime Environment) – это то место, где находится JVM (виртуальная машина), весь запущенный рантайм и загруженные классы, т. е. все, что нужно для работы и функционирования кода.

JVM (Java Virtual Machine) – основная штука, с помощью которой кросс-платформенность в принципе возможна. 
Работает примерно так:
- написанный код компилируется в байт-код, который может запускаться на этой виртуалке;
- виртуалка интерпретирует весь код в машинный код для конкретной платформы.

JIT (Just-in-time) – оптимизированная штука от Java, чем-то похожая на precompiled header из C++.

JNA (Java Native Access) – способ из Java вызывать нативный код для решения некоторых задач.

### Разница между интерфейсом и абстрактным классом
* _Абстрактные классы_ могут иметь константы и переменные, определенные и объявленные методы с любыми модификаторами доступа.
* _Интерфейсы_ включают в себя только константы и только объявление методов с публичным доступом.  Интерфейсы участвуют в имитации множественного наследования, а в случае с классом, он может наследоваться только от одного класса-родителя.

### Ключевое слово static
* Статическими могут быть как переменные, так и методы. Переменные экземпляров, объявленные как static, являются глобальными переменными. При объявлении объектов не создается никаких копий статической переменной. Вместо этого все экземпляры класса совместно используют одну и ту же статическую переменную.
* Статические методы могут вызывать только другие статические методы, умеют обращаться только к статическим переменным и не могут ссылаться на this и super.

### Ключевое слово final
Данное ключевое слово может применяться к методам, классам и переменным. Если это:
* _Класс_, то от него нельзя наследоваться.
* _Метод_, то его нельзя переопределять в саб-классах.
* _Переменная_, то это константа.

### Примитивы и объекты
К примитивам Java относится byte, short, char, int, long, float, double, boolean, а кастомные типы данных (класс String) формируются уже из примитивов.

Примитивы несут в себе значение, а не ссылки!

Для примитивов используется стек, а для объектов – куча.

### Передача по ссылке или по значению
Когда создается объект, то ссылка на объект хранит в себе адрес в памяти того объекта, который был создан с помощью оператора new. Если такую ссылку передать в качестве параметра функции, то в том месте, где она передается, будет создана копия, поэтому передача произойдет по значению. Но данная копия будет ссылаться на тот адрес, на который ссылается и оригинал. Если произвести действия над этой копией, оригинал тоже будет изменен.

С примитивами все проще: передав примитив в метод и изменив его там, будет изменяться копия, и это не повлияет на глобальные значения. 

### Анонимные классы
Существуют обычные классы и вложенные. Вложенные делятся еще на несколько видов, и среди них есть анонимный внутренний класс. 

Если коротко, то _анонимный класс_ - это класс без имени, который находится внутри другого класса.

### Перегрузка и переопределение
_Переопределение_ позволяет взять какой-то метод родительского класса и написать в каждом классе-наследнике свою реализацию этого метода.
Эта тема – ключ к пониманию, как работает полиморфизм.

Чтобы понять перегрузку, нужно запомнить, что тип и/или число параметров в каждом из перегружаемых классов должно быть разным.


