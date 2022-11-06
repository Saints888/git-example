# git-example
TestWork
Дано: таблица WORK в произвольной БД (использование in memory баз данных не рекомендуется), содержащая один столбец целочисленного типа (FIELD).

Необходимо написать консольное приложение на Java, использующее стандартную библиотеку JDK7 (желательно) либо JDK8 и реализующее следующий функционал:

1. Основной класс приложения должен следовать правилам JavaBean, то есть инициализироваться через setter'ы. Параметры инициализации - данные для подключения к БД и число Z. 

2. После запуска, приложение вставляет в WORK Z записей со значениями 1..Z. Если в таблице WORK находились записи, то они удаляются перед вставкой.

3. Затем приложение запрашивает эти данные из WORK.FIELD и формирует корректный XML-документ вида
<entries>
    <entry>
        <field>значение поля field</field>
    </entry>
    ...
    <entry>
        <field>значение поля field</field>
    </entry>
</entries>
(с Z вложенных элементов <entry>)
Документ сохраняется в файловую систему как "ZED.xml".

4. Посредством XSLT, приложение преобразует содержимое "ZED.xml" к следующему виду:
<entries>
    <entry field="значение поля field">
    ...
    <entry field="значение поля field">
</entries>
(с N вложенных элементов <entry>)
Новый документ сохраняется в файловую систему как "FREE.xml".

5. Приложение парсит "FREE.xml" и выводит арифметическую сумму значений всех атрибутов field в консоль. 

6.	При больших Z (~1000) время работы приложения не должно быть более десяти минут.
7.	Программу нужно реализовать с учетом возможности переиспользования/встраивания в других задачах и проектах.
