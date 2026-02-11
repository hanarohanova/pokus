# Datové struktury a soubory

## Strukturované datové typy, ukazatele, statické a dynamické pole, matice

### Strukturované datové typy

**Skalární datové typy** reprezentují jednotlivé hodnoty, například celá čísla (`int`), desetinná čísla (`float`) nebo znaky (`char`). Každá proměnná skalárního typu obsahuje právě jednu hodnotu.

> Pojem "skalární" pochází z matematiky a znamená "jednoduchý" nebo "nekompozitní". Skalární datové typy jsou základními stavebními kameny pro vytváření složitějších datových struktur.
> 
> `Věk` je skalární datový typ, protože představuje jednu hodnotu (například 25).
> `Teplota` je skalární datový typ, protože představuje jednu hodnotu (například 36.5 °C).

Opakem skalárních datových typů jsou **strukturované datové typy**, které mohou obsahovat více hodnot uspořádaných podle určitého pravidla.

**Strukturované datové typy** umožňují ukládat více hodnot uspořádaných podle určitého pravidla. Strukturované typy poskytují způsob organizace dat do logických celků, což zjednodušuje práci se složitějšími datovými strukturami.

> Příklady z reálného světa:
>
> `Osoba` může být strukturovaný datový typ, který obsahuje atributy jako `jmeno`, `vek`, `mesto`. Každý atribut představuje jednu vlastnost osoby, a všechny tyto vlastnosti dohromady tvoří komplexní datovou strukturu.

Základní typy strukturovaných dat zahrnují:

- **pole** – uspořádaná kolekce prvků stejného typu,
- **záznamy (struktury)** – kolekce prvků různých typů,
- **seznamy** – dynamické kolekce prvků,
- **slovníky** – kolekce párů klíč-hodnota.

### Pole jako základní datová struktura

**Pole** je základní strukturovaný datový typ, který uchovává pevný počet prvků stejného typu uspořádaných v posloupnosti. Každý prvek pole je přístupný pomocí **indexu**, což je číselná pozice prvku v poli.

Vlastnosti pole:

- všechny prvky mají stejný datový typ,
- prvky jsou uloženy v paměti za sebou,
- přístup k prvkům je rychlý díky indexování,
- velikost pole je obvykle stanovena při vytvoření.

Indexování v poli:

- v jazycích C a C++ se indexuje od nuly,
- první prvek má index `0`, druhý index `1` atd.
- přístup k prvku se provádí pomocí hranatých závorek, například `pole[0]` pro první prvek.

> V Pythonu tradiční pole nahrazují **seznamy** (`list`), které jsou dynamické a mohou obsahovat prvky různých typů, ale základní princip indexování zůstává stejný.
> Pole v Pythonu lze simulovat pomocí modulu `array`, který poskytuje efektivní pole pro základní datové typy.

Příklad v Pythonu s modulem `array`:

```python
import array
# Vytvoření pole celých čísel
cisla = array.array('i', [10, 20, 30, 40, 50])
print(cisla[0])  # Výstup: 10
```

Schematické znázornění pole:

```
Index:    0     1     2     3     4
Hodnota: [10]  [20]  [30]  [40]  [50]
         ^
         |
    adresa v paměti
```

### Statické pole

**Statické pole** má velikost pevně stanovenou při deklaraci a nelze ji během běhu programu změnit. Paměť pro statické pole je alokována při vytvoření proměnné.

Příklad v jazyce C:

```c
int cisla[5];  // Pole s 5 prvky typu int
cisla[0] = 10;
cisla[1] = 20;
cisla[2] = 30;

// Inicializace při deklaraci
int hodnoty[5] = {10, 20, 30, 40, 50};
```

### Dynamické pole

**Dynamické pole** umožňuje měnit svou velikost během běhu programu. Paměť se alokuje dynamicky podle potřeby, což poskytuje větší flexibilitu při práci s daty neznámého rozsahu.

V jazyce C se dynamická alokace provádí pomocí funkcí `malloc` a `free`:

```c
#include <stdlib.h>

int *pole;
int velikost = 5;

// Dynamická alokace paměti
pole = (int *)malloc(velikost * sizeof(int));

// Použití pole
pole[0] = 10;
pole[1] = 20;

// Uvolnění paměti
free(pole);
```

V Pythonu jsou seznamy (`list`) dynamické automaticky:

