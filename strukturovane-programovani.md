# Strukturované programování

## Důvody vzniku strukturovaného programování, zásady a základní rysy

### Vznik strukturovaného programování

V raných dobách programování se programy psaly převážně pomocí **nestrukturovaného kódu**, který obsahoval velké množství příkazů pro bezpodmínečné skoky (například příkaz `GOTO`). Tento způsob programování vedl k vytváření kódu, který byl obtížně čitelný a ještě obtížněji udržovatelný.

S rostoucí složitostí programů se začaly projevovat závažné problémy:

- **Špatná čitelnost** – program se stal obtížně pochopitelný i pro jeho autora po určité době,
- **Náročná údržba** – jakákoliv změna mohla způsobit neočekávané chyby na jiných místech,
- **Složité testování** – bylo téměř nemožné ověřit správnost všech možných průchodů programem,
- **Nízká produktivita** – vývoj a opravy zabíraly nepřiměřeně dlouhou dobu.

Tyto problémy vedly od 60. let 20. století k vývoji konceptu **strukturovaného programování**, který formulovali především *Edsger Dijkstra*, *C. A. R. Hoare* a další informatici. Dijkstra ve svém slavném dopise z roku 1968 s názvem *„Go To Statement Considered Harmful"* (česky „Příkaz GOTO považován za škodlivý") upozornil na nebezpečí nekontrolovaného používání příkazu `GOTO`.

---

### Principy strukturovaného programování

**Strukturované programování** je programovací paradigma, které klade důraz na přehlednost, logickou strukturu a systematický přístup k tvorbě programů. Jeho základním principem je rozklad složitých problémů na menší, lépe zvládnutelné části.

Základní **zásady strukturovaného programování** zahrnují:

- **Sekvence** – příkazy jsou vykonávány postupně jeden za druhým v určeném pořadí,
- **Větvení (selekce)** – program se může rozhodnout mezi různými cestami vykonávání na základě splnění podmínek,
- **Cykly (iterace)** – opakované vykonávání skupiny příkazů, dokud je splněna určitá podmínka,
- **Omezení nebo zákaz příkazu GOTO** – nahrazení bezpodmínečných skoků strukturovanými konstrukcemi.

Strukturované programování dále prosazuje:

- rozklad programu na menší procedury a funkce,
- používání lokálních proměnných s omezenou platností,
- jasné rozhraní mezi částmi programu,
- systematické pojmenování proměnných a funkcí.

Dodržování těchto principů vede k vytváření programů, které jsou:

- **čitelnější** – struktura programu je jasná a logická,
- **udržovatelnější** – změny lze provádět s menším rizikem zavedení chyb,
- **testovatelné** – jednotlivé části lze testovat odděleně,
- **opakovaně použitelné** – dobře navržené funkce lze využít v jiných projektech.

---

## Konstanty, proměnné, datové typy; rozdíly ve způsobu deklarace a použití

### Proměnné a konstanty

**Proměnná** je pojmenované místo v paměti počítače, které uchovává hodnotu, jež se může během běhu programu měnit. Proměnné jsou základním stavebním kamenem téměř každého programu, protože umožňují pracovat s daty a ukládat mezivýsledky výpočtů.

**Konstanta** je podobně jako proměnná pojmenované místo v paměti, ale její hodnota je nastavena při inicializaci a během běhu programu se již nemění. Použití konstant zvyšuje bezpečnost a čitelnost kódu, protože jasně vymezuje hodnoty, které by neměly být měněny.

Rozdíl mezi proměnnou a konstantou:

- proměnná může měnit svou hodnotu během běhu programu,
- konstanta má pevně stanovenou hodnotu, která zůstává neměnná.

---

### Datové typy

**Datový typ** určuje, jaký druh hodnot může proměnná nebo konstanta obsahovat a jaké operace s nimi lze provádět. Datové typy definují:

- rozsah možných hodnot,
- velikost paměti potřebné pro uložení hodnoty,
- operace, které lze s hodnotou provádět.

Základní datové typy zahrnují:

- **Celá čísla** (`int`) – např. `-5`, `0`, `42`,
- **Desetinná čísla** (`float`, `double`) – např. `3.14`, `-0.001`,
- **Znaky** (`char`) – jednotlivé znaky jako `'a'`, `'Z'`, `'5'`,
- **Textové řetězce** (`string`) – posloupnosti znaků jako `"Hello"`, `"Programování"`,
- **Logické hodnoty** (`bool`) – `true` nebo `false`.

---

### Statické vs. dynamické typování

Programovací jazyky se liší v přístupu k deklaraci a typování proměnných:

**Statické typování** – datový typ proměnné musí být explicitně deklarován a nelze jej během běhu programu změnit. Tento přístup používají jazyky jako C, C++, Java nebo C#. Výhodou je lepší kontrola chyb již při překladu programu a často i vyšší výkon.

**Dynamické typování** – datový typ proměnné není explicitně deklarován a může se měnit během běhu programu. Tento přístup používají jazyky jako Python, JavaScript nebo Ruby. Výhodou je rychlejší vývoj a flexibilnější kód, nevýhodou může být menší kontrola chyb a potenciálně pomalejší běh programu.

Příklad deklarace v jazyce C (statické typování):

```c
int vek = 25;              // Celé číslo
float teplota = 36.6;      // Desetinné číslo
char pismeno = 'A';        // Znak
const double PI = 3.14159; // Konstanta
```

Příklad deklarace v jazyce Python (dynamické typování):

```python
vek = 25              # Celé číslo (int)
teplota = 36.6        # Desetinné číslo (float)
pismeno = 'A'         # Řetězec (str) s jedním znakem
PI = 3.14159          # Konstanta (podle konvence velkými písmeny)
```

V jazyce C je nutné při deklaraci proměnné uvést její datový typ (`int`, `float`, `char`), zatímco Python datový typ automaticky odvodí z přiřazené hodnoty. V jazyce C se pro konstanty používá klíčové slovo `const`, v Pythonu se konstanty označují konvenčně velkými písmeny, ale technicky se chovají jako běžné proměnné.

---

## Řídicí struktury a jejich realizace v programovacích jazycích; podmíněné příkazy a cykly

**Řídicí struktury** určují, v jakém pořadí se budou vykonávat jednotlivé příkazy programu. Bez řídicích struktur by program vykonával příkazy pouze sekvenčně jeden za druhým. Řídicí struktury umožňují vytvářet složitější logiku a reagovat na různé situace.

V rámci strukturovaného programování rozlišujeme tři základní typy řídicích struktur:

### **Sekvence**

Sekvence je nejjednodušší řídicí struktura. Příkazy jsou vykonávány postupně v pořadí, v jakém jsou zapsány v kódu.

Příklad v Pythonu:

```python
a = 5
b = 10
c = a + b
print(c)  # Výstup: 15
```

Příklad v jazyce C:

```c
int a = 5;
int b = 10;
int c = a + b;
printf("%d\n", c);  // Výstup: 15
```

### **Větvení (selekce)**

Větvení umožňuje programu rozhodnout se mezi různými cestami vykonávání na základě splnění nebo nesplnění určité podmínky. Základním nástrojem větvení je **podmíněný příkaz**.

**Podmíněný příkaz `if`** vyhodnotí logickou podmínku a na základě jejího výsledku vykoná nebo nevykoná příslušný blok kódu.

Schéma toku řízení pro podmíněný příkaz:

```
        [Podmínka?]
           /    \
        ANO      NE
         /        \
    [Příkazy A]  [Příkazy B]
         \        /
          \      /
         [Pokračování]
```

Obecná struktura:

```
if (podmínka):
    příkazy vykonané, pokud je podmínka splněna
```

