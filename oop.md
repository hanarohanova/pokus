# Objektově orientované programování

## Důvody vzniku OOP, základní pojmy: třída, objekt, využití OOP v praxi

### Vznik objektově orientovaného programování

Procedurální programování, které řeší problémy postupným vykonáváním posloupnosti instrukcí, se ukázalo být nedostatečné pro vývoj rozsáhlých a složitých aplikací. S rostoucí velikostí programů se objevily zásadní problémy:

- **Obtížná údržba** – "spaghetti" kód s mnohými vzájemnými vazbami a globálními proměnnými se stává nepřehledným a nebezpečným na úpravy.
- **Opakování kódu** – stejné postupy se často píší znovu místo jejich opakovaného využití.
- **Špatná organizace** – chybí jasná struktura a logická hierarchie v programu.
- **Náchylnost na chyby** – změny v jedné části kódu neočekávaně ovlivňují jiné části.

Tyto problémy vedly v 70. a 80. letech 20. století ke vzniku **objektově orientovaného programování (OOP)**, které nabízí fundamentálně odlišný přístup: místo soustředění se na procedury a datové struktury se program modeluje pomocí **objektů**, které kombinují data a operace nad nimi v jeden celek.

### Základní pojmy OOP

**Třída** je abstraktní předpis (šablona, plán) definující, jaké vlastnosti a chování mají objekty daného typu. 

Třída určuje:

- jaké **atributy** (data, vlastnosti) budou objekty obsahovat,
- jaké **metody** (operace, chování) budou objekty vykonávat.

Třída sama o sobě není entita existující v paměti, je pouze **definicí**.

**Objekt** je konkrétní **instance třídy** vzniklá v paměti počítače. Objekt obsahuje skutečné hodnoty atributů a může vykonávat metody definované v třídě. Stejně jako lze mít mnoho instancí stejného programu spuštěno současně, lze vytvořit z jedné třídy mnoho objektů.

> Příklad z reálného světa:
>
> - třída `Automobil` by mohla definovat atributy jako `barva`, `rychlost`, `množství_paliva` a metody jako `akcelerace()`, `brzdění()`, `doplnění_paliva()`,
> - konkrétní automobil značky Škoda Octavia s červenou barvou a plnou nádrží by byl objektem třídy `Automobil`.

### Využití OOP v praxi

Objektově orientované programování se uplatňuje v mnoha oblastech:

- **Desktopové a webové aplikace** – objekty reprezentují prvky uživatelského rozhraní, formuláře, data z databází.
- **Počítačové hry** – objekty reprezentují postavy, předměty, nepřátele, prostředí; jejich interakce se řídí zapsaným chováním.
- **Simulace a vědecké výpočty** – objekty modelují fyzické entity a jejich interakce.
- **Informační systémy** – objekty reprezentují záznamy o zákaznících, výrobcích, transakcích.
- **Grafika a vizualizace** – objekty reprezentují geometrické tvary, kameru, osvětlení.

OOP je převažujícím paradigmatem v moderním softwarovém inženýrství, neboť přináší lepší organizaci, bezpečnost a znovupoužitelnost kódu.

---

## Deklarace třídy, atributy a metody, konstruktor a destruktor, typy metod a atributů, princip zapouzdření

### Struktura třídy

**Třída** jako základní stavební jednotka OOP obsahuje několik klíčových prvků:

- **atributy** (data) – proměnné uchovávající stav objektu,
- **metody** (funkce) – procedury provádějící operace nad daty,
- **konstruktor** – speciální metoda volaná při vytváření objektu,
- **destruktor** – speciální metoda volaná při zrušení objektu.

Příklad deklarace třídy v C++:

```cpp
class Osoba {
private:
    int vek;           // Privátní atribut
    string jmeno;      // Privátní atribut

public:
    // Konstruktor
    Osoba(string j, int v) {
        jmeno = j;
        vek = v;
    }

    // Metoda
    void predstaveni() {
        cout << "Jmenuju se " << jmeno << ", je mi " << vek << " let." << endl;
    }

    // Destruktor
    ~Osoba() {
        cout << "Osoba " << jmeno << " je zrusena." << endl;
    }
};
```

