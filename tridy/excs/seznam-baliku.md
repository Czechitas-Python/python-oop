---
title: Seznam balíků
demand: 3
---

Přepravní společnost musí rozdělovat balíky do jednotlivých aut. Při plánování dopravy je potřeba hlídat, zda pro jeden automobil není naplánována přeprava příliš velkého množství balíků. Vytvoř tedy tři objekty třídy `Package`. Dále vytvoř seznam `package_list`, do kterého vlož vytvořené objekty. Příklad objektů a seznamu je níže.

```py
package_1 = Package("Grimmauldovo náměstí 11", 15, "nedoručen")
package_2 = Package("Godrikův důl 47", 3, "nedoručen")
package_3 = Package("Vydrník svatého Drába 13", 0.5, "nedoručen")
package_list = [package_1, package_2, package_3]
```

- Vytvoř si proměnnou `total_weight`, do které si s využitím cyklu budeš ukládat celkovou hmotnost všech balíků. Na začátku bude mít hodnotu 0.
- Vytvoř cyklus, který projde seznam `package_list`.
- Pro každý balík přičti jeho hmotnost k proměnné `total_weight`.
- Na konci programu vypiš, jaká je celková hmotnost všech balíků.

Zatím jsme uvažovali, že třídu `Package` využívá ve svém programu přepravní společnost. Stejnou třídu by ale mohl používat e-shop, který takto eviduje zboží odeslané zákazníkům. Provozovatele e-shopu bude určitě zajímat, kolik celkem zaplatí přepravní společnosti za přepravu balíku. Využij tedy balíky v seznamu `package_list` a spočítej celkové náklady na jejich přepravu. Náklady na přepravu jednoho balíku zjistíš voláním metody `delivery_price()`.