**Příkaz `if-else`** umožňuje specifikovat alternativní blok kódu, který se vykoná, pokud podmínka není splněna.

```
if (podmínka):
    příkazy vykonané, pokud je podmínka splněna
else:
    příkazy vykonané, pokud podmínka není splněna
```

**Příkaz `elif/else if`** umožňuje testovat více podmínek postupně.

Příklad v jazyce C:

```c
int vek = 18;

if (vek >= 18) {
    printf("Jste plnoletý\n");
} else {
    printf("Jste mladistvý\n");
}
```


Příklad v Pythonu:

```python
vek = 18

if vek >= 18:
    print("Jste plnoletý")
else:
    print("Jste mladistvý")
```

**Ternární operátor** je zkrácený zápis jednoduchého podmíněného příkazu, který vrací jednu ze dvou hodnot podle splnění podmínky. Používá se především tam, kde je potřeba stručné rozhodnutí v rámci výrazu.

Příklad v Pythonu:

```python
vek = 20
stav = "plnoletý" if vek >= 18 else "mladistvý"
print(stav)
```

Příklad v jazyce C:

```c
int vek = 20;
const char *stav = (vek >= 18) ? "plnoletý" : "mladistvý";
printf("%s\n", stav);
```

**Příkaz `switch`** umožňuje výběr z více větví na základě hodnoty výrazu. Je vhodný tam, kde by bylo potřeba dlouhé řetězení `if-else if`. Větve se obvykle ukončují příkazem `break`, aby nedošlo k nechtěnému průchodu do další větve.

Příklad v jazyce C:

```c
int volba = 2;

switch (volba) {
    case 1:
        printf("První volba\n");
        break;
    case 2:
        printf("Druhá volba\n");
        break;
    default:
        printf("Neznámá volba\n");
}
```

Příklad v Pythonu (od verze 3.10):

```python
volba = 2

match volba:
    case 1:
        print("První volba")
    case 2:
        print("Druhá volba")
    case _:
        print("Neznámá volba")
```

---

### **Cykly (iterace)**

Cykly umožňují opakované vykonávání skupiny příkazů. 

Schéma toku řízení pro cyklus:

```
    [Inicializace]
          |
          v
    [Podmínka?] --NE--> [Konec cyklu]
          |
        ANO
          |
          v
    [Tělo cyklu]
          |
          v
    [Aktualizace]
          |
          +---> (zpět na podmínku)
```

Rozlišujeme dva základní typy cyklů:

**Cyklus `while`** – opakuje blok kódu, dokud je splněna určitá podmínka. Podmínka se testuje před každým průchodem cyklem.

```
while (podmínka):
    příkazy opakované, dokud je podmínka splněna
```

Příklad v jazyce C:

```c
int i = 0;
while (i < 5) {
    printf("%d\n", i);
    i++;
}
// Výstup: 0, 1, 2, 3, 4
```

Příklad v Pythonu:

```python
i = 0
while i < 5:
    print(i)
    i += 1
# Výstup: 0, 1, 2, 3, 4
```

**Cyklus `do...while`** – podmínka se testuje až po vykonání těla cyklu, takže tělo proběhne vždy alespoň jednou. Tento typ cyklu je standardní v jazyce C, v Pythonu nemá přímou syntaktickou podporu a obvykle se nahrazuje konstrukcí `while` s ručně řízeným ukončením.

Příklad v jazyce C:

```c
int i = 0;
do {
    printf("%d\n", i);
    i++;
} while (i < 5);
// Výstup: 0, 1, 2, 3, 4
```

Příklad v Pythonu (napodobení do...while):

```python
i = 0
while True:
    print(i)
    i += 1
    if i >= 5:
        break
# Výstup: 0, 1, 2, 3, 4
```

**Cyklus `for`** – používá se typicky pro opakování s předem známým počtem iterací. Cyklus `for` obvykle obsahuje inicializaci řídící proměnné, podmínku ukončení a krok změny proměnné.

