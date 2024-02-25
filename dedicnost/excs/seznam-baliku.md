---
title: Celková hodnota balíků
demand: 3
---

Pokračuj ve své práci pro zásilkovou společnost. Společnost chce doplnit do aplikace funkci pro výpočet celkového hodnoty nákladu nějakého auta, aby pak (např. v případě nehody nebo krádeže) mohla snadno spočítat celkovou hodnotu cenných balíků v autě a předat informaci pojišťovně. Příklad je podobný bonusu na výpočet celkové hmotnosti z předchozí části, liší se ale v tom, že hodnotu mají pouze cenné balíky, zatímco hmotnost mají všechny balíky.

Níže je příklad balíků, které můžeš použít pro tvorbu svého programu.

```py
package_1 = ValuablePackage("Grimmauldovo náměstí 11", 1.9, "nedoručen", 5500)
package_2 = Package("Godrikův důl 47", 1.9, "nedoručen")
package_3 = ValuablePackage("Vydrník svatého Drába 13", 1.9, "nedoručen", 5500)
package_list = [package_1, package_2, package_3]
```

- Vytvoř si proměnnou `total_value`, do které si s využitím cyklu budeš ukládat celkovou hodnotu všech balíků. Na začátku bude mít hodnotu 0.
- Vytvoř cyklus, který projde seznam `package_list`.
- Vyber funkci, která je podle tebe nejvhodnější pro zajištění bezpečného čtení atributu `value`. Můžeš použít funkci `isinstance()`, `hasattr()` i `getattr()`. Přičti hodnotu balíku k proměnné `total_value`, aniž by program skončil chybou u objektu `package_2`.
- Na konci programu vypiš, jaká je celková hodnota balíků v autě.