Příklad deklarace třídy v Pythonu:

```python
class Osoba:
    def __init__(self, jmeno, vek):  # Konstruktor
        self.jmeno = jmeno
        self.vek = vek

    def predstaveni(self):  # Metoda
        print(f"Jmenuju se {self.jmeno}, je mi {self.vek} let.")

    def __del__(self):  # Destruktor
        print(f"Osoba {self.jmeno} je zrusena.")
```

### Atributy a metody

**Atributy** jsou proměnné, které uchovávají data objektu. Každý objekt má svou vlastní sadu hodnot atributů.

**Metody** jsou funkce definované v třídě, které mohou pracovat s atributy objektu a provádět operace. Při volání metody musíme metodu volat na konkrétním objektu.

Příklad v C++:

```cpp
Osoba osoba("Alice", 25);
osoba.predstaveni();  // Volání metody na objektu
cout << osoba.vek;  // Přístup k atributu
```

Příklad v Pythonu:

```python
osoba = Osoba("Alice", 25)
osoba.predstaveni()  # Volání metody na objektu
print(osoba.vek)     # Přístup k atributu
```

### Konstruktor a destruktor

**Konstruktor** je speciální metoda, která se automaticky volá ve chvíli, kdy je objekt vytvářen. Slouží k inicializaci atributů objektu.

- V C++ má konstruktor stejné jméno jako třída a nemá návratový typ,
- v Pythonu je to metoda pojmenovaná `__init__`.

Konstruktor přijímá parametry, které určují počáteční hodnoty atributů:

Příklad volání konstruktoru v C++:

```cpp
Osoba osoba("Bob", 30);  // Volání konstruktoru
```

Příklad volání konstruktoru v Pythonu:

```python
osoba = Osoba("Bob", 30)  # Volání konstruktoru
```

**Destruktor** je speciální metoda volaná, když se objekt maže z paměti. Slouží k uvolnění prostředků (soubory, paměť) a čistění před zničením objektu.

- V C++ je destruktor pojmenován vlnkou `~` před jménem třídy,
- v Pythonu je to metoda `__del__`. Je však méně používaný, protože Python má automatickou správu paměti.

Příklad destruktoru v C++:

```cpp
~Osoba() {
    // Uvolnění prostředků
}
```

Příklad destruktoru v Pythonu:

```python
def __del__(self):
    # Uvolnění prostředků
    pass
```

### Instanční a třídní prvky

**Instanční atributy a metody** patří konkrétnímu objektu. Každá instance má vlastní hodnoty instančních atributů.

```cpp
class Ucet {
private:
    double zustatek;  // Instanční atribut
};
```

Objekty se vytvářejí instancování třídy:

```cpp
Ucet ucet1(1000);  // První instance s zůstatkem 1000
Ucet ucet2(500);   // Druhá instance s zůstatkem 500
```

**Třídní (statické) prvky** jsou sdíleny všemi instancemi třídy. Existují pouze jednou, bez ohledu na počet vytvořených objektů.

Příklad v C++:

```cpp
class Ucet {
private:
    double zustatek;
    static int pocet_uctu;  // Třídní atribut

public:
    Ucet(double z) : zustatek(z) {
        pocet_uctu++;  // Počet účtů se zvýší
    }

    static int getPocetUctu() {  // Třídní metoda
        return pocet_uctu;
    }
};

int Ucet::pocet_uctu = 0;  // Inicializace třídního atributu
```

Příklad v Pythonu:

```python
class Ucet:
    pocet_uctu = 0  # Třídní atribut

    def __init__(self, zustatek):
        self.zustatek = zustatek
        Ucet.pocet_uctu += 1

    @classmethod
    def get_pocet_uctu(cls):  # Třídní metoda
        return cls.pocet_uctu
```

### Princip zapouzdření