Příklad v jazyce C:

```c
for (int i = 0; i < 5; i++) {
    printf("%d\n", i);
}
// Výstup: 0, 1, 2, 3, 4
```

Příklad v Pythonu:

```python
for i in range(5):
    print(i)
# Výstup: 0, 1, 2, 3, 4
```

Rozdíly v zápisu mezi Pythonem a C:

- V Pythonu se bloky kódu oddělují **odsazením**, v jazyce C složenými závorkami `{}`,
- Python používá konstrukci `range()` pro generování posloupnosti čísel v cyklu `for`,
- V jazyce C má cyklus `for` explicitní tři části: inicializaci, podmínku a krok.

Řídicí struktury jsou základem strukturovaného programování a jejich správné použití je klíčové pro tvorbu logicky správných a efektivních programů.

---

## Podprogramy a jejich význam; funkce, lokální a globální proměnné

### **Význam podprogramů**

S rostoucí složitostí programů se stává nezbytné rozdělit kód na menší, lépe spravovatelné části. **Podprogramy** jsou samostatné bloky kódu, které plní určitou specifickou úlohu a mohou být volány z různých míst programu.

Výhody používání podprogramů:

- **Znovupoužitelnost** – stejný kód lze použít vícekrát bez nutnosti opakovaného psaní,
- **Přehlednost** – program je lépe strukturovaný a srozumitelnější,
- **Údržba** – změny v jednom podprogramu se promítnou všude, kde je voláván,
- **Testování** – jednotlivé části programu lze testovat odděleně,
- **Týmová spolupráce** – různí programátoři mohou pracovat na různých podprogramech.

V moderních programovacích jazycích se podprogramy implementují především jako **funkce** (v některých jazycích také jako **procedury** nebo **metody**).

---

### **Funkce**

**Funkce** je pojmenovaný blok kódu, který provádí určitou úlohu. Funkce může:

- **přijímat vstupní parametry** (argumenty),
- **vracet výsledek** pomocí návratové hodnoty,
- **nemít žádné parametry ani návratovou hodnotu**.

Základní struktura funkce:

```
funkce název(parametry):
    tělo funkce
    return výsledek
```

Příklad funkce v jazyce C:

```c
int secti(int a, int b) {
    int vysledek = a + b;
    return vysledek;
}

// Volání funkce
int main() {
    int suma = secti(5, 3);
    printf("%d\n", suma);  // Výstup: 8
    return 0;
}
```

Příklad funkce v Pythonu:

```python
def secti(a, b):
    vysledek = a + b
    return vysledek

# Volání funkce
suma = secti(5, 3)
print(suma)  # Výstup: 8
```

---

### Parametry a argumenty funkcí

**Parametry** jsou proměnné definované v hlavičce funkce, které přijímají hodnoty argumentů.

**Argumenty** jsou konkrétní hodnoty, které se předávají funkci při jejím volání. 

**Návratová hodnota** je výsledek, který funkce vrací volajícímu kódu.

Funkce může mít:

- více parametrů,
- žádný parametr,
- žádnou návratovou hodnotu (procedura).

Příklad funkce s více parametry a návratovou hodnotou v jazyce C:

```c
int secti(int a, int b) {
    return a + b;
}
```

Volání funkce:

```c
int suma = secti(5, 3);
printf("%d\n", suma);  // Výstup: 8
``` 

Příklad funkce s více parametry a návratovou hodnotou v Pythonu:

```python
def secti(a, b):
    return a + b
```

Volání funkce:

```python
suma = secti(5, 3)
print(suma)  # Výstup: 8
```

Příklad funkce bez návratové hodnoty v C:

```c
void pozdrav(char *jmeno) {
    printf("Ahoj, %s!\n", jmeno);
}

Příklad funkce bez návratové hodnoty v Pythonu:

```python
def pozdrav(jmeno):
    print(f"Ahoj, {jmeno}!")