```python
cisla = []  # Prázdný seznam
cisla.append(10)  # Přidání prvku
cisla.append(20)
cisla.append(30)

# Seznam automaticky roste podle potřeby
```

### Ukazatele a pole

**Ukazatel** je proměnná, která uchovává adresu v paměti, kde je uložena jiná hodnota. Ukazatele jsou klíčové při práci s dynamickými datovými strukturami.

V jazyce C existuje úzký vztah mezi poli a ukazateli:

```c
int pole[5] = {10, 20, 30, 40, 50};
int *ukazatel = pole;  // Ukazatel na první prvek

// Přístup pomocí ukazatele
printf("%d\n", *ukazatel);      // Výstup: 10
printf("%d\n", *(ukazatel + 1)); // Výstup: 20
```

Název pole v jazyce C funguje jako ukazatel na jeho první prvek. To umožňuje efektivní práci s pamětí, ale vyžaduje opatrnost při manipulaci.

### Matice (vícerozměrná pole)

**Matice** je vícerozměrné pole, nejčastěji dvourozměrné, které lze chápat jako tabulku hodnot s řádky a sloupci.

Příklad v jazyce C:

```c
int matice[3][4];  // Matice 3 řádky × 4 sloupce

// Inicializace
int cisla[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};

// Přístup k prvkům
cisla[0][0] = 10;  // První řádek, první sloupec
cisla[1][2] = 60;  // Druhý řádek, třetí sloupec
```

Příklad v Pythonu:

```python
# Vnořené seznamy jako matice
matice = [
    [1, 2, 3],
    [4, 5, 6]
]

# Přístup k prvkům
matice[0][0] = 10  # První řádek, první sloupec
matice[1][2] = 60  # Druhý řádek, třetí sloupec
```

Schematické znázornění matice:

```
        sloupec 0  sloupec 1  sloupec 2
řádek 0    [1]       [2]        [3]
řádek 1    [4]       [5]        [6]
```

Matice se používají v mnoha oblastech, například při reprezentaci obrazu, řešení soustav rovnic, grafice nebo zpracování tabulkových dat.

---

## Znakové řetězce, práce se znakovými řetězci v jazyce C a Python, funkce pro práci s řetězci

### Znakové řetězce jako datový typ

**Znakový řetězec** (string) je posloupnost znaků reprezentující text. Řetězce patří mezi nejpoužívanější datové typy, protože většina programů pracuje s textovými daty.

Reprezentace řetězců se liší mezi programovacími jazyky:

- v jazyce C je řetězec pole znaků ukončené speciálním znakem,
- v Pythonu je řetězec samostatný datový typ s mnoha vestavěnými metodami.

### Řetězce v jazyce C

V jazyce C je řetězec implementován jako **pole znaků** typu `char`, které je ukončeno nulovým znakem `'\0'`. Tento ukončující znak signalizuje konec řetězce a umožňuje funkcím určit délku řetězce.

Příklad:

```c
char pozdrav[6] = {'A', 'h', 'o', 'j', '!', '\0'};

// Zkrácený zápis - ukončovací znak se přidá automaticky
char text[] = "Ahoj!";
```

Reprezentace v paměti:

```
Index:  0   1   2   3   4   5
Znak:  'A' 'h' 'o' 'j' '!' '\0'
```

Práce s řetězci v jazyce C vyžaduje použití funkcí ze standardní knihovny `<string.h>`:

```c
#include <string.h>
#include <stdio.h>

char text1[20] = "Ahoj";
char text2[20] = " svete";

// Délka řetězce
int delka = strlen(text1);  // Výsledek: 4

// Kopírování řetězce
strcpy(text1, "Novy text");

// Spojení řetězců
strcat(text1, text2);  // text1 = "Novy text svete"

// Porovnání řetězců
int vysledek = strcmp(text1, text2);  // 0 = stejné, <0 nebo >0 = různé
```

Základní funkce pro práce s řetězci v C:

- `strlen(str)` – vrací délku řetězce,
- `strcpy(dest, src)` – kopíruje řetězec,
- `strcat(dest, src)` – připojuje řetězec,
- `strcmp(str1, str2)` – porovnává řetězce,
- `strchr(str, ch)` – hledá znak v řetězci.

### Řetězce v Pythonu

