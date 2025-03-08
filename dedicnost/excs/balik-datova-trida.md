---
title: Balík jako datová třída
demand: 2
---

Uprav třídu `Package` na datovou třídu. Třída bude mít atributy `address`, `weight`, a `state`. U každého z atributů vymysli a nastav vhodný datový typ. Existující metody ve třídě ponech. 

Následně vyzkoušej, zda funguje vytváření balíků. A co cenné balíky, fungují pořád, i když dědí od datové třídy?

:::solution
```py
from dataclasses import dataclass


@dataclass
class Package:
    address: str
    weight: float
    state: str

    def __str__(self):
        return f"Balík na adresu {self.address} má hmotnost {self.weight} kg a je ve stavu {self.state}."

    def delivery_price(self):
        if self.weight < 10:
            return 129
        elif self.weight < 20:
            return 159
        else:
            return 359
        
package = Package("Godrikův důl 47", 1.9, "nedoručen")
print(package)
print(package.delivery_price())
```
:::