pozdrav("Alice")  # Výstup: Ahoj, Alice!
```

---

### **Lokální a globální proměnné**

**Lokální proměnné** jsou deklarovány uvnitř funkce a existují pouze po dobu jejího vykonávání. Po ukončení funkce jsou lokální proměnné zrušeny a jejich hodnoty přestávají existovat.

Vlastnosti lokálních proměnných:

- viditelnost omezená na tělo funkce,
- každé volání funkce vytváří nové instance lokálních proměnných,
- různé funkce mohou mít lokální proměnné se stejným názvem bez konfliktu.

**Globální proměnné** jsou deklarovány mimo funkce a jsou přístupné z celého programu, včetně všech funkcí. Existují po celou dobu běhu programu.

Vlastnosti globálních proměnných:

- viditelnost v celém programu,
- sdíleny mezi všemi funkcemi,
- uchování hodnoty mezi jednotlivými voláními funkcí.

Příklad v jazyce C:

```c
int globalni_promenna = 100;  // Globální proměnná

void funkce() {
    int lokalni_promenna = 50;  // Lokální proměnná
    printf("Lokální: %d\n", lokalni_promenna);
    printf("Globální: %d\n", globalni_promenna);
}

int main() {
    funkce();
    return 0;
}
```

Příklad v Pythonu:

```python
globalni_promenna = 100  # Globální proměnná

def funkce():
    lokalni_promenna = 50  # Lokální proměnná
    print(f"Lokální: {lokalni_promenna}")
    print(f"Globální: {globalni_promenna}")

funkce()
# Výstup:
# Lokální: 50
# Globální: 100
```

**Rizika používání globálních proměnných:**

- **Nežádoucí změny** – jakákoliv funkce může změnit hodnotu globální proměnné, což může vést k neočekávanému chování.
- **Složitější ladění** – obtížné sledování, kde a kdy byla globální proměnná změněna.
- **Závislosti** – funkce používající globální proměnné jsou méně nezávislé a hůře znovupoužitelné.
- **Konflikty názvů** – v rozsáhlých projektech může docházet k nežádoucím kolizím názvů.

Proto je doporučováno minimalizovat používání globálních proměnných a preferovat předávání hodnot pomocí parametrů funkcí.

---

## Modularita programů, knihovny a jejich využití, hlavičkové soubory

### **Modularita a její přínosy**

S růstem velikosti a složitosti programů se stává nezbytné rozdělit kód do více samostatných částí. **Modularita** je princip členění programu na menší, logicky související celky nazývané **moduly**.

Modularita přináší několik zásadních výhod:

- **Lepší organizace** – kód je strukturovaný podle funkčnosti.
- **Znovupoužitelnost** – moduly lze používat v různých projektech.
- **Týmová spolupráce** – různí vývojáři mohou pracovat na různých modulech současně.
- **Snadnější údržba** – změny v jednom modulu neovlivňují ostatní.
- **Testování** – jednotlivé moduly lze testovat nezávisle.

---

### **Programové knihovny**

**Knihovna** je kolekce předpřipravených funkcí, tříd a dalších programových konstrukcí, které řeší běžné úlohy. Knihovny umožňují programátorům využívat již napsaný a otestovaný kód místo opětovného vymýšlení a implementace základních funkcionalit.

Rozlišujeme:

**Standardní knihovny** – dodávány společně s programovacím jazykem a poskytují základní funkcionalitu, například:

- práce s řetězci,
- matematické funkce,
- vstup a výstup,
- práce se soubory.

**Externí knihovny** – vytvářené třetími stranami pro specifické účely, například:

- grafické knihovny,
- síťové knihovny,
- knihovny pro zpracování dat.

V jazyce Python se knihovny připojují pomocí příkazu `import`, v jazyce C pomocí direktivy preprocesoru `#include`.

