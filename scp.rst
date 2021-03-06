.. _sphinx-chapter:
   
.. meta::
    :description: 1С: Предприятие SSH SFTP SCP
    :keywords: 1С, Предприятие, SSH, SFTP, SCP

.. meta::
    :http-equiv=Content-Type: text/html; charset=utf-8

=======================================
SCP
=======================================

Создание объекта в 1С
---------------------------

.. index:: Подключиться
.. function:: Подключиться()

    Синоним: Connect()
    Функция выполняет подключение к серверу по проколу SSH. Происходит установка TCP соединения.

Пример использования:

.. code-block:: bsl
   :linenos:

    ПутьКомпоненты = "ОбщийМакет.МакетКомпонента";
		
    Если НЕ ПодключитьВнешнююКомпоненту(ПутьКомпоненты,"SSH", ТипВнешнейКомпоненты.Native) Тогда
        ВызватьИсключение "Ошибка подключения внешней компоненты";
    КонецЕсли;

    Компонента = Новый("AddIn.SSH.SSH");	

    ТаблицаОшибок = ПолучитьТаблицуОшибокКомпоненты(Компонента);
        
    Попытка
        КодВозврата = Компонента.Подключиться();
    Исключение
        ВызватьИсключение ОписаниеОшибки() + ": " + Компонента.ОписаниеОшибки();
    КонецПопытки;

    Если СообщеноОбОшибке(КодВозврата) Тогда
        Возврат;
    КонецЕсли;

    Попытка
        КодВозврата = Компонента.Подключиться();
    Исключение
        ВызватьИсключение ОписаниеОшибки() + ": " + Компонента.ОписаниеОшибки();
    КонецПопытки;

    Если СообщеноОбОшибке(КодВозврата) Тогда
        Возврат;
    КонецЕсли;



    

