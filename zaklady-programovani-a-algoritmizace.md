# Základy programování a algoritmizace

## 1. Základní pojmy z programování (program, algoritmus, programovací jazyk, překladače)

### **Počítačový program**

**Program v obecném smyslu** je scénář kroků (instrukcí), které vedou k dosažení určitého cíle. 

> Například program poznávacího výletu může obsahovat kroky jako: vstát, nasnídat se, sbalit si věci, vyrazit na autobusové nádraží, nastoupit do autobusu a dorazit do cíle.

**Počítačový program** je soubor instrukcí sestavených tak, aby je mohl vykonat počítač, konkrétně procesor. Tyto instrukce jsou napsány v programovacím jazyce (tzv. **zdrojový kód**), který je srozumitelný pro člověka, ale musí být přeložen do **strojového jazyka (binárního kódu)**, kterému rozumí procesor.

Většina programů je určena k řešení konkrétního problému nebo úkolu, například:

- zpracování dat,
- řízení hardwaru,
- komunikaci s uživatelem,
- provádění výpočtů.

> Příkladem jednoduchého programu může být kalkulačka, která přijímá vstupy zadané uživatelem, provádí výpočty podle určitého algoritmu a zobrazuje výstupy.

---

### **Algoritmus**

Algoritmus je **přesný a konečný postup řešení určitého problému nebo úkolu**, který je popsán pomocí jednotlivých kroků (instrukcí).

> Slovo **algoritmus** pochází z latinského přepisu jména perského matematika *Al-Chorezmiho* (9. století).  

Algoritmy mohou být vyjádřeny různými způsoby, například:

- přirozeným jazykem,
- vývojovým diagramem,
- pseudokódem.

Obecně můžeme za algoritmus považovat jakýkoliv postup, který splňuje následující kritéria:

- **Konečnost** – algoritmus má jasně definovaný začátek a konec.
- **Definovanost** – každý krok algoritmu je jednoznačně určen.
- **Vstupy** – algoritmus může pracovat se vstupními daty.
- **Výstupy** – algoritmus produkuje výsledky své činnosti.

> Mini příklad algoritmu (bez programování): „Uvař čaj“
>
> - Nalij vodu do konvice.
> - Zapni konvici.
> - Do hrnku dej sáček.
> - Zalij vroucí vodou.
> - Počkej 3–5 minut.
> - Vyjmi sáček.

---

### **Programovací jazyk**

**Přirozený jazyk** je jazyk, kterým lidé běžně komunikují (např. čeština, angličtina). Tyto jazyky jsou však pro počítače příliš složité a nejednoznačné.

**Programovací jazyk** je **formální jazyk** určený k psaní počítačových programů. Umožňuje programátorům komunikovat s počítačem a vyjadřovat algoritmy a logiku pomocí přesně definovaných instrukcí.

Každý programovací jazyk má:

- **syntaxi** – pravidla zápisu příkazů,
- **sémantiku** – význam jednotlivých příkazů.

Existuje mnoho různých programovacích jazyků, které se liší svým určením a oblastí použití, například:

- **webový vývoj** – JavaScript (HTML a CSS jako doplňkové jazyky),
- **vědecké výpočty a data** – Python, R,
- **systémové programování** – C, C++,
- **mobilní aplikace** – Swift, Kotlin.

*Poznámka: HTML a CSS nejsou plnohodnotné programovací jazyky, ale značkovací a stylovací jazyky, které se používají společně s programovacími jazyky při tvorbě webových stránek.*

---

### **Překladače**

Počítač neumí přímo vykonávat programy napsané ve vyšších programovacích jazycích, proto je potřeba je přeložit do **strojového jazyka (binárního kódu)**.  
Tento proces se nazývá **překlad** a provádějí jej speciální programy nazývané **překladače**.

Rozlišujeme dva základní typy překladačů:

- **Kompilátor**  
  Překládá celý zdrojový kód najednou do strojového kódu, který je uložen jako samostatný spustitelný soubor.  
  Příklady kompilovaných jazyků: **C, C++, Go**.