Příklad použití standardní knihovny v jazyce C:

```c
#include <stdio.h>
#include <math.h>

int main() {
    double vysledek = sqrt(16.0);  // Odmocnina
    printf("%.1f\n", vysledek);  // Výstup: 4.0
    return 0;
}
```

Příklad použití standardní knihovny v Pythonu:

```python
import math

vysledek = math.sqrt(16)  # Odmocnina
print(vysledek)  # Výstup: 4.0
```

---

### **Hlavičkové soubory v jazyce C**

**Hlavičkový soubor** (header file) je soubor s příponou `.h`, který obsahuje deklarace funkcí, datových typů, konstant a dalších konstruktů, které mají být sdíleny mezi různými částmi programu.

Hlavičkové soubory plní dvě základní role:

- **Rozhraní** – definují, jaké funkce a datové struktury jsou dostupné,
- **Deklarace** – oddělují deklaraci funkcí od jejich implementace.

Typická struktura programu v jazyce C:

```
hlavickovy_soubor.h  - deklarace funkcí a typů
zdrojovy_soubor.c    - implementace funkcí
hlavni_program.c     - hlavní program využívající funkce
```

**Standardní hlavičkové soubory** jsou součástí standardní knihovny jazyka C a poskytují základní funkcionalitu:

- `<stdio.h>` – vstup a výstup (např. `printf`, `scanf`),
- `<math.h>` – matematické funkce (např. `sqrt`, `sin`, `cos`),
- `<string.h>` – práce s řetězci (např. `strlen`, `strcpy`),
- `<stdlib.h>` – obecné funkce (např. `malloc`, `free`, `rand`).

Standardní hlavičkové soubory se vkládají pomocí lomených závorek:

```c
#include <stdio.h>
#include <math.h>
```

**Uživatelské hlavičkové soubory** jsou vytvářeny programátorem pro vlastní projekty. Umožňují rozdělit kód do logických celků a znovupoužití funkcí v různých částech programu.

Uživatelské hlavičkové soubory se vkládají pomocí uvozovek:

```c
#include "moje_funkce.h"
```

Příklad uživatelského hlavičkového souboru `matematika.h`:

```c
#ifndef MATEMATIKA_H
#define MATEMATIKA_H

int secti(int a, int b);
int odecti(int a, int b);

#endif
```

Příklad implementace v souboru `matematika.c`:

```c
#include "matematika.h"

int secti(int a, int b) {
    return a + b;
}

int odecti(int a, int b) {
    return a - b;
}
```

Použití v hlavním programu:

```c
#include <stdio.h>
#include "matematika.h"

int main() {
    int vysledek = secti(10, 5);
    printf("Výsledek: %d\n", vysledek);  // Výstup: 15
    return 0;
}
```

Direktivy `#ifndef`, `#define` a `#endif` tvoří tzv. **include guard** (ochranu proti vícenásobnému zahrnutí), který zajišťuje, že hlavičkový soubor bude do programu vložen pouze jednou, i když je k němu odkazováno z více míst.

---

### **Moduly v jazyce Python**

V Pythonu se modularita realizuje pomocí **modulů**. Modul je jednoduše soubor s příponou `.py` obsahující definice funkcí, tříd a proměnných.

Příklad modulu `matematika.py`:

```python
def secti(a, b):
    return a + b

def odecti(a, b):
    return a - b
```

Použití modulu v jiném souboru:

```python
import matematika

vysledek = matematika.secti(10, 5)
print(f"Výsledek: {vysledek}")  # Výstup: 15
```

Alternativně lze importovat pouze konkrétní funkce:

```python
from matematika import secti

vysledek = secti(10, 5)
print(f"Výsledek: {vysledek}")  # Výstup: 15
```

Modularita je klíčovým principem moderního programování a její správné využití výrazně zvyšuje kvalitu a udržovatelnost softwarových projektů.
