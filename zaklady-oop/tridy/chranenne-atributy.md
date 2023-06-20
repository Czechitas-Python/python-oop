## Chráněné atributy

Ve třídě `Employee` jsme přidali způsob, jak mohou zaměstnanci "bezpečně" žádat o dovolenou, aby se nedostali do mínusu. Musíme si však uvědomit, že hodnotu atributů lze v Pythonu měnit přímo.

Můžeme přímo nastavit nějakou hodnotu.

```py
frantisek.holiday_entitlement = 10
```

Stejně tak je možné provést snížení hodnoty.

```py
frantisek.holiday_entitlement = frantisek.holiday_entitlement - 10
```

Většina objektově orientovaných jazyků umožňuje vytvořit tvz. soukromé atributy, které nejde měnit zvenku, ale pouze prostřednictvím method. Autoři jazyk Python se však rozhodli dát vývojářům a vývojářkám svobodu atributy objektu měnit libovolně. Můžeme ale vytvořit tzv. chráněný atribut. Chráněný atribut se vyznačuje tím, že jeho název začíná s podtržítkem. Sice je pořád možné měnit jej přímo, dáváme tím ale jasně najevo, že by se to **dělat nemělo**. Tento přístup funguje v realitě docela dobře, protože dnes je možné dohledat autora (autorku) každého řádku zdrojového kódu, takže si všichni dávají pozor, aby atributy měnili přímo pouze v případech krajní nouze.

```py
class Employee:
    def __init__(self, name, position, holiday_entitlement):
        self.name = name
        self.position = position
        self._holiday_entitlement = holiday_entitlement
    
    def __str__():
        return f"Zaměstnanec {self.name} pracuje na pozici {self.position}."

    def taky_holiday(self, days):
        if self._holiday_entitlement >= days:
            self._holiday_entitlement -= days
            return f"Užij si to."
        else:
            return f"Bohužel už máš nárok jen na {self._holiday_entitlement} dní."

frantisek = Employee("František Novák", "konstruktér", 25)
print(str(frantisek))
```