- **Interpret**  
  Překládá a zároveň vykonává zdrojový kód řádek po řádku během běhu programu.  
  Příklady interpretovaných jazyků: **Python, JavaScript, Ruby**.

Moderní programovací jazyky často kombinují oba přístupy. Například:

- **Java** se kompiluje do tzv. *bytecode*, který je následně vykonáván virtuálním strojem JVM.
- **Python** je také převáděn do bytecode, který je interpretován Python interpreterem.

**Bytecode** představuje mezikrok mezi zdrojovým kódem a strojovým kódem. Umožňuje lepší přenositelnost programů mezi různými platformami, protože bytecode lze spustit na libovolném zařízení s odpovídajícím interpretem nebo virtuálním strojem.

---

## 2. Stručný vývoj programování, nižší a vyšší programovací jazyky, typy a příklady moderních programovacích jazyků

---

### **Historický vývoj programování**

Počátky programování úzce souvisí s vývojem výpočetní techniky. První počítače byly konstruovány pro řešení konkrétních výpočetních úloh a jejich programování bylo velmi složité a časově náročné. Například první programy pro počítač ENIAC byly zadávány pomocí přepínačů a kabelů.

V nejranějších fázích se programy zapisovaly přímo ve **strojovém kódu**, tedy jako posloupnosti nul a jedniček. Tento způsob programování byl velmi nepřehledný, náchylný k chybám a silně závislý na konkrétním typu procesoru.

Postupně vznikly **assemblerové jazyky**, které umožnily zapisovat strojové instrukce pomocí symbolických názvů (mnemotechnických zkratek). Přesto zůstávalo programování stále úzce svázané s konkrétním hardwarem.

S rozvojem výpočetní techniky a rostoucí složitostí programů začaly vznikat **vyšší programovací jazyky**, které se snažily přiblížit způsob zápisu lidskému myšlení. Tyto jazyky umožnily:

- zvyšovat produktivitu programátorů,
- psát přehlednější a lépe udržovatelný kód,
- vytvářet přenositelnější programy.

Mezi historicky významné vyšší programovací jazyky patří například **Fortran**, **COBOL**, **Pascal** nebo **C**. Tyto jazyky položily základy moderního programování a mnohé jejich principy se používají dodnes.

---

### **Nižší a vyšší programovací jazyky**

Programovací jazyky lze rozdělit podle úrovně abstrakce na **nižší** a **vyšší**.

**Nižší programovací jazyky** jsou velmi blízké hardwaru a umožňují přímou kontrolu nad chodem počítače. V současnosti se používají méně často, ale stále jsou důležité pro specifické úlohy, jako je vývoj operačních systémů, ovladačů nebo vestavěných systémů.

Typické vlastnosti:

- silná vazba na konkrétní procesor nebo architekturu,
- vysoký výkon a efektivita,
- složitější zápis a horší čitelnost kódu.

Příklady nižších jazyků:

- strojový jazyk - přímý binární kód vykonávaný procesorem,
- assembler - jazyk blízký strojovému kódu, jedna instrukce odpovídá jedné strojové instrukci, ale oproti strojovému kódu používá symbolické názvy pro instrukce a adresy.

Ukázka assemblerového kódu (pro x86 architekturu):

```asm
  MOV AX, 5      ; Načti hodnotu 5 do registru AX
  ADD AX, 10     ; Přičti hodnotu 10 k registru AX
  MOV BX, AX     ; Přesuň hodnotu z registru AX do registru BX
```

**Vyšší programovací jazyky**. Instrukce v těchto jazycích jsou blíže přirozenému jazyku (například angličtině), což usnadňuje jejich pochopení a použití.
Umožňují psát kód, který je srozumitelnější a snadněji udržovatelný, protože abstrahují detaily hardwaru a v jedné instrukci mohou zahrnovat více operací.

Typické vlastnosti:

- lepší čitelnost a srozumitelnost kódu,
- vyšší produktivita při vývoji,
- větší přenositelnost programů mezi platformami.

Příklady vyšších jazyků:

- C, C++,
- Java,
- Python,
- JavaScript.