V Pythonu je řetězec objektem typu `str`, který poskytuje mnoho vestavěných metod pro manipulaci s textem. Řetězce v Pythonu jsou **neměnné** (*immutable*) – jakmile jsou vytvořeny, nelze změnit jejich obsah, ale lze vytvořit nové řetězce.

Příklad:

```python
text = "Ahoj!"
dalsi_text = 'Python'

# Spojení řetězců
spojen = text + " " + dalsi_text  # "Ahoj! Python"

# Délka řetězce
delka = len(text)  # 5

# Přístup k znakům pomocí indexu
prvni_znak = text[0]  # 'A'
posledni_znak = text[-1]  # '!'

# Vyříznutí podřetězce (slicing)
cast = text[0:4]  # "Ahoj"
```

Základní metody pro práci s řetězci v Pythonu:

```python
text = "Ahoj Svete"

# Převod na velká/malá písmena
velky = text.upper()     # "AHOJ SVETE"
maly = text.lower()      # "ahoj svete"

# Hledání podřetězce
pozice = text.find("Svete")  # 5
obsahuje = "Svete" in text   # True

# Rozdělení řetězce
slova = text.split(" ")  # ["Ahoj", "Svete"]

# Nahrazení podřetězce
novy = text.replace("Ahoj", "Nazdar")  # "Nazdar Svete"

# Odstranění bílých znaků
text2 = "  text  "
cisteny = text2.strip()  # "text"
```

### Srovnání práce s řetězci

Hlavní rozdíly mezi jazyky C a Python:

| Aspekt | C | Python |
|--------|---|--------|
| Reprezentace | Pole znaků s `'\0'` | Objekt typu `str` |
| Měnitelnost | Měnitelné | Neměnné |
| Délka | Musí se vypočítat (`strlen`) | Vestavěná funkce `len()` |
| Spojení | `strcat()` | Operátor `+` |
| Bezpečnost | Riziko přetečení bufferu | Automatická správa paměti |

Python nabízí pohodlnější a bezpečnější práci s řetězci díky vysokoúrovňovým abstrakcím, zatímco C poskytuje větší kontrolu nad pamětí, ale vyžaduje opatrnější přístup.

---

## Regulární výrazy a jejich využití při práci s textem

### Princip regulárních výrazů

**Regulární výraz** (*regular expression*, *regex*) je vzor definující množinu řetězců. Regulární výrazy poskytují mocný nástroj pro vyhledávání, ověřování a manipulaci s textem na základě definovaných pravidel.

Regulární výrazy umožňují:

- vyhledávat řetězce odpovídající danému vzoru,
- ověřovat správnost formátu dat (validace),
- extrahovat části textu,
- nahrazovat text podle vzoru.

### Základní konstrukce regulárních výrazů

Regulární výrazy používají speciální znaky a konstrukce pro definování vzorů:

**Literály** – běžné znaky odpovídají samy sobě:
- `abc` – odpovídá řetězci "abc"

**Metaznaky** – speciální znaky s významem:
- `.` – jakýkoliv znak
- `^` – začátek řetězce
- `$` – konec řetězce
- `*` – 0 nebo více opakování
- `+` – 1 nebo více opakování
- `?` – 0 nebo 1 výskyt
- `|` – alternativa (nebo)

**Třídy znaků** – definují množinu znaků:
- `[abc]` – znak a, b nebo c
- `[0-9]` – jakákoliv číslice
- `[a-z]` – jakékoli malé písmeno
- `\d` – číslice (digit)
- `\w` – alfanumerický znak
- `\s` – bílý znak (mezera, tabulátor)

**Kvantifikátory** – určují počet opakování:
- `{n}` – přesně n opakování
- `{n,}` – n nebo více opakování
- `{n,m}` – mezi n a m opakování

### Použití regulárních výrazů v Pythonu

Python poskytuje modul `re` pro práci s regulárními výrazy:

```python
import re

text = "Kontakt: email@example.com, telefon: 123-456-789"

# Vyhledání emailové adresy
email_vzor = r'\w+@\w+\.\w+'
email = re.search(email_vzor, text)
if email:
    print(email.group())  # Výstup: email@example.com

# Vyhledání všech číslic
cisla = re.findall(r'\d+', text)
print(cisla)  # ['123', '456', '789']

# Kontrola formátu
telefon = "123-456-789"
vzor_telefonu = r'^\d{3}-\d{3}-\d{3}$'
if re.match(vzor_telefonu, telefon):
    print("Platné telefonní číslo")
```

