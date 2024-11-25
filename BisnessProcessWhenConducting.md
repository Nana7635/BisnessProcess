# BisnessProcess
```
Процедура ПриВыполнении(Отказ)
	СсылкаНаДокумент=БизнесПроцессы.СогласованиеДокумента.НайтиПоНомеру(БизнесПроцесс.Номер).СсылкаНаДокумент;
	Если Выполнена=Истина Тогда
		Документ=Документы.ЗаявкаНаРасход.НайтиПоНомеру(СсылкаНаДокумент.Номер).ПолучитьОбъект();
		Документ.СтатусДокумента=Перечисления.СтатусыДокументов.Согласован;
		Документ.Записать(РежимЗаписиДокумента.Проведение);              
		
		ДокументПланированияРасхода=Документы.ПланированиеРасхода.СоздатьДокумент();
		ДокументПланированияРасхода.Дата=ТекущаяДата();
		ДокументПланированияРасхода.ЗаявкаНаРасход=Документ.Ссылка;
		ДокументПланированияРасхода.Контрагент=Документ.Контрагент;
		ДокументПланированияРасхода.Договор=Документ.Договор;
		ДокументПланированияРасхода.СуммаРасхода=Документ.СуммаРасхода;
		ДокументПланированияРасхода.ДатаРасхода=Документ.ДатаРасхода;
		ДокументПланированияРасхода.СтатьяРасходаДС=Документ.СтатьяРасходаДС;
		ДокументПланированияРасхода.Ответственный=Документ.Ответственный;

		Сообщение = Новый СообщениеПользователю;
		Сообщение.Текст = "Документ согласован"; 
		Сообщение.Сообщить(); 	
	КонецЕсли;
КонецПроцедуры
```