Rozdělení na nižší a vyšší jazyky není zcela striktní. Některé jazyky (např. C nebo C++) stojí na pomezí obou kategorií – umožňují práci blízkou hardwaru, ale zároveň poskytují prvky vyšší úrovně.

---

### **Typy moderních programovacích jazyků**

Moderní programovací jazyky lze rozdělit podle různých hledisek. Jedním z nejpoužívanějších je rozdělení podle **oblasti použití**, dalším kritériem může být **paradigma programování** (procedurální, objektově orientované, funkcionální, logické), použitá **syntaktická struktura** (blokové jazyky, značkovací jazyky), případně **úroveň abstrakce** (nízkoúrovňové vs. vysokoúrovňové jazyky).

- **Programovací jazyky pro webový vývoj**

  - JavaScript – klientská i serverová část webu,
  - PHP – serverové webové aplikace,
  - Python – backend, webové frameworky.

- **Programovací jazyky pro aplikační a systémový vývoj**

  - C, C++ – systémový software, ovladače, herní enginy,
  - Java, C# – desktopové a podnikové aplikace,
  - Rust – systémové programování s důrazem na bezpečnost.

- **Programovací jazyky pro mobilní aplikace**

  - Swift – aplikace pro iOS,
  - Kotlin – aplikace pro Android.

- **Programovací jazyky pro vědecké výpočty a práci s daty**
  - Python – analýza dat, umělá inteligence,
  - R – statistika a datová analýza.

- **Speciální a doménově orientované jazyky**
  - SQL – práce s databázemi,
  - Bash – skriptování v operačních systémech.

Výběr programovacího jazyka závisí na konkrétním účelu použití, požadavcích na výkon, přenositelnost, bezpečnost a také na zkušenostech vývojáře nebo vývojového týmu.

---

## 3. Princip fungování programu v počítači, program a proces, multitasking, multithreading, využívání paměti, ukazatele

---

### **Princip fungování programu v počítači**

Počítač vykonává programy pomocí **procesoru (CPU)**, který postupně zpracovává jednotlivé instrukce. 

Aby bylo možné program spustit, musí být jeho instrukce:

1. načteny z úložiště (např. disk),
2. umístěny do operační paměti (RAM),
3. postupně vykonávány procesorem.

> Procesor pracuje v cyklu, který se často označuje jako **cyklus načti – dekóduj – vykonej**:
>
> - **načti** instrukci z paměti,
> - **dekóduj** instrukci (zjisti, co má procesor udělat),
> - **vykonej** instrukci (výpočet, práce s pamětí, skok v programu).

Operační systém přitom zajišťuje:

- spouštění programů,
- přidělování systémových prostředků (čas procesoru, paměť),
- komunikaci mezi hardwarem a softwarem.

Program tedy nikdy neběží „sám o sobě“, ale vždy **za asistence operačního systému**.

---

### **Program a proces, multitasking a multithreading**

**Program** je pasivní entita – jedná se o soubor instrukcí uložený na disku (např. soubor `.exe`, `.py`, `.jar`).  

**Proces** je aktivní instance programu, která právě běží v paměti a je vykonávána procesorem.

> Rozdíl mezi programem a procesem lze přirovnat k vaření podle receptu:
>
> - program je jako „recept“,
> - proces je jako „vaření podle receptu“.

**Multitasking** označuje schopnost operačního systému **současně spravovat více procesů**. Ve skutečnosti procesor velmi rychle přepíná mezi jednotlivými procesy, čímž vytváří dojem, že běží současně.

**Multithreading** znamená, že jeden proces může obsahovat více **vláken (threads)**. Vlákno je menší jednotka vykonávání uvnitř procesu. 

> Grafické aplikace často využívají multithreading k oddělení vykreslování uživatelského rozhraní od zpracování dat na pozadí. Síťové servery mohou používat více vláken k obsluze současných požadavků od různých uživatelů.

Vlastnosti vláken:

- vlákna jednoho procesu sdílejí paměť,
- umožňují paralelní zpracování úloh,
- zvyšují efektivitu využití vícejádrových procesorů.