Běžné operace s regulárními výrazy:

```python
# Hledání prvního výskytu
vysledek = re.search(vzor, text)

# Hledání všech výskytů
vse = re.findall(vzor, text)

# Kontrola od začátku řetězce
shoda = re.match(vzor, text)

# Nahrazení podle vzoru
novy_text = re.sub(vzor, nahrada, text)
```

### Praktické příklady

**Validace emailové adresy:**

```python
email_vzor = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
email = "uzivatel@example.com"
if re.match(email_vzor, email):
    print("Platný email")
```

**Extrakce dat z textu:**

```python
text = "Datum: 15.01.2026, cena: 1500 Kč"
datum = re.search(r'\d{2}\.\d{2}\.\d{4}', text)
cena = re.search(r'\d+', text)
print(datum.group())  # 15.01.2026
```

**Nahrazení citlivých dat:**

```python
text = "Číslo karty: 1234-5678-9012-3456"
anonymizovano = re.sub(r'\d{4}-\d{4}-\d{4}-\d{4}', 'XXXX-XXXX-XXXX-XXXX', text)
print(anonymizovano)  # Číslo karty: XXXX-XXXX-XXXX-XXXX
```

### Oblasti využití

Regulární výrazy se používají v mnoha oblastech:

- **validace vstupů** – ověření formátu emailů, telefonních čísel, hesel,
- **zpracování logů** – extrakce informací ze souborů protokolů,
- **čištění dat** – odstranění nechtěných znaků nebo normalizace formátu,
- **vyhledávání v textu** – pokročilé hledání v editorech a nástrojích,
- **web scraping** – extrakce dat z HTML stránek.

Regulární výrazy jsou mocný nástroj, ale jejich složitost může činit kód méně čitelným. Proto je důležité používat je uvážlivě a dokumentovat složitější vzory.

---

## Zpracování datových souborů v programech, vstupní a výstupní operace se soubory

### Význam souborů v programování

**Soubor** je pojmenovaná oblast na trvalém úložišti (disk, USB), která uchovává data. Soubory umožňují programům:

- **uchovávat data** i po ukončení programu,
- **sdílet data** mezi různými programy,
- **zpracovávat velké objemy dat**, které by se nevešly do paměti najednou,
- **vytvářet trvalé záznamy** a logy.

### Textové a binární soubory

**Textové soubory** obsahují data reprezentovaná jako znaky čitelné člověkem. Každý řádek je obvykle ukončen speciálním znakem pro nový řádek. Textové soubory lze otevřít a číst v běžném textovém editoru.

Příklady textových souborů:

- `.txt` – prostý text,
- `.csv` – tabulková data oddělená čárkami,
- `.html`, `.xml`, `.json` – strukturované textové formáty.

**Binární soubory** obsahují data v binární podobě, která není přímo čitelná člověkem. Jsou efektivnější pro ukládání velkých objemů dat nebo složitých struktur.

Příklady binárních souborů:

- `.exe` – spustitelné soubory,
- `.jpg`, `.png` – obrázky,
- `.mp3`, `.wav` – zvukové soubory,
- `.bin`, `.dat` – obecná binární data.

### Základní operace se soubory

Práce se soubory typicky zahrnuje čtyři základní kroky:

1. **Otevření souboru** – vytvoření spojení mezi programem a souborem.
2. **Čtení nebo zápis** – manipulace s daty.
3. **Zpracování dat** – operace s načtenými daty.
4. **Uzavření souboru** – uvolnění prostředků.

### Práce se soubory v jazyce C

V jazyce C se používají **souborové ukazatele** typu `FILE*` pro práci se soubory. Hlavičkový soubor `<stdio.h>` obsahuje funkce pro vstup a výstup.

**Otevření souboru:**

```c
#include <stdio.h>

FILE *soubor;
soubor = fopen("data.txt", "r");  // "r" = čtení

if (soubor == NULL) {
    printf("Chyba při otevírání souboru\n");
    return 1;
}
```

Režimy otevření souboru:
- `"r"` – čtení (soubor musí existovat),
- `"w"` – zápis (vytvoří nový nebo přepíše existující),
- `"a"` – připojení (zápis na konec souboru),
- `"r+"` – čtení i zápis.

**Čtení ze souboru:**

