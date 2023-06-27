# On-board-computer
Программа для бортового компьютера с использованием Arduino для мотоцикла.

## Содержание
- [Возможности данной системы](#possibilities)
- [Настройки в программе](#settings)
- [Версии](#versions)

<details>
<summary>Печатная плата версии 1.1</summary>
  
![Снимок экрана (229)](https://user-images.githubusercontent.com/98914596/227523754-4a894226-a50f-4dee-866c-b5c0760a0344.png)

![Снимок экрана (228)](https://user-images.githubusercontent.com/98914596/227523778-13929767-6987-40cb-bed5-fe86fbeffd14.png)

![Снимок экрана (269)](https://user-images.githubusercontent.com/98914596/152302594-038accc3-8d7a-41bd-a859-1d5ee7e6715a.png)

![Снимок экрана (315)](https://user-images.githubusercontent.com/98914596/152304932-b542c358-555f-4f2a-b90a-e0459858ce10.png)

</details>

**Новое!** Печатная плата версии 2.0

![Снимок экрана (621)](https://user-images.githubusercontent.com/98914596/227524028-127583b5-e5e1-4215-af5c-d1d2a282c108.png)

![Снимок экрана (627)](https://user-images.githubusercontent.com/98914596/227524253-68c96e26-99ba-4576-bb2a-9a42e390723c.png)

![Снимок экрана (625)](https://user-images.githubusercontent.com/98914596/227524171-5109d7ee-f4bd-4ce1-ae0b-4e31d6c6d6bc.png)

<details>
<summary>ещё фото</summary>

![Снимок экрана (623)](https://user-images.githubusercontent.com/98914596/227524471-6c7682d0-2f44-4279-a386-17850afbadd3.png)

![Снимок экрана (630)](https://user-images.githubusercontent.com/98914596/227524509-c7896081-abb2-462f-8e39-10fbe146ebfd.png)

</details>


Устройство на мотоцикле

![Снимок экрана (322)](https://user-images.githubusercontent.com/98914596/152306161-d93440b4-e3fa-4f79-a25c-1ad9fa971339.png)

![Снимок экрана (544)](https://user-images.githubusercontent.com/98914596/199455337-e09b5fae-a4e7-4f53-92f3-4d579ebb58d6.png)


<a id="possibilities"></a>
## Возможности данной системы
- На дисплее отображаются показания температуры цилиндров, напряжение в сети мотоцикла. 
- В правом верхнем углу выводятся предупреждения: высокое/низкое напряжение в сети, перегрев цилиндров. 
- Повторители указателей поворота отображаются на дисплее в виде стрелок, а также загорается светодиод и, если включить опцию в настройках, звучит пищалка. 
- При нажатии на кнопку на индикаторе высвечивается версия установленной программы, а на дисплее время текущей поездки. 
- При двойном нажатии на кнопку на индикаторе отображается количество оставшейся оперативной памяти, на дисплее – моточасы и температура процессора. 
- Система имеет ряд настроек:
  - при долгом нажатии на кнопку на индикаторе отображается “tune” и открывается меню настроек;
  - первый пункт – яркость индикатора TM1637 от 0 до 7;
  - второй изменяет порог показа максимальной температуры цилиндров;
  - третий – настройка минимального напряжения;
  - четвёртый – настройка максимального напряжения;
  - пятый* - включение пьезоэлемента;
  - шестой* - тест пьезоэлемента;
  - седьмой изменяет яркость светодиода;
  - восьмой обнуляет счётчик моточасов;
  - девятый* - включение предупреждений эко-оборотов.

*Все настройки, в том числе и моточасы, сохраняют свои значения после отключения питания, благодаря встроенной энергонезависимой памяти EEPROM (Electrically Erasable Programmable Read-Only Memory) – электрически стираемого программируемого ПЗУ.
 Настройки минимального напряжения необходима для корректного отображения предупреждений и корректной записи в EEPROM. Настройка максимального напряжения необходима для корректного отображения предупреждений. Настроить порог показа предупреждения о перегреве цилиндра можно любой.*
 
 *конфигурируется определениями (define)
 <a id="settings"></a>
## Настройки в программе
- с версии *2.9.5.1* находятся в файле `configuration.h`

Настройки библиотек: EB_BETTER_ENC (установлен по умолчанию с версии 2.0 библиотеки), EB_HALFSTEP_ENC, EB_FAST, MAX6675_DELAY
<a id="versions"></a>
## Версии
`старые версии находятся в LOG-versions.md. Они не предназначены для системы на плате`

- v2.0 версия для системы на печатной плате с мк-к Arduino Pro Mini, добавлена поддержка раздельного питания системы (с буферным аккумулятором, отключается от основной системы
при включении зажигания, при выключенном зажигании заряжается от основного аккумулятора), показание напряжения буферного аккумулятора при 1 нажатии на кнопку, 
предупреждение о низком заряде аккумулятора, небольшие правки кода;
- v2.1 добавлены новые символы для LCD 1602, доработан фильтр на сравнении - сравнение делается по модулю, усредняется, ускорена его работа, добавлены удобные макросы,
некоторые части кода переписаны в универсальные библиотеки, исправление недочётов; //15.10.21
- v2.2 Применена библиотека Tachometer (https://github.com/GyverLibs/Tachometer) для более оптимального считывания количества RPM, имеет встроенный медианный фильтр,
убраны все фильтры RPM (необходимо фильтровать не RPM, а резкие изменения количества времени между сигналами), изменены действия после нажатия кнопки, 
оптимизация кода; //20.12.21
- v2.3 применена библиотека EncButton (https://github.com/GyverLibs/EncButton) для работы с энкодером и кнопкой, написано меню с настройками (пока только яркость TM1637) в 
LCD1602, изменены действия кнопки (1 нажатие - выводится время поездки и версия программы, 2 нажатия - количество моточасов и температура процессора, долгое нажатие - переход
в меню настроек), оптимизация кода, исправлено много багов; //23.10.21
- v2.3.1 Исправление багов (не работал счётчик моточасов), добавлена функция вывода на индикатор оставшейся оперативной памяти при двойном нажатии на кнопку; //26.11.21
- v2.3.2 Исправление багов (некорректно работал счётчик моточасов и настройки из-за неправильной работы с EEPROM), добавлена функция обнуления счётчика моточасов(последний пункт меню), 
теперь все параметры в меню сохраняют значения после выключения платы, в меню настроек на TM1637 отображается "tune"; //30.11.21
- v2.3.2.1 Оптимизированы некоторые условия if, ускорен вывод температуры после включения, добавлен дефайн, при подключении которого становится возможной работа с некачественными и убитыми энкодерами (средствами библиотеки v1.12, EB_BETTER_ENC); //2.12.21
- v2.3.3 Функция изменения яркости светодиода, исправлен баг с быстрым поворотом энкодера; //6.12.21
- v2.3.4 Добавлен динамический вывод размерности температуры, режим для полушаговых энкодеров; //12.01.22
- v2.3.5 Для строк добавлен макрос F, сэкономлено 80 байт оперативки; //13.01.22
- v2.3.6 Исправление багов (неправильно работал светодиод).
Вывод строк через функцию printFromPGM (тех, которые часто повторяютя), макросы для вывода строк, сэкономлено пару байт; //16.01.22
- v2.3.7 Настройка минимального и максимального напряжения! (полезно при настройке показа предупреждений о низком или высоком напряжении,
мигании светодиода, также уровень минимального напряжения участвует в сохранении параметров в EEPROM при отключении), оптимизация записи 
и чтения EEPROM (теперь настройки сохраняются даже при отключении напряжения (из меню), тратится меньше процессорного времени, параметры меняются быстрее, 
меньше изнашивается память) //22.01.21
- v2.4.0 Добавлена поддержка активной пищалки (buzzer), добавлены директивы препроцессора ((#ifdef ... #endif) bufferBatt и RPMwarning, которые
включают код с обработкой буферного аккумулятора и предупреждения о высоких оборотах), убран серьёзный баг, который мог негативно влиять на
перезагрузку контроллера сторожевым таймером WDT, т.е. контроллер уходил в bootloop.	Это связано с тем, что контроллер автоматически ставит таймаут WDT на 16 мс и, 
если функция watchdog.enable() стоит не в начале, код до неё может выполняться дольше 16 мс (особенно со старым загрузчиком) и контроллер уходит в bootloop, 
вернее WDT перезагружает контроллер каждые 16 мс. Может случиться, что даже если сбросили таймер в начале сетапа, контроллер всё равно уходит в bootloop, 
тогда необходимо перепрошить загрузчик на optiboot или убрать его совсем. //2.02.2022 
- v2.4.1 Ускорена работа программы. Применена библиотека GyverMAX6675, исправлен баг. //4.02.2022
- v2.4.2 Оптимизация некоторых условий, вырезаны лишние действия, исправлены баги, функция настройки максимальной температуры цилиндров (при превышении этой температуры показывается предупреждение о перегреве цилиндров); //23.02.22 
- v2.4.3 Режим для активного/пассивного зуммера, переключается дефайном, режим теста зуммера в настройках, отлажено поведение светодиода в настройках; //5.03.22 
- v2.4.3.1 Оптимизация некоторых условий, правка комментариев; //20.04.22
- v2.4.4 Оптимизация работы с LCD1602: убраны ненужные setCursor, т.к. функция print сама переставляет курсор после выведенного слова (например можно писать
несколько параметров друг за другом), переделан вывод динамической температуры, заменены функции clear на более быстрые операции, убрано условие, при
котором значение моточасов записывалось в память каждые 10 минут, убраны лишние переменные, поправлены их типы, улучшения; //26.04.22 
- v2.4.5 Оптимизирована очистка дисплея пробелами в коде обработки указателей поворота и в коде вывода предупреждений о неисправностях на экран; //28.04.22 
- v2.5.0 Исправлен баг, из-за которого при определённых условиях в редких случаях светодиод оставался гореть (например, когда переменная z ещё соответствовала
состоянию включенного светодиода, а происходил выход из блока управления светодиодом (например температура или напряжение пришли в норму), и светодиод
оставался включенным (код выключения не выполнялся), исправлена печать символа градуса при изменении разряда температуры, 
чуть переделан вывод версии программы, другие исправления, вырезан вывод строк через функцию printFromPGM, т.к. компилятор сам оптимизирует строки, они не
дублируются в памяти, переработана структура программы для более оптимальной работы; //3.04.22
- v2.6.0 Применена библиотека GyverTimers для чёткой отработки периода теймера времени работы
(На 1 таймере может некорректно работать ШИМ на 9 и 10 пинах!), применены более лёгкие таймеры millis(), оптимизация памяти и скорости; //5.05.22 
- v2.7.0 Увеличена быстрота выполнения кода обработки указателей поворота, уменьшен вес, теперь компилятор выдаст ошибку, если одновременно
определить buzzActive и buzzPassive, предварительное объявление всех функций (быстрее компилируется), исправление ошибок, оптимизация блока
записи моточасов; //16.05.22
- v2.7.1 Переменнные, обрабатываемые в прерывании, объявлены volatile; //26.05.22
- v2.8.0 trip time заменен на более корректный elapsed time, таймаут WDT изменён с 8 сек. на 4 сек., исправлен код, небольшая правка в setup,
t1 и t2 изменены на tL и tR (левый и правый), увеличена задержка переключения CLK до 20 мкс; //23.08.22
- v2.8.1 Небольшая правка вывода ошибки #error; //31.10.22
- v2.9.0 Теперь можно определить количество цилиндров мотоцикла через define OneCylinder и TwoCylinders. Нельзя одновременно определять эти настройки, также необходимо
определить хотя бы одну из них (программа предупредит о неправильной установке определений). При одновременной установке OneCylinder и bufferBatt напряжение и
предупреждения о низком напряжении буферного аккумулятора будут находиться под температурой цилиндра. Если в проекте не используется пьезоэлемент, можно закомментировать определения 
buzzPassive и buzzActive, и весь код, связанный с зуммером не будет скомпилирован, например, пункты Buzz Enable и Buzzer Test не будут отображаться в настройках.
В то же время нельзя одновременно определять buzzPassive и buzzActive, т.к. зуммер может иметь только один тип. Оптимизация под разные варианты сборки системы (бортового компьютера).
Правка условий вывода ошибок #error, исправления; //1.11.22
- v2.9.1 Исправления: оптимизация вывода значка градуса при изменении разрядности температуры, доработки меню настроек, переменную P сделал локальной static,
почистил структуру, применил тернарный оператор в выводе температуры, правка комментариев. //7.11.22 
- v2.9.2 Обновление библиотек CPUTemperature (https://github.com/alexkor433/CPUTemperature) (бывш. CPUtemp) и GetVolt (https://github.com/alexkor433/GetVolt):
оптимизация, в CPUTemperature добавил параметр gain для более точной калибровки, улучшение кода меню настроек: теперь функции constrain вызываются только после изменения
соответствующих параметров (изменили параметр - вызвали constrain), исправил баг - теперь при изменении настройки максимального напряжения оно не устанавливается меньше
верхнего порога минимального (constrain), подправил обработку количества оборотов (RPM) при установке количества цилиндров, другие исправления. //20.11.22
- v2.9.3 Добавил коррекцию яркости светодиода по CRT гамме (кубической параболой); //23.11.22
- v2.9.3.1 Оптимизация работы с таймерами. //28.11.22 
- v2.9.4 Правка записи настроек в EEPROM при выходе из меню, оптимизация обработки ввода параметров (увеличение быстродействия меню), функцию CRT коррекции светодиода
кубической параболой заменил массивом данных с 32 уровнями яркости, исправление бага с расположением значка градуса при температуре больше 100 при включении, применил
switch - case в коде обработки указателей поворота, некоторые функции объявил как inline, мелкие улучшения; //27.01.23
- v2.9.4.1 Изменение логики включения светодиода и пьезоэлемента в настройках, увеличение быстродействия меню, упразднение флага однократного чтения из EEPROM
при входе в меню настроек, изменение очередности параметров в меню, упразднение условия, при котором не производилась запись моточасов при нулевом напряжении:
1. Яркость TM1637;							3. Мин. напряжение;		5. Включение пьезоэлемента;		7. Яркость светодиода;
2. Настройка макс. температуры цилиндров;	4. Макс. напряжение;	6. Тест пьезоэлемента;			8. Обнуление счётчика моточасов; //8.02.23
- v2.9.4.2 Улучшение работы с выбором и записью настроек в меню, ввод макроса switchonanimation для быстрого включения функции анимации при включении БК,
ввод переменной minVMH для правильной записи моточасов при выключении (minVMH = minV - 1.5); //12.02.23
- v2.9.5 Оптимизация: облегчение функции после одинарного и двойного нажатий, ввод структуры с флагами превышения нормальных показателей (макс/мин напряжение, макс температура)
для удобной работы и увеличения скорости обработки, оптимизация функции показа предупреждений (выводим строки только, если не выводили до этого), программа меньше загружена 
проверками, обработка меню производится отдельной функцией, обработка и вывод температуры теперь осуществляется только, если она изменилась, небольшое улучшение в функции обработки 
меню, применены 1-байтные переменные для таймера обновления тахометра (решена проблема с неправильной работой таймера с переменными типа uint8_t), код обработки
светодиода перенесён в блок таймера на millis переключающего переменнную z (мигание текста и светодиода), упразднение переменной ledState, для переменной myTimer4 изменение типа на uint16_t, 
другие улучшения. //17.02.23
- v2.9.5.1 Небольшая оптимизация чтения состояния кнопки enc.held(), обработка датчиков и отрисовка основного экрана вынесена отдельными функциями, все пользовательские
предустановки вынесены в отдельный файл Configuration.h. Это даёт возможность сохранить все настройки для конкретного электронного устройства, а при обновлении просто
заменить файл ino; //23.02.23
- v2.9.5.2 После включения поворота код вывода информации выполняется один раз, добавление настройки частоты пассивной пищалки buzzFrq и I2C адреса LCD1602 lcdAddr. //26.02.23
- v2.9.5.3 Исправлена ошибка, из-за которой после изменения параметров макс./мин. напряжения и макс. температуры соответствующие им предупреждения оставались
на дисплее. //17.04.23
- v2.9.6 Добавлена поддержка светодиода, информирующего об экономичных оборотах двигателя (2200 - 3000), добавлены дефайны ecoRPM и ecoInterval для включения данной
функции и установки границ эко-оборотов, включение функции добавлено в меню настроек, небольшая оптимизация меню настроек, оптимизация приведением типов переменных
в switch case, переработана логика выключения светодиода после активности указателей поворота, добавлены дефайны CRT_VALS и ECO_RPM_VALS (служебные определения) для
определения номеров настроек в массиве vals, исправление других ошибок. //19.05.23
- v2.9.6.1 Исправлено некорректное поведение светодиода ecoInterval, изменены стрелки указателей поворота, улучшен код обработки указателей поворота,
изменено управление основным светодиодом, изменена частота опроса напряжения и вывода RPM на индикатор, другие исправления. //26.05.23 