Příklad:

- webový prohlížeč může mít jedno vlákno pro vykreslování stránky,
- jiné vlákno pro načítání dat,
- další vlákno pro reakce na vstupy uživatele.

---

### **Využití paměti, ukazatele**

Během běhu programu jsou data a instrukce uloženy v **operační paměti (RAM)**.  
Paměť je rozdělena na malé adresovatelné jednotky, z nichž každá má svou **adresu**. 

Program při běhu typicky pracuje s:

- pamětí pro kód programu,
- pamětí pro proměnné a data,
- pamětí pro dočasné výpočty.

Operační systém zajišťuje, aby jednotlivé procesy:

- měly přidělen vlastní paměťový prostor,
- nemohly nelegálně přistupovat k paměti jiných procesů.

**Ukazatel (pointer)** je proměnná, která **neuchovává přímo hodnotu**, ale **adresu v paměti**, kde je hodnota uložena.

Ukazatele se používají zejména:

- při efektivní práci s pamětí,
- při dynamické alokaci paměti,
- při práci s většími datovými strukturami.

Ukazatele jsou typické především pro nižší a systémové programovací jazyky (např. C, C++). 

Ve vyšších programovacích jazycích (např. Python, Java) jsou detaily práce s pamětí většinou skryty před programátorem a spravuje je automaticky běhové prostředí (**garbage collector**) nebo virtuální stroj, což zjednodušuje vývoj, ale může omezit kontrolu nad výkonem a využitím paměti.

---

## 4. Algoritmizace, možnost zápisu algoritmů, vývojový diagram

---

### **Algoritmizace**

**Algoritmizace** je proces navrhování a vytváření algoritmů pro řešení konkrétních problémů nebo úkolů.
Cílem algoritmizace je vytvořit jasný, přesný a efektivní postup, který lze následně implementovat v programovacím jazyce.

Algoritmizace zahrnuje několik kroků:

1. **Analýza problému** – pochopení požadavků a cílů.
2. **Návrh algoritmu** – vytvoření kroků a logiky řešení.
3. **Zápis algoritmu** – vyjádření algoritmu pomocí vhodného zápisu (pseudokód, vývojový diagram).
4. **Testování a optimalizace** – ověření správnosti a efektivity algoritmu.

Existuje řada ustálených algoritmů pro běžné úlohy, jako jsou třídění (např. **bubble sort**, **quicksort**), vyhledávání (např. **binární vyhledávání**) nebo grafové algoritmy (např. **Dijkstrův algoritmus**).

---

### **Způsoby zápisu algoritmů**

Algoritmy lze zapsat různými způsoby, které usnadňují jejich pochopení a implementaci:

- **Pseudokód** – textový zápis algoritmu, který používá strukturovaný jazyk podobný programovacím jazykům, ale bez striktních pravidel syntaxe. Pseudokód je snadno čitelný a slouží jako most mezi myšlením a kódováním.
  
  Příklad pseudokódu pro výpočet faktoriálu:
  ```
  Funkce Faktorial(n)
      Pokud n == 0 nebo n == 1 pak
          Návrat 1
      Jinak
          Návrat n * Faktorial(n - 1)
  Konec Funkce
  ```
- **Vývojový diagram** – grafické znázornění algoritmu pomocí symbolů a šipek, které ukazují tok řízení mezi jednotlivými kroky. Vývojové diagramy jsou užitečné pro vizualizaci struktury algoritmu a jeho logiky.

---

### **Vývojový diagram**

Vývojový diagram (flowchart) používá různé tvary k reprezentaci různých typů operací a rozhodnutí v algoritmu.

Přehled symbolů:

- Ovál – začátek/konec
- Obdélník – procesní krok
- Kosočtverec – rozhodovací bod
- Šipky – tok řízení
- Paralelogram – vstup/výstup

Příklad vývojového diagramu pro výpočet faktoriálu:

```
   [Start]
      |
      v
   [Zadej n]
      |
      v
   [n == 0 nebo n == 1?] -- Ano --> [Návrat 1] --> [Konec]
      |
      Ne
      |
      v
   [Faktorial(n - 1)]
      |
      v
   [Návrat n * Faktorial(n - 1)]
      |
      v
   [Konec]
```