**Zapouzdření** (encapsulation) je princip skrývání interního stavu objektu a řízení přístupu k němu. Objekty poskytují veřejné rozhraní (veřejné metody), zatímco interní implementace zůstává skryta.

> Příklady: 
>
> Bankovní účet by měl skrýt svůj zůstatek a umožnit přístup pouze prostřednictvím metod pro vklad, výběr a kontrolu zůstatku.
>
> Automobil by měl skrýt své vnitřní mechanismy a umožnit ovládání pouze přes metody jako `start()`, `stop()`, `accelerate()`.

Zapouzdření zajišťuje:

- **Bezpečnost** – data nelze nechtěně změnit přímým přístupem.
- **Kontrolu** – všechny změny dat procházejí skrze metody, které mohou ověřit validitu.
- **Flexibilitu** – interní reprezentaci lze změnit bez ovlivnění zbytku programu.

Jazyk C++ poskytuje tři úrovně viditelnosti:

- `public` – přístupné zvenčí,
- `protected` – přístupné jen z třídy a jejích potomků,
- `private` – přístupné pouze z třídy samotné.

Privátní atributy a metody jsou přístupné pouze z metod třídy, což umožňuje skrýt vnitřní stav objektu.

Přístupové metody se obvykle nazývají **gettery** (slouží k získání hodnoty) a **settery** (slouží k nastavení hodnoty) a umožňují kontrolovat přístup k atributům.

Příkladem getteru a setteru v C++:

```cpp
class Auto {
private:
    int rychlost;   
public:
    int getRychlost() {  // Getter
        return rychlost;
    }
    void setRychlost(int r) {  // Setter
        if (r >= 0) {
            rychlost = r;
        }
    }   
```

V Pythonu není zapouzdření striktně vynuceno, ale konvenčně se private prvky označují podtržítkem:

```python
class Auto:
    def __init__(self, rychlost):
        self._rychlost = rychlost  # Konvenčně privátní

    def get_rychlost(self):  # Getter
        return self._rychlost

    def set_rychlost(self, r):  # Setter
        if r >= 0:
            self._rychlost = r  
```

Modernějším přístupem v Pythonu je použití **dekorátorů** `@property` pro vytvoření getterů a setterů:

```python
class Auto:
    def __init__(self, rychlost):
        self._rychlost = rychlost

    @property
    def rychlost(self):  # Getter
        return self._rychlost

    @rychlost.setter
    def rychlost(self, r):  # Setter
        if r >= 0:
            self._rychlost = r
```

Zapouzdření je jedním z pilířů OOP a umožňuje vytváření robustních a bezpečných aplikací.

---

## Dědičnost a polymorfismus, významnost opětovného použití kódu, příklady implementace v různých jazycích

### Princip dědičnosti

**Dědičnost** je mechanismus, kterým nová třída (odvozená třída, potomek) zdědí vlastnosti a chování z již existující třídy (základní třída, rodič).

Dědičnost umožňuje vytvářet hierarchie tříd a znovu používat kód.

**Základní třída (rodičovská třída)** obsahuje obecné vlastnosti a metody, které jsou společné pro skupinu objektů.

**Odvozená třída** zdědí všechny veřejné a chráněné prvky základní třídy a může je rozšířit novými atributy a metodami.

> Příklady z reálného světa:
>
> `Zvíře` je rodičovská třída, `Pes` nebo `Kočka` jsou odvozené třídy (potomci).
>
> `Auto` je rodičovská třída, `OsobníAuto` nebo `NákladníAuto` jsou odvozené třídy (potomci).

Při dědičnosti může odvozená třída přidat nové metody a atributy, které nejsou v základní třídě, a také může **překrýt** (*override*) metody základní třídy, aby poskytla specifické chování.

Příklad v C++:

```cpp
// Základní třída (rodičovská třída)
class Zvire {
protected:
    string jmeno;

public:
    Zvire(string j) : jmeno(j) {}

    void zvuk() {
        cout << jmeno << " vydava zvuk." << endl;
    }
};

// Odvozená třída (potomek)
class Pes : public Zvire {
public:
    Pes(string j) : Zvire(j) {}

    void zvuk() {  // Překrytí metody
        cout << jmeno << " štěká." << endl;
    }
};
```

Příklad v Pythonu:

```python
# Základní třída (rodičovská třída)
class Zvire:
    def __init__(self, jmeno):
        self.jmeno = jmeno

    def zvuk(self):
        print(f"{self.jmeno} vydava zvuk.")

# Odvozená třída (potomek)
class Pes(Zvire):  # Dědí z Zvire
    def zvuk(self):  # Překrytí metody
        print(f"{self.jmeno} štěká.")
```

V obou příkladech `Pes` dědí z `Zvire` a přepisuje metodu `zvuk()`, aby poskytla specifické chování pro psy.

> V některých jazycích je možné dědit z více tříd (vícenásobná dědičnost), což umožňuje kombinovat chování z různých zdrojů, ale může také vést k problémům s konflikty metod (např. v C++).

### Polymorfismus a přetěžování metod

**Polymorfismus** (mnohočetnost forem) umožňuje objektům různých typů reagovat na stejný příkaz různě. Stejné volání metody se chová odlišně v závislosti na typu objektu.

> Příklady z reálného světa:
>
> Když řeknete "zvuk", pes může štěkat, kočka může mňoukat, a pták může zpívat. Všechny tyto objekty reagují na stejnou metodu `zvuk()`, ale chovají se odlišně.

Příklad v C++:

```cpp
Zvire* zvire1 = new Zvire("Zvíře");
Zvire* zvire2 = new Pes("Rex");
zvire1->zvuk();  // Výstup: Zvíře vydava zvuk.
zvire2->zvuk();  // Výstup: Rex štěká.
delete zvire1;
delete zvire2;  
```

Příklad v Pythonu:

```python
zvire1 = Zvire("Zvíře")
zvire2 = Pes("Rex")

zvire1.zvuk()  # Výstup: Zvíře vydava zvuk.
zvire2.zvuk()  # Výstup: Rex štěká.
```

Ačkoliv se obě volání jmenují `zvuk()`, chování se liší – to je polymorfismus.

**Přetěžování metod** znamená, že metoda se stejným jménem může v jedné třídě existovat s různými parametry (různými typy nebo počtem argumentů). Přetěžování umožňuje definovat více verzí stejné metody pro různé situace.

Příklad v C++:

```cpp
class Kalkulator {
public:
    int secti(int a, int b) {
        return a + b;
    }

    double secti(double a, double b) {  // Přetěžování
        return a + b;
    }
};
```

Příklad volání přetížených metod:

```cpp
Kalkulator k;
cout << k.secti(3, 4);        // Volá int verzi
cout << k.secti(3.5, 4.2);  // Volá double verzi
```

V Pythonu není přetěžování metod podporováno jako v jazyce C++, ale lze jej simulovat pomocí výchozích parametrů nebo proměnného počtu argumentů:

```python
class Kalkulator:
    def secti(self, a, b=None, c=None):
        if c is not None:
            return a + b + c
        elif b is not None:
            return a + b
        else:
            return a
```

### Opětovné použití kódu

Dědičnost a polymorfismus umožňují výrazně snížit opakování kódu:

- **společný kód se napíše jednou** v základní třídě,
- **odvozené třídy jej zdědí** a nemusí jej psát znovu,
- **specializace se provádí překrytím** metod.

Tento přístup vede k:

- **menšímu množství kódu**,
- **snadnější údržbě** – změna v základní třídě se automaticky promítne do všech potomků,
- **lepší organizaci** – třídy jsou logicky hierarchicky uspořádány.

Příklad hierarchie tříd v OOP:

```
Vozidlo (základní třída)
├── Auto
   ├──  OsobníAuto
   ├──  NákladníAuto
├── Motocykl
```

Všechny třídy mohou dědit například metodu `urychlit()` z `Vozidla`, ale každá ji může implementovat jinak.

