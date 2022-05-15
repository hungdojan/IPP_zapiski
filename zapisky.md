# Zapisky z IPP
----------

- [# Zapisky z IPP](#-zapisky-z-ipp)
- [Deleni programovacich jazyku](#deleni-programovacich-jazyku)
- [Imperativni vs deklarativni jazyky](#imperativni-vs-deklarativni-jazyky)
- [Proceduralni jazyky](#proceduralni-jazyky)
  - [Specifikace jazyku, nazvoslovi](#specifikace-jazyku-nazvoslovi)
    - [Syntaxe](#syntaxe)
    - [Semantika](#semantika)
    - [Definice a deklarace](#definice-a-deklarace)
    - [Vlastnosti promenne](#vlastnosti-promenne)
  - [Nestrukturovane jazyky](#nestrukturovane-jazyky)
    - [Datove a ridici abstrakce](#datove-a-ridici-abstrakce)
    - [Zpracovani - analyza, vyhodnoceni, preklad](#zpracovani---analyza-vyhodnoceni-preklad)
  - [Strukturovane jazyky](#strukturovane-jazyky)
    - [Formalismy a uziti](#formalismy-a-uziti)
    - [Datove a ridici abstrakce](#datove-a-ridici-abstrakce-1)
  - [Modularni jazyky](#modularni-jazyky)
    - [Formalismy a uziti](#formalismy-a-uziti-1)
    - [Datove a ridici abstrakce](#datove-a-ridici-abstrakce-2)
- [Principy objektove orientovanych jazyku](#principy-objektove-orientovanych-jazyku)
    - [Koncepty OOP](#koncepty-oop)
    - [Minimalni model vypoctu](#minimalni-model-vypoctu)
    - [Vyhoda a nevyhoda OPP](#vyhoda-a-nevyhoda-opp)
    - [Datove a ridici abstrakce](#datove-a-ridici-abstrakce-3)
    - [Tridne orientovane jazyky](#tridne-orientovane-jazyky)
    - [Polymorfismus](#polymorfismus)
  - [Prototypove orientovane jazyky](#prototypove-orientovane-jazyky)
  - [Vlastnosti objektove orientovanych jazyku](#vlastnosti-objektove-orientovanych-jazyku)
- [Deklarativni jazyky](#deklarativni-jazyky)
  - [Typy deklarativnich jazyku](#typy-deklarativnich-jazyku)
  - [$\lambda$-kalkul](#lambda-kalkul)
    - [Syntaxe](#syntaxe-1)
    - [Konvence v $\lambda$-kalkulu](#konvence-v-lambda-kalkulu)
    - [Redukce/konverze](#redukcekonverze)
    - [Relace v $\lambda$-kalkulu](#relace-v-lambda-kalkulu)
    - [Rekurze v $\lambda$-kalkulu](#rekurze-v-lambda-kalkulu)
  - [Funkcionalni programovaci jazyky](#funkcionalni-programovaci-jazyky)
    - [Data a jejich zpracovani](#data-a-jejich-zpracovani)
    - [Ridici struktury](#ridici-struktury)
    - [Preklad, interpretace](#preklad-interpretace)
    - [Zpracovani typu](#zpracovani-typu)
  - [Logicke programovaci jazyky](#logicke-programovaci-jazyky)
    - [Data a jejich zpracovani](#data-a-jejich-zpracovani-1)
    - [Ridici struktury](#ridici-struktury-1)
    - [Preklad a interpretace](#preklad-a-interpretace)

## Deleni programovacich jazyku
- Strojove orientovane jazyky
  - shluk skupin bitu a bajtu
  - psana pro cilovou architekturu
  - aritmeticke a bitove operace
  - nepodporuje vyssi abstrakci dat
- Prvni jazyky vyssi urovne
  - jednoduch datove struktury - nese obecne vlastnosti a mnozinu dostupnych operaci
  - neni urceno pro obecne pouziti
  - slozitejsi datove vztady jsou umele vytvorene (napr. seznam studentu == seznam jmena, adres apod.)
- Jazyk PL/I
  - pokus o prvni jazyk obecneho pouziti
  - komplexni
  - nemoznost definovat dalsi uzivatelske datove typy
  - neexistence klicovych slov
- Blokove strukturovane jazyky
  - Pascal
  - moznost definovat slozitejsi datove struktury a abstrakce
  - zvysuje prehlednost a citelnost zdrojoveho kodu
- Modularni blokove strukturovane jazyky
  - umoznuje oddelit definici typu od operaci, ktere ho manipuluji
  - skryva implementaci a zvysuje modifikovatelnost programu
  - DT: jmeno $\rightarrow$ modul: operace nad jmenem
- Objektove orientovane jazyky
  - rozsiruje o moznost spojit konkretni data i s operacemi
  - povoluje pristup ke svym slozkam

## Imperativni vs deklarativni jazyky
U **imperativnich** jazyku programator musi resit:
- co za operace ma byt provedeno
- v jakem poradi maji byt operace provedeny

U **deklarativnich** jazyku programator musi resit:
- co za operace ma byt provedeno

## Proceduralni jazyky
- posloupnost prikazu
- moznost vnoreni prikazu
- podpora opakovani (cykly a smycky) a variantniho vyberu (vetveni)

Typy abstrakce rizeni behu programu
- Podprogram
  - vnorene zpracovani urcitych logickych funkci/operaci
  - vola se skrze sve rozhrani (predavane parametry a vysledek)
  - podpora volani sebe sama (rekurze) a volani jinych podprogramu
- Blok
  - nema jmeno a uplatnuje se pouze v miste definice
- Ko-programy
  - pojmenovane bloky kodu, ktere jsou vzhledem k sobe symetricke
  - zpracovany soucasne/prokladane
- Paramlelni programy/procesy
  - tvori vetsi logicke celky nez ko-porgramy
  - muze dochazet k synchronizaci
- Odlozene zpracovani
  - pokud vysledek nektere operace v danem miste nemusi byt dale pouzit, tak vyhodnoce operace je pozdrzeno


### Specifikace jazyku, nazvoslovi
#### Syntaxe
*Syntaxe* definuje strukturu programu, tj. jakym zpusobem je dovoleno jednotlive konstrukce radit za sebe.
- definuje i *lexikalni* stavbu jazyka
- jde popsat slovnim popisem, syntaktickymi grafy, BNF/EBNF, nebo gramatikami.

#### Semantika
*Semantika* definuje vyznam jednotlivych syntaktickych konstrukci, zpusobu jejich vyhodnoceni, zpracovani, atd.
- Staticka semantika
  - popisuje vlastnosti, ktere mohou byt studovany a overovany v dobe analyzy/prekladu programu
    - typova kompatibilita, existence promennych
- Dynamicka 
  - popisuje vlastnosti, jejich splneni lze overit az v dobe behu programu
    - velikost indexu pole daneho vyrazem, velikost vysledku

#### Definice a deklarace
*Deklarace* uplne vymezuje atributy dane entity. Muze byt explicitni i implicitni.
*Definice* uplne vymezuje atributy dane entity a dale u promennych zpusob alokace pameti a u funkci navic telo funkce.
```c
extern int variable;                // variable declaration
int function(int, double, char *)   // function declaration (prototype)

// variable definition
int variable = 54;
// function definition
int function(int i, double d, char *s) {
    return i+(int)(d / (double)*s);
}
```

Pri definicim/deklaracim dochazi k definici vazeb mezi vytvorenou entitou a celou skupinou vlastnosti a atributu.
- behem definice samotneho jazyka - mnozina povolenych operaci nad danym typem
- behem implementace programu - prirazeni typu promenne
- behem prekladu programu - inicializacni hodnota promenne
- behem spojovani prelozenych modulu (linking) - urceni adresy objektu ciziho modulu pro pristup k nemu
- behem spousteni programu - navazani na standardni vstup
- v dobe behu programu - prirazeni adresy likalni promenne

#### Vlastnosti promenne
- Jmeno promenne
  - maximalni delka identifikatoru = maximalni pocet znaku, ktere pro danou implementaci jazyka je mozne vyuzit
  - efektivni delka identifikatoru = pocet znaku identifikatoru, ktery je skutecne zpracovan
  - tvoreno znaky abecedy, cisly a podtrzitkem
  - case sensitive $\times$ case insensitive
- Adresa a umisteni v pameti
  - L-hodnota - umisteni v pameti a adresu v ramci tohoto umisteni
  - R-hodnota - reprezentace hodnoty
  - lokalni promenne jsou ukladany na zasobnik
  - dynamicky vytvorene promenne se ukladaji na haldu (heap)
- Typ
  - urcuje mnozinu moznych hodnot a mnozinu operaci, ktere mohou byt na ni aplikovany
  - beztypove (typeless) $\rightarrow$ nema zadny typ
    - teoreticke jazyky a formalismy
  - netypovane (non-type) $\rightarrow$ typy jsou implicitni, zjistuji se za behu
    - typ neni urcen ve zdrojovem kodu
    - interpret zjistuje implicitni typove konveerze automaticky
  - typovane $\rightarrow$ typ se explicitne definuje
    - type je urcen ve zdrojovem programu u kazde entity
    - explicitni, nebo odvozeni
- Rozsah platnosti promenne
  - urcuje tu cast programu, kdy je mozne s promennou pracovat
- Doba zivota
  - casovy interval, po ktery je pro danou promennou alokovana pamet

```
_Formalni baze_ je takovy formalni prostredek (kalkul, algebra),
ktery umoznuje exaktne popsat vsechny konstrukce daneho jazyka.
Slouzi pro formalni dukaz vlastnosti jazyka.
``` 

### Nestrukturovane jazyky
- Basic, Fortran
- nema formalni bazi
- syntaxe je podana prirozenym jazykem s priklady (jednoducha)
- semantika je popsana neformalne tvorena priklady

#### Datove a ridici abstrakce
- neposkytuji datove ani ridici abstrakce
- numericke typy, pole a retezce
- smycka s pevnym krokem a ridici promennou (for cyklus)
- vetveni (if) a skok
- nelze definovat nove typy ani podprogramy
- lze pouzit pouze vestavene operace
- Otevreny podprogram
  - je ulozen v ramci hlavniho zdrojoveho textu
  - nema pevne dane rozhrani (parametry, vstupni a vystupni bod, vysledek)
  - vstup se deje skokem na prikaz, ukonceni je dano vyvolanim prislusneho prikazu
  - parametry a vysledky jsou predavany globalne, chybi podpora rekurze, slozita struktura programu
- vetsinou netypovane $\rightarrow$ explicitne se neuvadi typ, pozna se z kontexxtu
- nemoznost blokove strukturovat skupiny prikazu

#### Zpracovani - analyza, vyhodnoceni, preklad
- Analyzator
  - analyzu vstupni text v nejakem programovacim jazyce
  - provadi kontrolu textu
  - vraci seznam chyb, varovani a doporuceni
- Interpret
  - ihned vykona prikaz, pokud mu prijde na vstup
- Prekladac
  - vstupni text prevadi na posloupnost prikazu jineho jazyka

### Strukturovane jazyky
- Angol, Pascal
- nemaji formalni bazi, jazyk byl vytvoren bez uziti formalismu
- syntaxe je popsana formalni/semiformalni cestou
  - pouziti bezkontextovych gramatik (EBNF, syntakticke grafy)
- semantika je popsana neformalni cestou, propracovany
- lze uplatnit dekompozici problemu
#### Formalismy a uziti
- lze pouzit Floyd-Hoare logiku pro overeni vlastnosti algoritmu
  - zakladni konstrukce jazyka, pravidla pro praci s cisly a jejich ekvivalenty
  - kazdy prog. prvek je definovan podminkamy pred a po provedeni operace

#### Datove a ridici abstrakce
- moznost definovat typy odvozene
- *ukazatel* - adresa pametove bunky v systemu
  - umoznuje rekurzivne odkazovat urcitemu typu dat na sebe sama
- vznik uzavrenych podprogramu
  - podpora rekurze
  - ukryti implementace
  - odluka od hlavniho toku programu
- typovane $\rightarrow$ programator musi explicitne uvadet
  - typ promenne se za behu programu nemeni
  - existuji vestavene funkce pro konverzi typu
    - slabe typovane - implicitni typove konverze
    - silne typovane - explicitni typove konverze
- tvorba datove struktury
  - n-tice slozek, ktera ma jednoznacne jmeno
  - kazda slozka ma typ
  - variantni datova struktura (union) $\rightarrow$ sjednoceni jednotlivych slozek struktury
  - ukladani do pameti
    - zasadne za sebou bez mezer + zarovnani
    - union uklada slozky pres sebe
  - adresa slozky = adresa slozky struktury + offset
  - kvuli zarovnani muze v pameti vzniknout "prazdna mista" $\rightarrow$ mozno pouzit jako bitova pole
  - pole
    - homogenni datova struktura
    - je pevne indexovana urcitou hodnotou; vsechny slozky jsou stejneho typu
    - problem u pole struktur $\rightarrow$ zarovnani pameti $\rightarrow$ narocny pristupovy algoritmus
    - `a[i] = <baze> + (i-len) * sizeof(<typ>)`
    - `a[i] = <baze> - len * sizeof(<typ>) + i * sizeof(<typ>)` $\rightarrow$ prvni cast je konstanta (mapovaci funkce)
- kompatibilita typu v poli - shoda jmen a vnitrni struktury
- struktura a podprogramy
  1. nelze predavat strukturu pres parameter
  2. predani odkazem
  3. predani hodnotou
     - limitovana velikost - muze se vytvoret kopie na zasobniku/halde
- podobne i u predavani vysledku
- tok rizeni programu
  - lokalni definice promennych
  - podpora vnorovani a kombinovanost
  - smycky, podminene prikazy, prikaz nasobneho vetveni (switch/case)
  - snaha eliminovat skoky - implementace break a continue
  - 
```
_Harvardska architektura_ logicky oddeluje prostor pro data a pro ulozeni kodu programu.
$\rightarrow$ ukazatel ma 2 casti
    - adresa
    - znacka -> do jake pameti vlastne ukazuje
```

### Modularni jazyky
- Modula-2, Ada, C, ML
- moznost predavat si jiz vygenerovane moduly a navod, jak ho pouzivat - rozhrani modulu
- primarne nemaji formalni bazi
- syntaxe
  - (E)BNF
  - syntakticke grafy
  - formalni gramatika
- semantika podana neformalne a priklady pro rychlejsi pochopeni
#### Formalismy a uziti
- lze vyuzit Floyd-Hoare
- v SI se vyuziva dekompozice problemu *shora dolu*, ci *zdola nahoru*
- problemy pri praci s moduly:
  - nemoznost spojit moduly do vysledneho celku
    - spatna specifikace modulu, nevhodna dekompozice
  - kvuli spatne logice rizeni toku programu celek nepracuje spravne
  - nevhodne uziti navrhovych metodologii pro modularizaci
- moduly jsou spojene pomoci linkeru

#### Datove a ridici abstrakce
- vznik knihoven
  - sada funkci pro manipulaci s urcitym abstraktnim typem
  - implementace modulu je skryta
- tvorba rozhrani $\rightarrow$ seznam jednotlivych konsturkci, ktere mohou byt pouzity mimo modul
- Jazyk C - ma rozhrani pro deklarace promennych a funkci, nikoli typu
  - typy musi byt explicitne definovane
- moduly se skladaji do stromove hierarchie $\rightarrow$ acyklicky orientovany graf
- definice typu nejdou skryt
  - jedine pres ukazatel na typ $\rightarrow$ prinasi nove problemy
- moznost predat rizeni z jednoho modulu do druheho
- problemy s moduly (konvence):
  - predat parametry
  - vratit/prijmout vysledek funkce
  - vyuzit registry pro optimalizaci
- dusledky:
  - prirazovani registru se deje pouze v ramci funkce
  - standardizace predavani parametru
    - volany/volajici dodrzuji urcite konvence
  - standardizace predavani vysledku
    - volany/volajici dodrzuji urcite konvence
- predavani parametru
  - hodnotou/vysledkem/hodnotou a vysledkem $\rightarrow$ kopie
  - odkazem $\rightarrow$ ukazatelelm
  - jmenem $\rightarrow$ predava se dvojice pristupovych metod k dane entite: pro zapis a pro cteni
- pri sestavovani programu se pouziva *linker* - prebira nektere role prekladace
- lexikalni analyza - textovy preprocesor, ktery je spousten pred vlastnim prekladacem
- syntakticka analyza - zalozena na bezkontextovych gramatikach
  - oznaceni symbolu vyvazencyh z modulu a dovazenych do modulu
- linker - nova chybova hlaseni
  - chybejici symbol $\rightarrow$ nektery modul pozaduje symbol, ktery zadny modul nedefinuje
  - vicenasobna definice $\rightarrow$ nektery ze symbnolu je definovan vicekrat
  - rozdilne typy symbolu
- relativni kod $\rightarrow$ vazba na promenou uskutecnenou pres tabulku
  - je definovan modulem? je vyvazen?
  - neobsahuji skutecne adresy, jen odkaz do tabulky
- linker spojuje symboly mezi moduly $\rightarrow$ provadi kontroly
  - vysledkem je relokatibilni kod nebo absolutni kod
- absolutni kod
  - urceni adres vsech entit v programu a modifikace kodu, ktery na ne odkazuje
- prichazime o nektere optimalizace z duvodu chybejicich informaci behem prekladu
  - napr nezname adresu pole $\rightarrow$ musime nacist adresu a pote pridat offset = 2 akce

## Principy objektove orientovanych jazyku
- rozsireni modularnich jazyku o moznost spojit kontretni data i s operacemi, ktere je manipuluji
- zpusob abstrakce, kdy algoritmus implementujeme pomoci mnoziny zapouzdrenych vzajemne komunikujicich entit (objektu), z nichz kazda ma plnou vypocetni silu celeho pocitace
- Objektove orientovany system
  - sklada se z jednoho ci vice objektu, ktere spolu komunikuji a interaguji pri spolupraci na reseni daneho problemu
- Objekt
  - = jednoznacne identifikovatelny realny objekt nebo abstrakci
    - zahrnuje data a ajejich chovani
  - se tridami
    - instance tridy obsahujici data a operace
  - = entita, ktera rozumi zaslani nekterych zprav a ve sve vnitrni strukture umoznuje zapouzdrit dalsi objekty
  - = entita zapouzdrujici stavove informace (data reprezentovana dalsimi objekty) a poskytujici sadu operaci nad timto objektem nebo jeho casti
- vnitrni bunky - instancni promenne/atributy
  - pojmenovane datove casti objektu
- Zprava
  - komunikacni jednotka mezi objekty
  - sklada se z:
    - selektor (jmeno zpravy)
    - odkaz na prijemce (komu se zasila zprava)
    - parametry (argumenty)
  - dulezite je i odesilatel zpravy
    - neni soucasti zpravy (ulozene v zasobniku volani/kontextu)
  - prijemce hleda implementaci reakce na zpravu
    - zapouzdrena funkce = metoda
    - mnozina vsech zprav, kteremu objekt rozumi = rozhrani objektu
#### Koncepty OOP
- Objekty
  - zakladni jednotka modularity
  - spojuje data a funkcionalitu
- Abstrakce
  - schopnost programu ignorovat/zjednodusit/zanedbat nektere aspekty/vlastnosti objetku
  - pohled na vybrany problem realneho sveta
  - skryva detaily, definuje rozhrani
- Zapozdreni
  - uzivatel musi pri zmene interniho stavu dodrzovat poskytovane rozhrani
  - ostatni uzivatele komunikuji s externim rozhranim/implementace je skryta
- Polymorfismus (=mnohotvarnost)
  - konkretni pouzita metoda reagujici na zasilani zpravy zavisi na kontretnim objektu, jemuz je tato zprava zaslana
  - promenna muze behem programu odkazovat na jiny objekt
    - zasilani stejne zpravy objektu promenne muze objekt reagovat jinym zpusobem
- Dedicnost
  - zpusob, jak implementovat sdilene chovani
  - nove objekty mohou sdilet a rozsirovat chovani tech jiz existujicich
    - indikace, ze nove chovani specializuje jine jiz existujici chovani
    - sdileni kodu
- Identita
  - porovnava, zda jsou objekty ottozne; zda se jedna o tentyz objekt
- Shodnost
  - porovnava objekty podle jejich obsahu
  - shodne objekty nemusi byt identicke; identicke objekty musi byt shodne

#### Minimalni model vypoctu
- prirazeni objektu do promenne - pojmenovani
- zasilani zpravy objektu
  1. objekt nalezne implementaci zpravy a zavola prislusnou metodu
  2. objekt neobsahuje implementaci metody, ale rodic obsahuje implementaci teto metody
  3. objekt, ani jeho rodic neobsahuji implementaci teto metody
     - je vyvolana vyjimka
#### Vyhoda a nevyhoda OPP
- <span style="color:green">vyssi mira abstrakce</span>
- <span style="color:green">prirozenejsi prace se zapouzdrenim a moduly</span>
- <span style="color:green">jednodussi dekompozice problemu</span>
- <span style="color:green">udrzovatelnost a rozsiritelnost</span>
- <span style="color:green">znovu pouzitelnost</span>
- <span style="color:red">neexistence analogie s realnymi objekty</span>
  - obtizne urcit a definovat
- <span style="color:red">slozitejsi semantika</span>
- <span style="color:red">nemoznost porusovat koncepci zapouzdreni</span>
  - implementace viditelnosti
- <span style="color:red">vysledny generovany kod je pomalejsi</span>
- <span style="color:red">rezie na ulozeni objektu v pameti</span>
#### Datove a ridici abstrakce
- k popisu objektu slouzi **tridy** a **dedicnost**
  - class-based - tridni jazyky
- beztridni reseni - pouziti prototypu, rys a delegaci
  - object-based - prototypove jazyky
#### Tridne orientovane jazyky
- pouziti specialniho objektu **trida** pro spolecny popis vlastnosti objektu
- Trida
  - sablona, podle niz mohou byt vytvareny objekty (instance teto tridy)
  - stara se o spravu protokolu objektu, smerovani zprav a obsahuje implementace nekterych metod
- Instanciace objektu
  - proces samotneho vytvareni objektu
  - instance tridy = objekt naplneny instancnimi promennymi a odkazem na tridu, ze ktere vznikl
  - po vytvoreni objektu (vyhrazeni prostoru v pameti a naplneni odkazu na tridu) dostavame prazdny objekt
    - datove polozky musi byt teprve naplneny nebo inicializovany
      - pouziti konstruktoru
  - pro vytvoreni objektu se pouziva klicove slovo *new*
- dalsi moznost tvorby objektu
  - deep copy
    - krome atributu se kopiruji i objekty, ktere ony instancni promenne referencuji
  - shallow copy
    - instancni promenne obsahuji odkazy na totozne objekty jako kopirovana predloha

- Manipulace s objekty v kodu a v pameti
  - nektere jazyky (napr. C++) rozlisuji, zda se objekt nachazi na zasobniku nebo na halde
    - zasobnik - samotny datovy zaznam
    - halda - reference na objekt
  - ostatni (napr. Simula, Smalltalk) toto skryvaji; vsechno se predava pres reference

- Ruseni objektu v pameti
  - Automaticky
    - provadi *garbage collector*
    - vyhleda objekty, na ktery jiz neexistuje odkaz
    - pred zrusenim se vola finalni funkce (tzv. *finalizace*)
  - Manualne
    - programator si sam musi hlidat likvidaci
    - pri likvidaci se vola *destruktor*
      - kvuli dedicnosti se resi poradi volani *destruktoru*
- Dedicnost a hierarchie trid
  - `trida B dedi od tridy A`
  - reflexivni, tranzitivni a antisymetricka relace
- Ucel dedicnosti
  - znovupouziti definovane tridy pro specifictejsi verzi tridy
  - zajisteni zpetne kompatibility z pohledu rozhrani instance zdedenych trid
- Klasifikace dedicnosti
  - Jednoducha
    - *potomek* ma nejvyse jednoho primeho predka
  - Vicenasobna
    - *potomek* muze mit vice primych predku
    - musi se resit konflikty a duplikace jmen clenu ruznych predku
      - zakaz vyskytu konfliktnich jmen clenu nadtrid
      - uvadeni klasifikace predka, ze ktereho konfliktni metody invokovat
    - algoritmus na vyhledani metod
  - Implementace dedicnosti
    - dedi atributy a metody vcetne jejich implementace
    - ruzne implementace metod; kolize instancnich promennych
  - Dedicnost rozhrani
    - snaha vyuzit vicenasobne dedicnosti
    - seznam metod, ktere je potreba v potomkovi implementovat
- Ciste OOJ
  - vsechny entity jsou objekty; kazdy objekt ma svou tridu
    - i tridy maji svou tridu = metatridy

```
Objekt jako instance tridy
  - instancni promenne
  - trida, ktera zajistuje operace nad timto objektem
Objekt neni trida
  - instancni promenne
  - instancni metody
Objekt je trida
  - tridni promenne
  - tridni metody
```

Trida jako typ:
- podtyp (superclass)
- nadtyp (subclass)

- Vyzadana dedicnost
  - dedicny vztah zajistuje existenci potrebneho protokolu
  - kontrola jmena typu
- Skutecny podtyp
  - volnejsi nez vyzadana dedicnost
  - kontrola existence pozadovanych metod v konkretnim dosazovanem typu
  - zjistuje se za behu

- Pristupy
  - Ciste objektovy
    - vsechno je objekt
    - existuje nadtrida
  - Hybridne objektovy
    - existence primitivnich typu
      - lze skladat do homogennich a heterogennich struktur

- Staticky typovany jazyk
  - urcuje mnozinu operaci nad objektem v dobe prekladu
- Dynamicky typovany jazyk
  - kontroluje mnozinu operaci az za behu programu

- Redefinice metod = overriding
  - moznost predefinovat metodu v podtride
  - stejna signatura
- existence implicitni nebo explicitni reference na prijemce zpravy (self, this)
- reference na predka (base nebo super)

#### Polymorfismus
- umoznuje pouzivat vicero objektu na jednom miste bez zasahu do programu
- Casna vazba
  - volana metoda je jiz znama v dobe prekladu (je znama jeji adresa)
- Pozdni vazba
  - volana metoda neni znama v dobe prekladu; nevime, ktery objekt tuto metodu invokuje
  - existence *tabulky virtualnich metod*
    - staticka struktura; kazdy objekt ma na ni odkaz
    - v tabulce jsou odkazy na konkretni metody, ktere jsou pro typ platne

### Prototypove orientovane jazyky
- sklada se ze slozek objektu - *sloty*
- novy objekt se vytvari klonovanim existujicich objektu
- objekt je zrusen, pokud na nej jiz neexistuji odkazy
- Delegace
  - pokud neni nalezena metoda k invokaci v objektu prijemce, zprava je poslana do rodicovskych objektu
  - delegace nemeni kontext - prijemcem zpravy je stale originalni prijemce
- Dedicnost
  - objekty obsahujici sdilene chovani se rikaji rysy
    - sdili se metodove sloty a rodicovske sloty
  - dynamicka dedicnost -> v prubehu programu se hodnoty rodice muzou menit
- Prototyp
  - doplnime-li rysy o sloty instancnich promennych s implicitnimi hodnotami

### Vlastnosti objektove orientovanych jazyku
- silne typovane
  - neexistuje moznost, jak implicitne zpusobit typovou chybu/nekonzistenci s vyjimkou explicitni typove konverze
- slabe typovane
  - muze po kompilaci dojit k typove chybe

- Jmenny prostor
  - kontejner pro identifikatory
  - nevyskytuji se zde dva stejne identifikatory

- Modifikatory viditelnosti
  - ma za ukol menit moznost pristupu k ruznym entitam jazyka
  - soukromy (private)
    - atributy a metody jsou pristupne pouze z metody stejne tridy
  - chraneny (protected)
    - atributy ci metody jsou prisupne z metody stejne tridy a metody zdedenych podtrid
  - verejny (public)
    - atributy a metody jsou dostupne odkudkoliv

- Pretezovani metod (overloading)
  - moznost definovat ve tride vice metod stejneho jmena
  - musi mit jiny typ/pocet parametru

- Vicenasobna dedicnost
  - schopnost dedit z vice trid
  - problemy:
    - rodicovske tridy obsahuji cleny stejneho jmena i typu
      1. zakaz kolize jmen
      2. dozadovat se uprasneni, ve ktere tride volanou metodu hledat
      3. reimplementace metody
    - rodicovske tridy obsahuji cleny stejneho jmena, ale jineho typu
      1. zakaz kolize jmen
      2. povoleni v pripade, ze jazyk povoluje pretezovani
    - poradi volani konstruktoru
      1. podle zapisu ve zdrojovem textu
      2. ignorovani zapisu
         - uzivatel si definuje sam; muze dojit k deadlocku
    - ulozeni objektu tridy v pameti
      - neexistuje univerzalni reseni
- Rozhrani
  - schema, ktere deklaruje seznam metod a pripadne i nekolik nadrozhrani
  - pouziti rozhrani na jistou tridu pak vynucuje implementaci vsech metoduvedenych v rozhrani a ve vsech jeho nadrozhranich

- Vyjimky
  - moderni zpusob osetrovani chyb
    - siri informace o chybe
  - pri vyvolani vyjimky v try-bloku skoci program do catch-blocku
    - vice catch-blocku pro ruzne odpovedi na tridy vyjimek
  - finally-block, ktery se spusti vzdy

- Sablony
  - 

## Deklarativni jazyky
- vysoka abstrakce a vyjadrovaci sily
- prikazy pro vetveni toku rizeni a opakovani
- vyhodnocovaci strategie je definovan prekladacem, nebo aktualnim stavem vypoctu

Strategie vyhodnoceni a volani podprogramu
- Volani hodnotou (call-by-value)
  - parametry se vyhodnocuji pred volanim podprogramu
    - eliminuje se opakovane vyhodnoceni
  - striktni vyhodnoceni
- Volani jmenem (call-by-name)
  - parametry se predavaji nevyhodnocene - jsou reprezentovany zastupnym jmenem
  - vyhodnocuji se, az kdyz to vyzaduje volany podprogram
  - nestriktni vyhodnoceni
- Volani v pripade potreby (call-by-need)
  - parametry jsou vyhodnoceny, az kdyz jsou potreba
  - hodnota se uklada pro dalsi znovupouziti (= lazy)
  - nestriktni vyhodnoceni

### Typy deklarativnich jazyku
- (Ciste) funkcionalni jazyky
  - Haskell, Miranda, Gofer, FP, Hope, Orwell
  - formalni baze: $\lambda$-kalkul
  - zakladem je funkce z matematickeho pojeni
    - pro danou kombinaci parametru vraci vzdy stejnou vyslednou hodnotu
- Logicke jazyky
  - Prolog, Pralog, Gödel, CLP($R$), KL1 (KLIC)
  - formalni baze: predikatova logika
  - zakladem jsou klauzule, predikaty, termy apod.
- Jazyky pro definici a mianipulaci dat
  - SQL, QUEL (Query Language), QBE (Query By Example)
  - formalni baze: muze chybet; $\lambda$-kalkul
  - vazba na prirozeny jazyk
  - nejsou vypocetne uplne $\rightarrow$ nelze popsat jakykoliv algoritmus
- Jazyky s grafickym rozhranim
  - popis toku dat ci signalu (data flow, signal flow)
  - Simulink (Matlab)
  - manipulace s grafickymi entitami, jejich kombinace a propojovani liniovymi entitami

### $\lambda$-kalkul
Formalni baze pro funkcionalni programovaci jazyky.
#### Syntaxe
```
<vyraz> ::= promenna
         | (<vyraz> <vyraz>)
         | ([lambda] <promenna> . <vyraz>)
```
- Konstruktory
  - Vyraz reprezentujici identitu
    - $(\lambda x . x)$
  - Vyraz provadejici prohozeni poradi aplikace svych argumentu
    - $(\lambda x. (\lambda y . (y \,x)))$
  - Vyraz pro opakovane aplikovani funkce
    - $(\lambda f.(\lambda x.((f \,x) x )))$
- Promenne
  - definuji vazbu s okolim a reprezentuji pojmenovane entity uvnitr vyrazu
- Aplikace
  - $\lambda$-aplikace
    - `(<vyraz> <vyraz>)`
    - mame-li v aplikace 2 vyrazy $E_1$ a $E_2$, tak je mozne jeden aplikovat na druhy
      - $(E_1 \,E_2)$ - $E_1$ je operator, $E_2$ je operand
- Abstrakce
  - $\lambda$-abstrakce
    - `([lambda] <promenna> . <vyraz>)`
    - reprezentuji funkce s jednou vazanou promennou (header) a telem tvorenym $\lambda$-vyrazem

Volne a vazane promenne
$$(\lambda x.y_{volna}x_{vazana})(\lambda y.x_{volna}y_{vazana})$$
```
vaze se na prvni vyskyt lambdy nalevo
          [lambda] x . x y ([lambda] x . x) y
                   |---|             |---|
                     |                 |
                   vazba             vazba
```
$$
(\lambda \color{magenta}f\color{black}.
  (
    (\color{red}x\color{black}\
      (\lambda \color{brown}f\color{black}.
        (\lambda \color{green}x\color{black}.
          (
            (\color{brown}f\color{black} \,\color{green}x\color{black}
            )\,\color{red}y\color{black}
          )
          (\color{brown}f\color{black} \,\color{green}x\color{black}
          )
        )
      )
    )\
  \color{magenta}f\color{black})\
\color{red}w\color{black})
$$

#### Konvence v $\lambda$-kalkulu
- Aplikace je zleva asociativni
  - $E_1 E_2$         misto $(E_1 \,E_2)$
  - $E_1 E_2 E_3$     misto $((E_1 \,E_2) \,E_3)$
  - $E_1 E_2 E_3 E_4$ misto $(((E_1 \,E_2) \,E_3) \,E_4)$
- Dosah hlavicky abstrakce $\lambda V$ dosahuje nejvic doprava, jak to jen jde
  - $(\lambda V.(E_1 \,E_2 \,\dots \,E_n)) = \lambda V.E_1\,E_2\,\dots\,E_n$
- Bezprostredne vnoreni abstrakce je mozne retezit
  - $(\lambda V_1(\dots(\lambda V_n . E)\dots))$
- mozno pojmenovat vyraz - `LET ~ = <vyraz>`

$$
(\lambda f.((x\,(\lambda f.(\lambda x.((f\,x)\,y)(f\,x))))\,f)\,w)
$$
se transformuje na
$$
\lambda f.x\,(\lambda f\,x.(f\,x\,y)(f\,x))\,f\,w
$$

#### Redukce/konverze
- $\alpha$-konverze
  - $\lambda V.E = \lambda V'.E[V'/V]$
  - substituce promenne $V'$ za volne vyskyty promenne $V$ v E
    - zadna volna promenna ve vyrazu $E[E'/V]$ se nestane vazanou
- $\beta$-konverze
  - $(\lambda V.E_1)E_2$ muze byt redukovana na $E_1[E_2/V]$, pokud je substituce platna
- $\eta$-konverze
  - libovolna abstrakce tvaru $\lambda V.(EV)$, kde $V$ neni volne v $E$, muze byt redukovana na $E$.

priklady
> $\lambda x.x \rightarrow \lambda y.y$
> $\lambda x.f\,x \rightarrow \lambda y.f\,y$
> $\lambda x.\lambda y. F\,x\,y \rightarrow \lambda y. \lambda y.F\,y\,y$ - neplatne
> $(\lambda x.f\,x)\,E \rightarrow f\,E$
> $(\lambda x\,y.F\,x\,y)\,E \rightarrow (\lambda y.F\,E\,y)$
> $(\lambda x\,y.F\,x\,y)(E\,y) \rightarrow (\lambda y.F\,(E\,y)\,y)$ - neplatne

#### Relace v $\lambda$-kalkulu
- Dva vyrazy $E_1$ a $E_2$ jsou identicke, pokud jsou zapsany toutez posloupnosti znaku
  - $E_1\equiv E_2$
- Dva vyrazy $E = E'$ jsou si rovny, pokud plati:
  - $E\equiv E'$
  - existuji $E_1, \dots, E_n$ a plati:
    - $E \equiv E_1$
    - $E' \equiv E_n$
    - a muzeme na vsechny aplikovat alfa/beta/eta konverze oboustrane
    - u relace je smer jednostranny
- Zobecnena substituce
  - pokud by se behem substituce mohl objevit konflikt, ktery by zneplatnil substituci,
  - tak se provede jeste predtim $\alpha$-substituce, ktera fonfliktni promenne prejmenuje na nekonfliktni
priklad
```
  LET _TRUE_  = [l] x y.x
  LET _FALSE_ = [l] x y.y
  LET _NOT_   = [l] t.t _FALSE_ _TRUE_
  dukaz:
  _NOT_ _TRUE_ = ([l] t.t _FALSE_ _TRUE_) _TRUE_
              -> beta-konverze _TRUE_ -> [l] t.t
               = _TRUE_ _FALSE_ _TRUE_
               = ([l] x y.x) _FALSE_ _TRUE_
              -> beta-konverze _FALSE_ -> [l] x.x
               = ([l] y. _FALSE_) _TRUE_
              -> beta-konverze _TRUE_ -> [l] y
               = _FALSE_
```
#### Rekurze v $\lambda$-kalkulu
- nelze definovat rekurze `LET F = ... F ...`
- vyuziti operatoru **Y**
  - **Y** E = E (**Y** E)

### Funkcionalni programovaci jazyky
- funkce je zakladnim a jedinym vyrazovym prostredkem pro popis a definici algoritmu i dat
- Haskell, ML
- formalni baze: $\lambda$-kalkul, automaticke typove odvozeni
- syntaxe je jednoducha, neni kompletne popsana, priklady
- neformalni popis semantiky
#### Data a jejich zpracovani
- jednoduche, skalarni, slozite, slozene
- pouziti knihoven pro vlozeni abstraktnich datovych typu
- skalarni + seznamy, n-tice
  - diky silne typovosti jsou seznamy homogenni
    - `[1, 2, 3, 4, 5]`
  - n-tice jsou heterogenni datove struktury bez pojmenovani
    - `('a', 123.4, 6)`
- lze definovat vlastni typy
  - vycty, zaznamy, variantni zaznamy, rekurzivni datove typy
```Haskell
data Osoba = Osoba String String Int
data Barva = RGB Int Int Int
           | Gray Int
data Strom = List
           | Uzel Inte Data Strom Strom
```
- vstupni a vystupni operace
  - kontinuace - proudove vstupy a vystupy
    - funkce pro vstup a vystup preda parametry pro realizace vlastni operace a dale dve funkce:
      1. zbytek programu, ktery se vykona po uspechu
      2. zbytek programu, ktery se vykona po neuspechu
  - monady - vystupem I/O operaci je akce
- pole se nevyskytuji
- moznost implementace generickych algoritmu
  - podpora polymorfismu na urovni funkci
  - pouziti *typovych promennych* misto kontretni promenne
  - konkretni typ se doplni za promenou az podle parametru aplikace
#### Ridici struktury
- zakladni struktura: funkce
  - funkce lze vnorovat, lze tvorit lokalni funkce
  - deklarace neexistuji
- podpora modulu
- vetveni uplne
  - podle tela funkce
  - podle vzoru a unifikace
#### Preklad, interpretace
- Volani hodnotou
  - striktni vyhodnoceni $\rightarrow$ hodnoty vyrazu se sdili, nedochazi k vyhodnoceni pod $\lambda$-abstrakcemi
- Volani podle potreby
  - funkce se vola bez toho, ayb se vhodnotily parametry
    - parametr je vyhodnoce az tehdy, pokud telo funkce potrebuje jeho hodnotu k dalsimu postupu vypoctu
    - pouziti kontextovych obalek (context closer)
      - hodnoty, vyrazy a funkce, ktere jsou v aktualnim case volany, jsou ulozeny pro pozdejsi pouziti
    - pouziti lazy evaluation $\rightarrow$ vyrazy se vyhodnoti maximalne jednou
- interpret neexistuje
#### Zpracovani typu
- netypovane $\rightarrow$ kontroluji se na posledni chvili
- typovane $\rightarrow$ striktni typova kontrola
- typove tridy
  - shlukuji funkce a operatory do skupin

### Logicke programovaci jazyky
- zakladni struktura: predikaty, ktere pracuji nad atomy, termy ci predikaty
- Prolog, Gödel
- formalni baze: predikatova logika
- Term
  - promenna
  - vyraz $f(t_1, \dots, t_n)$, kde $f$ funkcni symbol a $t_1, \dots, t_n$ jsou termy
  - kombinace vrchnich 2 pravidel
- interpretace je modelem nejake formule
  - formule je pravdiva pro kazde ohodnoceni volnych promennych
  - formule je splnitelna, pokud existuje takova interpretace, ktera je modulem
#### Data a jejich zpracovani
- jednoduche, skalarni, slozite a slozene
- neni mnoho atomickych datovych typu
- cast programu lze sestavit az v dobe behu program samotneho
- seznamy - heterogenni $\rightarrow$ jazyky jsou netypovane
- prace s daty
  - rozpoznani a unifikace vzoru v hlavicce klauzule
    - prace s parametry predikatu
  - prevod na jiny typ
    - prevod mezi termem a netermem
  - primy pristup k termum
#### Ridici struktury
- jmeno predikatu a pocet parametru
  - pocet parametru je dulezite pri pretezovani jmen predikatu
- tok rizeni je ovlivnen vyberem predikatu/klauzuli na zaklade unifikace vzoru
```prolog
a(...) :- b1(...), ..., bm(...).
```
ekvivalence $\forall (a(\dots) \lor \neg b_1(\dots) \lor \dots \lor \neg b_m(\dots))$
- pri selhani dochazi k backtrackingu
  - vraci se zpet a hleda se lepsi cesta
#### Preklad a interpretace
- vyhodnocovaci strategie
  - SLD rezoluce
    - vstup: Hornovy klauzule
    - vyhodnocovani
      1. klauzule jsou z databaze vybirany shora dolu, dle umisteni ve vstupnim textu
      2. tela predikatu jsou zpracovana zleva doprava
```
a(...) -->> b(...), c(...), d(...).
               +->> c(...), d(...), c(...).
                       +->> d(...).
                               +->> d(...). ERROR
                               +->> e(...), d(...)
                               apod.
```
- Unifikace
  - hledani hlavicky podcile v databazi klauzuli
    - stejne jmeno a pocet parametru/datovych typu
- Nejobecnejsi unifikace
  - neexistuje zadny jiny unifikator, ktery by pro nejakou cast unifikace nabizel obecnejsi reseni
- Robinsonuv algoritmus
  - vstup: mnozina literalu
  - vystup: navrat, nejobecnejsi unifikace, selhani
```
t1 = tree(X, leaf, Y)
t2 = tree(128, Z, tree(W, U, leaf))

S1 = [128/X]
t1 = tree(128, leaf, Y)
t2 = tree(128, Z, tree(W, U, leaf))

S2 = [leaf/Z]
t1 = tree(128, leaf, Y)
t2 = tree(128, leaf, tree(W, U, leaf))

S3 = [tree(W, U, leaf)/Y]
t1 = tree(128, leaf, tree(W, U, leaf))
t2 = tree(128, leaf, tree(W, U, leaf))

S1 o S2 o S3 = [128/X] o [leaf/Z] o [tree(W, U, leaf), Y]
```