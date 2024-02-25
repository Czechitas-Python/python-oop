---
title: Audioknihy
demand: 4
---

V některých případech je nutné sáhnout k úpravám již třídy. Uvažujme například například nakladatelství, pro které jsme vytvořili třídu `Book` v minulé lekci. Třída měla atributy `title`, `pages` and `price`. Nyní uvažujeme, že se nakladatelství rozhodlo vydávat i audioknihy. Ty nemají počet stránek, ale musíme u nich evidovat herce nebo herečku, který/která audioknihu předčítá. Budeme tedy chtít vytvořit třídu `AudioBook`, ale ta by neměla přímo dědit od třídy `Book`, protože by nám tam zbyl nepotřebný atribut `pages`. Musíme tedy prové úpravu již existujícího kódu. Takové úpravě se někdy říká *refaktorizace*.

Vytvoř třídu `Item`, což je obecná položka, kterou bude nakladatelství prodávat. Třída `Item` bude mít atributy `title` a `price`. Uprav třídu `Book` tak, aby dědila od třídy `Item`. Třída `Book` bude mít navíc atribut `pages`. Atributy `titel` a `price` nastav s využitím metody `__init__` rodičovské třídy `Item`. Dále přidej třídu `AudioBook`, která bude mít navíc atributy `duration_in_hours` (délka nahrávky v hodinách) a `narrator` (člověk, který knihu čte). Třída `AudioBook` bude opět dědit od třídy `Item` a atributy `titel` a `price` bude nastavovat s využitím metody `__init__` rodičovské třídy `Item`.

Třída `Book` si zachová svoji metodu `get_time_to_read()`, která pracuje s počtem stran (`pages`). Třída `AudioBook` bude mít metodu `get_time_to_read()` taky a při jejím zavolání bude vracet hodnotu atributu `duration_in_hours`. Pokud mají metodu všichni potomci, je běžné metodu přidat i rodičovské třídě. Přidej tedy metodu `get_time_to_read()` třídě `Item`. Do metody vlož klíčové slovo `pass`, protože pro třídu `Item` nebudeme do metody vkládat žádný výpočet.

Vytvoř objekty reprezentující audiokihu Problém tří těles (délka 14.4, čte Zbyšek Horák, cena 299 Kč) a knihu Kadet Hornblower (242 stran, cena 399 Kč). Uvažuj, že nakladatelství přidá do e-shopu funkci, která vrátí celkový čas, kdy si bude moci zákazník nebo zákaznice užívat nakoupené produkty. Vytvoř tedy proměnnou `total_time`, která bude obsahovat součet délky audioknihy a času potřebného na přečtení knihy. Obojí zjisti s využitím metody `get_time_to_read()`.