---

## Vytváření objektů, možnosti práce s objekty a s pamětí v různých jazycích

### Vznik objektu v paměti

Když se vytváří objekt, dochází k několika procesům:

1. **přidělení paměti** – operační systém přidělí potřebné místo v paměti,
2. **inicializace** – konstruktor inicializuje atributy objektu,
3. **reference** – objekt je dostupný skrze proměnnou (referenci nebo ukazatel).

V C++ se objekt vytváří dvěma způsoby:

```cpp
// Vytvoření na zásobníku (stack)
Osoba osoba1("Alice", 25);

// Vytvoření na haldě (heap) – vyžaduje ukazatel
Osoba *osoba2 = new Osoba("Bob", 30);
```

Objekt na zásobníku se automaticky zruší, když opustí svůj obor platnosti.

Objekt na haldě zůstává, dokud není explicitně zrušen pomocí `delete`:

```cpp
delete osoba2;  // Uvolnění paměti
```

> Rozdíl mezi stackem (zásobník) a heapem (halda):
>
> - **Stack** – rychlejší, ale omezený velikostí a životností (objekt existuje pouze v rámci bloku kódu),
> - **Heap** – pomalejší, ale flexibilnější (objekt může existovat, dokud není explicitně zrušen).

V Pythonu se objekty vždy vytváření na haldě a proměnné jsou pouze odkazy na tyto objekty:

```python
osoba1 = Osoba("Alice", 25)  # Automaticky na haldě
osoba2 = Osoba("Bob", 30)
```

Díky automatické správě paměti v Pythonu se programátor nemusí starat o přidělování a uvolňování paměti.

### Hodnota vs. reference

V C++ rozlišujeme:

- **hodnotový přístup** – proměnná obsahuje přímo hodnotu objektu, kopíruje se celý obsah,
- **referenční přístup** – proměnná obsahuje adresu objektu v paměti, nekopíruje se.

Příklad:

```cpp
Osoba osoba1("Alice", 25);
Osoba osoba2 = osoba1;  // Hodnotový přístup – kopie
osoba2.jmeno = "Alice2";  // osoba1 se nezmění

Osoba *ptr1 = &osoba1;  // Referenční přístup – adresa objektu, ptr1 ukazuje na osoba1
Osoba *ptr2 = ptr1;     // ptr2 ukazuje na stejný objekt jako ptr1
ptr2->jmeno = "Alice3";  // osoba1 se změní, protože ptr1 a ptr2 ukazují na stejný objekt
```

V Pythonu jsou všechny objekty referenční (vždy se předává odkaz):

```python
osoba1 = Osoba("Alice", 25)
osoba2 = osoba1  # Odkaz na stejný objekt
osoba2.jmeno = "Alice2"  # osoba1 se také změní
```

### Správa paměti

**C++ – Explicitní správa**

V C++ programátor sám odpovídá za přidělení a uvolnění paměti. Objekty na haldě se vytváří pomocí `new` a ruší pomocí `delete`:

```cpp
Osoba *osoba = new Osoba("Alice", 25);
// Použití objektu
delete osoba;  // Manuální uvolnění
```

Zapomenutí `delete` vede k **úniku paměti** (*memory leak*), kdy paměť zůstává obsazena zbytečně.

K automatizaci správy paměti se v moderním C++ používají **inteligentní ukazatele**:

```cpp
std::unique_ptr<Osoba> osoba(new Osoba("Alice", 25));
// Paměť se automaticky uvolní, když unique_ptr opustí obor
```

**Python – Automatická správa**

Python automaticky spravuje paměť pomocí **garbage collectoru**, který sleduje, které objekty jsou ještě používány. Jakmile se objekt přestane používat, je automaticky odstraněn:

```python
osoba = Osoba("Alice", 25)
# Python automaticky uvolní paměť, když osoba už není potřeba
```

Programátor se nemusí starat o `delete` či `free`.

### Zrušení objektu a destruktor

