---
title: Auta a balíky
demand: 2
---

U našich balíků budeme nově evidovat, který řidič(ka) balík doručuje. Díky tomu pak bude možné odeslat SMS zprávu s číslem řidiče (řidičky), aby mohli zákazníci v případě potřeby řidiče (řidičku) kontaktovat.

Vytvoř třídu `Driver`, která bude mít atributy `name` a `phone_number`. Dále uprav třídu `Package`. Třída bude mít nově atribut `driver`, ve kterém bude uložen(a) řidič(ka) doručující balík. Uprav i třídu `ValuablePackage`, aby v metodě `__init__()` předala hodnotu parametru `driver` metodě `__init__` rodičovské třídy. Přidej třídě `Package` metodu `send_message()`, která odešle zprávu s textem: "Dnes budeme doručovat váš balík. V případě potřeby kontaktujte řidiče na čísle: " Na konec zprávy doplň telefonní číslo.
