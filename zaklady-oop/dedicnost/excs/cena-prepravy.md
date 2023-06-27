---
title: Cena přepravy
demand: 3
---

Pokračuj ve své práci pro zásilkovou společnost. Společnost nově požaduje, aby náš software uměl dopočítat cenu přepravy balíku.

- Do třídy `Package` přidej metodu `get_costs()`. Vypočítej přepravu na základě hmotnosti. Přeprava balíku do 2 kg stojí 150 Kč, balíků mezi 2 a 5 kg 190 Kč a těžších balíků 220 Kč. Zkontroluj, zda metoda funguje i pro cenné balíky.
- U cenných balíků bude k ceně připočtení pojištění. Přidej ke třídě `ValuablePackage` metodu `get_costs()`. Ta spočítá cenu přepravy s využitím metody mateřské třídy `Package`. K tomu připočte pojistné ve výši 5 % ceny balíku.