Destruktor se volá automaticky, když se objekt maže. V C++ se volá při `delete` nebo když objekt opustí obor:

```cpp
{
    Osoba osoba("Alice", 25);
    // destruktor se volá na konci bloku
}
```

V Pythonu se destruktor volá, když garbage collector detekuje, že objekt není už nikde referován. Je však důležité poznamenat, že v Pythonu není zaručeno, kdy přesně se destruktor `__del__` zavolá, protože závisí na implementaci garbage collectoru.

---

## Další aplikace principů OOP: abstraktní třídy, rozhraní

### Abstraktní třídy

**Abstraktní třída** je třída, kterou nelze bezprostředně instancovat. Slouží jako šablona pro odvozené třídy a definuje společné rozhraní.

> Příklady z reálného světa:
>
> `Zvíře` může být abstraktní třída, protože nemůžeme mít konkrétní zvíře bez specifikace druhu. Místo toho můžeme mít odvozené třídy jako `Pes`, `Kočka`, které implementují konkrétní chování.
>
> `Vozidlo` může být abstraktní třída, protože nemůžeme mít konkrétní vozidlo bez specifikace typu. Místo toho můžeme mít odvozené třídy jako `Auto`, `Motocykl`, které implementují konkrétní chování.

Abstraktní třída obsahuje **abstraktní metody** – metody bez implementace, které musí být implementovány v odvozených třídách.

Příklad v C++:

```cpp
class Zvire {  // Abstraktní třída
public:
    virtual void zvuk() = 0;  // Čistě virtuální – abstraktní metoda
    virtual ~Zvire() {}
};

class Pes : public Zvire {
public:
    void zvuk() {  // Povinná implementace
        cout << "Štěkání" << endl;
    }
};

// Zvire z;  // Chyba – nelze instancovat
Pes p;  // OK
```

Příklad v Pythonu s použitím modulu `abc`:

```python
from abc import ABC, abstractmethod

class Zvire(ABC):  # Abstraktní třída
    @abstractmethod
    def zvuk(self):  # Abstraktní metoda
        pass

# z = Zvire()  # Chyba
class Pes(Zvire):
    def zvuk(self):  # Povinná implementace
        print("Štěkání")
```

V obou příkladech `Zvire` je abstraktní třída, která definuje abstraktní metodu `zvuk()`. Odvozená třída `Pes` musí tuto metodu implementovat, jinak by také byla abstraktní.

Abstraktní třídy vynucují, aby všechny odvozené třídy implementovaly určitá chování.

### Rozhraní (Interface)

**Rozhraní** definuje sadu metod, které třídy musí implementovat. 

> Příklady z reálného světa:
>
> `Pohyblivý` může být rozhraní, které definuje metody jako `pohni_se()`, `zastav()`. Různé třídy jako `Auto`, `Pes`, `Robot` mohou implementovat toto rozhraní a poskytovat vlastní implementaci těchto metod. Rozhraní tak umožňuje různým třídám sdílet společné chování, aniž by musely být ve stejné hierarchii dědičnosti.

V C++ se rozhraní simuluje pomocí abstraktní třídy obsahující pouze abstraktní metody:

```cpp
class Vozidlo {  // Rozhraní
public:
    virtual void urychlit() = 0;
    virtual void zastavit() = 0;
    virtual ~Vozidlo() {}
};

class Auto : public Vozidlo {
public:
    void urychlit() { cout << "Auto akceleruje." << endl; }
    void zastavit() { cout << "Auto brzdí." << endl; }
};
```

V Pythonu se používá abstraktní třída s metodami:

```python
from abc import ABC, abstractmethod

class Vozidlo(ABC):
    @abstractmethod
    def urychlit(self):
        pass

    @abstractmethod
    def zastavit(self):
        pass

class Auto(Vozidlo):
    def urychlit(self):
        print("Auto akceleruje.")

    def zastavit(self):
        print("Auto brzdí.")
```

Rozhraní zajišťují, že různé třídy disponují jednotným chováním.