```c
char radek[100];

// Čtení řádku
while (fgets(radek, 100, soubor) != NULL) {
    printf("%s", radek);
}

// Čtení jednotlivých znaků
int znak;
while ((znak = fgetc(soubor)) != EOF) {
    putchar(znak);
}
```

**Zápis do souboru:**

```c
FILE *soubor = fopen("vystup.txt", "w");

fprintf(soubor, "Text: %s\n", "Ahoj");
fprintf(soubor, "Číslo: %d\n", 42);

fclose(soubor);
```

**Uzavření souboru:**

```c
fclose(soubor);  // Důležité pro uvolnění prostředků
```

### Práce se soubory v Pythonu

Python poskytuje vestavěné funkce pro práci se soubory a doporučuje použít **kontextový manažer** (`with`), který automaticky uzavře soubor.

**Čtení ze souboru:**

```python
# Bezpečný způsob - automatické uzavření
with open("data.txt", "r", encoding="utf-8") as soubor:
    obsah = soubor.read()  # Celý obsah
    print(obsah)

# Čtení po řádcích
with open("data.txt", "r", encoding="utf-8") as soubor:
    for radek in soubor:
        print(radek.strip())  # strip() odstraní \n

# Načtení všech řádků do seznamu
with open("data.txt", "r", encoding="utf-8") as soubor:
    radky = soubor.readlines()
```

**Zápis do souboru:**

```python
# Zápis přepíše existující soubor
with open("vystup.txt", "w", encoding="utf-8") as soubor:
    soubor.write("První řádek\n")
    soubor.write("Druhý řádek\n")

# Připojení na konec souboru
with open("vystup.txt", "a", encoding="utf-8") as soubor:
    soubor.write("Další řádek\n")
```

Režimy otevření v Pythonu:
- `"r"` – čtení (výchozí),
- `"w"` – zápis (přepíše existující),
- `"a"` – připojení,
- `"r+"` – čtení i zápis,
- `"b"` – binární režim (např. `"rb"`, `"wb"`).

### Srovnání práce se soubory

| Aspekt | C | Python |
|--------|---|--------|
| Otevření | `fopen()` | `open()` |
| Čtení | `fgets()`, `fgetc()` | `read()`, `readline()` |
| Zápis | `fprintf()`, `fputc()` | `write()` |
| Uzavření | Manuální `fclose()` | Automatické s `with` |
| Bezpečnost | Vyžaduje kontrolu | Jednodušší správa chyb |

Python nabízí pohodlnější a bezpečnější práci se soubory díky automatické správě prostředků, zatímco C poskytuje nižší úroveň kontroly.

---

## Nejpoužívanější typy datových formátů (CSV, XML, JSON, YAML), základní rysy a praktické využití

### Význam strukturovaných datových formátů

Při ukládání a přenosu dat mezi programy nebo systémy je důležité používat standardizované formáty, které zajistí:

- **přenositelnost** – data lze sdílet mezi různými programy a platformami,
- **čitelnost** – strukturovaná data jsou srozumitelnější,
- **parsovatelnost** – programy mohou data snadno načíst a zpracovat,
- **interoperabilitu** – různé systémy mohou spolupracovat.

### CSV (Comma-Separated Values)

**CSV** je jednoduchý textový formát pro ukládání tabulkových dat. Každý řádek souboru odpovídá jednomu záznamu a hodnoty jsou odděleny čárkami (nebo jinými oddělovači).

Příklad CSV souboru:

```
jmeno,vek,mesto
Alice,25,Praha
Jan,30,Brno
Ludmila,22,Ostrava
```

Vlastnosti CSV:

- **jednoduchost** – snadné vytvoření i ruční editace,
- **kompaktnost** – malá velikost souborů,
- **široká podpora** – většina nástrojů CSV podporuje,
- **omezení** – obtížné ukládání hierarchických nebo vnořených dat.

Práce s CSV v Pythonu:

```python
import csv

# Čtení CSV
with open("data.csv", "r", encoding="utf-8") as soubor:
    ctenar = csv.reader(soubor)
    hlavicka = next(ctenar)  # První řádek
    for radek in ctenar:
        print(radek)  # ['Alice', '25', 'Praha']

# Zápis CSV
with open("vystup.csv", "w", newline="", encoding="utf-8") as soubor:
    zapisovac = csv.writer(soubor)
    zapisovac.writerow(["jmeno", "vek", "mesto"])
    zapisovac.writerow(["David", "28", "Plzeň"])
```

