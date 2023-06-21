## Další možnosti objektově orientovaného programování

Následující text popisuje další pokročilá témata, které většinou není možné během kurzu probrat, můžeš se však k nim kdykoli vrátit a prohloubit svoje znalosti.


### Vlastnosti objektu

U našich obrazců máme implementované metody metody `vypocti_obvod()` a `vypocti_obsah()`. Obvod a obsah jsou hodnoty, které jsou pro nějaký obrazec konkrétní velikosti konstantní. Bylo by tedy zajímavé upravit naše objekty tak, aby se obsah a obrazec tvářily jako atributy. Atribut objektu, pro jehož získání používáme funkci, je v Pythonu označován jako vlastnost (`property`). Vlastnosti označíme pomocí dekorátoru `@property`. U abstraktní třídy pak použijeme speciální dekorátor `@abstractproperty`.

Vlastnosti poté čteme jako atributy, tj. nepoužíváme kulaté závorky jako při volání funkce.

```python
from abc import ABC, abstractproperty

class Obrazec(ABC):
    @abstractproperty
    def obvod():
        pass

    @abstractproperty
    def obsah():
        pass

class Ctverec(Obrazec):
    def __init__(self, a):
        self.a = a

    @property
    def obvod(self):
        return 4 * self.a

    @property
    def obsah(self):
        return self.a * self.a


class Obdelnik(Obrazec):
    def __init__(self, a, b):
        self.a = a
        self.b = b

    @property
    def obvod(self):
        return 2 (self.a + self.b)

    @property
    def obsah(self):
        return self.a * self.b


maly_ctverec = Ctverec(10)
velky_obdelnik = Obdelnik(20, 25)
plocha_celkem = maly_ctverec.obsah + velky_obdelnik.obsah
print(f"Celková plocha obou obrazců je {plocha_celkem}.")
```

### Soukromé a veřejné metody

Soukromé metody jsou metody, které mohou být volány pouze jinými metodami dané třídy, nikoli však zvenku. Python, na rozdíl od jiných programovacích jazyků, skutečně soukromé metody nemá. Všechny metody a atributy tříd jsou veřejné a není žádný způsob jak je opravdu skrýt před vývojářem.

Obecně platí, že atributy nebo metody začínající podtržítkem jsou soukromé a vývojář by je mimo danou třídu neměl číst, upravovat nebo volat. Takové metody nebo atributy se nezobrazí, pokud na třídu zavoláme funkci `help`. Zobrazí se až při bližším zkoumání, například pomocí funkce `dir`. Vývojář třídy tímto odhaluje všechny své karty a dává uživateli do rukou možnost tyto karty taktéž použít, pokud bude potřebovat.

```python
class Zamestnanec:
    def __init__(self, krestni_jmeno, prijmeni):
        self.krestni_jmeno = krestni_jmeno
        self.prijmeni = prijmeni

    @property
    def _delka_jmena(self):
        return len(self.krestni_jmeno + self.prijmeni)

    @property
    def business_card_data(self):
        if self._delka_jmena < 20:
            return f"{self.krestni_jmeno} {self.prijmeni}"
        else:
            return f"{self.krestni_jmeno[0]}. {self.prijmeni}"
```
### Dvojité podtržítko — dunder funkce

`dunder` (double under) jsou funkce začínající a končící dvěma podtržítky. Dvěma z nich je již známé funkce `__init__` pro inicializaci třídy a `__str__` pro převod na řetězec. Mají svůj význam také mimo třídy, například `__file__` pro zjištění cesty, kde se soubor nachází. Jedná se o funkce či atributy, které jsou něčím výjimečné, v Pythonu mají předdefinované chování a Python ví, jak s nimi pracovat.

Několika dunder funkcemi můžeme upravit svou třídu tak, aby se chovala podobně a nebo stejně jako například `list`. Mimo dalších je touto dunder funkcí i  `__len__`, která vrací informaci o délce instance a je zavolána dosazením instance do funkce `len`. Délkou instance se rozumí to, co v daném kontextu dává smysl, pro firmu by mohlo jít o počet zaměstnanců a pro rok by šlo o měsíce.

```python
class Company:
    def __init__(self, Zamestnanecs):
        self.Zamestnanecs = Zamestnanecs

    def __len__(self):
        return len(self.Zamestnanecs)

    def __iter__(self):
        return iter(self.Zamestnanecs)
```

### Dědičnost a dvojité podtržítko

Dvojité podtržení z jedné strany má také svůj význam. Jde o soukromé metody, které navíc zdědí jméno své třídy. Tím dává vývojář třídy najevo, že tato by opravdu za žádných okolností neměla být volána zvenku.

`__join_names` ze třídy `Zamestnanec` se po spuštění pro veřejnost přemění na `_Zamestnanec__join_names` a pro svou instanci zůstane jako `__join_names`. Díky tomuto nedojde v dědící třídě k přejmenování pomocných funkcí, které jsou zásadní pro fungování ostatních funkcí. I tyto funkce se nezobrazí po dosazení třídy nebo instance do napovídající funkce `help`.

```python
class Zamestnanec:
    def __init__(self, krestni_jmeno, prijmeni):
        self.krestni_jmeno = krestni_jmeno
        self.prijmeni = prijmeni

    def __join_names(self):
        return (self.krestni_jmeno + self.prijmeni).lower()

    @property
    def email(self):
        return self.__join_names() + "@goodcompany.com"

class GoodCompanyZamestnanec(Zamestnanec):
    def __join_names(self):
        return self.prijmeni + self.krestni_jmeno

    @property
    def skype(self):
        return self.__join_names()

Zamestnanec = GoodCompanyZamestnanec("Alžběta", "Nováková")

print(Zamestnanec.skype)
print(Zamestnanec.email)
# print(Zamestnanec.__join_names()) # chyba
print(Zamestnanec._GoodCompanyZamestnanec__join_names()))
```