---

## 5. Základní prvky syntaxe programovacího jazyka, převod algoritmu do zdrojového kódu, typické chyby a ladění programů

---

### **Syntaxe programovacího jazyka**

**Syntaxe** je soubor pravidel, která určují, jak správně psát kód v daném programovacím jazyce. Každý jazyk má svou vlastní syntaxi, která definuje strukturu příkazů, deklaraci proměnných, použití operátorů, tvorbu funkcí a další aspekty programování.

Správnost syntaxe lze ověřit pomocí překladače nebo interpretu, který při nalezení chyby obvykle poskytne chybovou zprávu s informací o místě a typu chyby.

Důležitou roli hrají také **komentáře**, které umožňují programátorům přidávat poznámky do kódu bez ovlivnění jeho běhu (např. `// Tento řádek je komentář` v C++ nebo `# Tento řádek je komentář` v Pythonu).

**Reference na dokumentaci** jazyka je klíčová pro pochopení specifických pravidel a konvencí daného jazyka.

---

### **Převod algoritmu do zdrojového kódu**

Převod algoritmu do zdrojového kódu zahrnuje přepis kroků algoritmu do syntaxe konkrétního programovacího jazyka. Tento proces vyžaduje pochopení jak algoritmu, tak pravidel daného jazyka.

Například jazyk Python a jazyky C mají odlišnou syntaxi pro deklaraci proměnných a řízení toku. Zatímco v Pythonu se proměnné deklarují jednoduše přiřazením hodnoty (`x = 5`), v C je nutné specifikovat datový typ (`int x = 5;`). V Pythonu se bloky kódu určují odsazením, zatímco v C se používají složené závorky `{}`.

Například převod jednoduchého algoritmu pro výpočet faktoriálu do jazyka Python může vypadat takto:

```python
def factorial(n):
    if n == 0 or n == 1:
        return 1
    else:
        return n * factorial(n - 1)

print(factorial(5))  # Výstup: 120
```

Stejný algoritmus v jazyce C by vypadal takto:

```c
#include <stdio.h>

int factorial(int n) {
    if (n == 0 || n == 1) {
        return 1;
    } else {
        return n * factorial(n - 1);
    }
}

int main() {
    printf("%d\n", factorial(5));  // Výstup: 120
    return 0;
}
```

---

### **Typické chyby a ladění programů**

Při psaní kódu se mohou vyskytnout různé typy chyb, které lze rozdělit do několika kategorií:

- **Syntaktické chyby** – chyby v zápisu kódu, které porušují pravidla syntaxe jazyka (např. chybějící středník, nesprávné odsazení). Tyto chyby jsou obvykle detekovány překladačem nebo interpretem při pokusu o spuštění programu.
- **Sémantické chyby** – chyby v logice programu, kdy kód dělá něco jiného, než bylo zamýšleno (např. nesprávné podmínky, špatné výpočty). Tyto chyby mohou být obtížnější k odhalení, protože program může běžet bez chybových hlášení, ale výsledky jsou nesprávné.
- **Běhové chyby** – chyby, které se objevují během vykonávání programu (např. dělení nulou, přístup k neexistujícímu indexu pole). Tyto chyby často vedou k pádu programu nebo neočekávanému chování.

Pro ladění programů se používají různé techniky a nástroje:

- **Debuggery** – specializované nástroje, které umožňují krokování kódu, sledování hodnot proměnných a analýzu toku programu.
- **Výpisy (logování)** – přidávání výstupních zpráv do kódu pro sledování průběhu programu a hodnot proměnných v různých bodech.
- **Jednotkové testy** – psaní testovacích případů pro ověření správnosti jednotlivých částí kódu.
- **Code reviews** – kontrola kódu jinými vývojáři za účelem odhalení chyb a zlepšení kvality kódu.

Ladění je klíčovou součástí vývojového procesu a pomáhá zajistit, že program funguje správně a efektivně.