CSV se používá pro:

- export dat z tabulkových procesorů,
- výměnu dat mezi databázemi,
- statistické zpracování dat,
- logy a reporty.

### XML (eXtensible Markup Language)

**XML** je značkovací jazyk určený pro strukturované ukládání dat. Používá značky (tagy) pro definování hierarchie a struktury dat.

Příklad XML souboru:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<osoby>
    <osoba>
        <jmeno>Alice</jmeno>
        <vek>25</vek>
        <mesto>Praha</mesto>
    </osoba>
    <osoba>
        <jmeno>Jan</jmeno>
        <vek>30</vek>
        <mesto>Brno</mesto>
    </osoba>
</osoby>
```

Vlastnosti XML:

- **hierarchická struktura** – stromová organizace dat,
- **samodokumentující** – názvy tagů popisují obsah,
- **rozšiřitelnost** – možnost definovat vlastní tagy,
- **validace** – lze ověřit strukturu pomocí schémat,
- **rozvláčnost** – větší velikost souborů kvůli opakujícím se tagům.

XML se používá pro:

- konfigurační soubory,
- výměnu dat mezi systémy (SOAP webové služby),
- reprezentaci dokumentů (Office Open XML),
- ukládání komplexních datových struktur.

### JSON (JavaScript Object Notation)

**JSON** je lehký textový formát pro výměnu dat založený na syntaxi JavaScriptu. Je čitelnější a kompaktnější než XML.

Příklad JSON souboru:

```json
{
  "osoby": [
    {
      "jmeno": "Alice",
      "vek": 25,
      "mesto": "Praha"
    },
    {
      "jmeno": "Jan",
      "vek": 30,
      "mesto": "Brno"
    }
  ]
}
```

Vlastnosti JSON:

- **jednoduchost** – snadno čitelný i zapisovatelný,
- **kompaktnost** – menší velikost než XML,
- **nativní podpora** – přímo podporován v JavaScriptu,
- **omezené datové typy** – čísla, řetězce, objekty, pole, boolean, null.

Práce s JSON v Pythonu:

```python
import json

# Načtení JSON
with open("data.json", "r", encoding="utf-8") as soubor:
    data = json.load(soubor)
    print(data["osoby"][0]["jmeno"])  # Alice

# Zápis JSON
data = {
    "osoby": [
        {"jmeno": "Ludmila", "vek": 22, "mesto": "Ostrava"}
    ]
}
with open("vystup.json", "w", encoding="utf-8") as soubor:
    json.dump(data, soubor, indent=2, ensure_ascii=False)
```

JSON se používá pro:

- RESTful API komunikaci,
- konfigurační soubory,
- ukládání strukturovaných dat,
- výměnu dat mezi webovými aplikacemi.

### YAML (YAML Ain't Markup Language)

**YAML** je lidsky čitelný formát pro serializaci dat. Klade důraz na jednoduchost a čitelnost, používá odsazení místo složených závorek.

Příklad YAML souboru:

```yaml
osoby:
  - jmeno: Alice
    vek: 25
    mesto: Praha
  - jmeno: Jan
    vek: 30
    mesto: Brno
```

Vlastnosti YAML:

- **čitelnost** – velmi přehledný pro člověka,
- **minimalistický** – méně syntaktických značek,
- **podpora komentářů** – označeny `#`,
- **citlivost na odsazení** – struktura je určena odsazením.

YAML se používá pro:

- konfigurační soubory (Docker, Kubernetes),
- definice CI/CD pipeline,
- nastavení aplikací,
- dokumentaci struktury dat.

### Srovnání formátů

| Formát | Čitelnost | Velikost | Složitost | Typické využití |
|--------|-----------|----------|-----------|-----------------|
| CSV | Vysoká | Malá | Nízká | Tabulková data |
| XML | Střední | Velká | Vysoká | Dokumenty, komplexní struktury |
| JSON | Vysoká | Střední | Střední | Web API, konfigurace |
| YAML | Velmi vysoká | Střední | Střední | Konfigurace, DevOps |

Volba formátu závisí na konkrétních požadavcích projektu:

- **CSV** pro jednoduché tabulkové exporty,
- **JSON** pro moderní webové API,
- **XML** pro komplexní dokumenty a legacy systémy,
- **YAML** pro čitelné konfigurační soubory.
