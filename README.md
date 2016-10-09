# Praktično programiranje

Početnički tutorijal za programiranje u PHP-u. Autor: Nebojša Horvat Cinger


[![Pridružite se chat-u na https://gitter.im/nebojsac/prakticno-programiranje](https://badges.gitter.im/nebojsac/prakticno-programiranje.svg)](https://gitter.im/nebojsac/prakticno-programiranje?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

# Kratak Sadržaj

1. [Uvod](#uvod)
 * [Imajte na umu](#imajte-na-umu)
 * [Zašto PHP?](#zašto-php)
 * [Šta će vam ovaj tekst pokazati](#Šta-će-vam-ovaj-tekst-pokazati)
 * [Potrebno predznanje(ukratko: skoro pa ništa)](#potrebno-predznanjeukratko-skoro-pa-ništa)
 * [Potrebni programi](#potrebni-programi)
 * [Saveti za savladavanje materije](#saveti-za-savladavanje-materije)
 * [Traženje pomoći](#traženje-pomoći)
2. Podešavanje radnog okruženja
 * [Windows](poglavlja/podešavanje-radnog-okruženja.md)
 * [MacOS](poglavlja/podešavanje-radnog-okruženja-MacOS.md)
 * [Program za rad](poglavlja/podešavanje-radnog-okruženja.md#program-za-rad)
 * [Folder za rad](poglavlja/podešavanje-radnog-okruženja.md#folder-za-rad)
3. [Počnimo sa kodom!](poglavlja/pocnimo-sa-kodom.md)
 * [Echo](poglavlja/pocnimo-sa-kodom.md#echo)
 * [Uslovi (IF/ELSE)](poglavlja/pocnimo-sa-kodom.md#uslovi-ifelse)
 * [Napredniji Uslovi](poglavlja/pocnimo-sa-kodom.md#napredniji-uslovi)
  * [Ukratko o boolean vrednostima](poglavlja/pocnimo-sa-kodom.md#ukratko-o-boolean-vrednostima)
 * [Logičke operacije](poglavlja/pocnimo-sa-kodom.md#logičke-operacije)
 * [Kratak pregled tipova podataka/promenljivih](poglavlja/pocnimo-sa-kodom.md#kratak-pregled-tipova-podatakapromenljivih)
  * [Više o Boolean(istinitost)](poglavlja/pocnimo-sa-kodom.md#više-o-booleanistinitost)
  * [Malo o strogoj jednakosti](poglavlja/pocnimo-sa-kodom.md#malo-o-strogoj-jednakosti)
* [POST i GET](poglavlja/post-i-get.md)
* [Osnove nizova](poglavlja/osnove-nizova.md)
* [Pravimo digitron sa ovim što znamo](poglavlja/pravimo-digitron-sa-ovim-sto-znamo.md)
 * [Jednostavna HTML forma](poglavlja/pravimo-digitron-sa-ovim-sto-znamo.md#jednostavna-html-forma)
* [Petlje](poglavlja/petlje.md)
 * [Matematika u petljama](poglavlja/petlje.md#matematika-u-petljama)
 * [While petlja](poglavlja/petlje.md#while-petlja)
* [Datum i vreme uz date() funkciju](poglavlja/datum-i-vreme-uz-date-funkciju.md)
 * [Rad sa predefinisanim vremenima i datumom](poglavlja/rad-sa-predefinisanim-vremenima-i-datumom.md)
* [Napredniji rad sa nizovima](poglavlja/napredniji-rad-sa-nizovima.md)
 * [Nizovi i For petlja](poglavlja/napredniji-rad-sa-nizovima.md#nizovi-i-for-petlja)
 * [Nizovi i Foreach petlja](poglavlja/napredniji-rad-sa-nizovima.md#nizovi-i-foreach-petlja)
 * [Višedimenzionalni nizovi](poglavlja/napredniji-rad-sa-nizovima.md#višedimenzionalni-nizovi)
* [Funkcije](poglavlja/funkcije.md)
 * [Argumenti vs Parametri](poglavlja/funkcije.md#argumenti-vs-parametri)
 * [Variable Scope](poglavlja/funkcije.md#variable-scope)
 * [Default Values](poglavlja/funkcije.md#default-values)
 * [Return](poglavlja/funkcije.md#return)
 * [Include](poglavlja/funkcije.md#nclude)

## Teme u najavi

* [Tipični problemi](#tipični-problemi-todo)
 * Ne znam pokrenuti XAMPP
 * XAMPP radi ali "Apache" pokazuje grešku sa PORTom
 * Ne znam pokrenuti primer u browseru
 * U browseru vidim isto što u editoru
 * [Rekurzija (napredno)](#rekurzija-napredno)
* [Klase](#klase)
 * [Atributi, Metode, Vidljivost](#atributi-metode-vidljivost)

## Uvod

Svrha ovog teksta je da se programiranje približi apsolutnim početnicima u cilju da razbije taj prvobitni strah od nepoznatog. Kad se pohvataju osnovni pojmovi poput promenljivih, uslova, logičkih operacija, petlji, funkcija i klasa, lakše je i preći na bilo koji drugi jezik po potrebi.

### Imajte na umu

Ovaj tekst je "rad u toku", što znači da je nesavršen, nedovršen i da će vremenom biti unapređen. Ukoliko pronađete neke greške, ili imate neke predloge, prosledite mi ih, biću vam zahvalan. U trenutnom stanju je namenjen kao pomoćni materijal za kurs programiranja kojeg vodim. Plan je da ova dokumentacija uvek bude besplatna i dostupna svima.

### Zašto PHP?

* Lak za početi
* Brzo i jednostavno se vide opipljivi rezultati (web stranice)
* Odličan dodatak na znanje HTML-a i CSS
* Među najkorišćenijim jezicima na svetu(većina blogova i stranica na internetu, WordPress, Wikipedia, Facebook i drugi)
* Jako fleksibilan za rad i veoma popustljiv(tj. nije strog)
* I naravno, zato što je meni najbliži :)

Svako ima svog favorita, mnogi će vam reći da su Python i Javascript bolji izbori za početak. Ja smatram da je svejedno sa kojim krenete, jer kada savladate osnove i svarite neke naprednije pojmove, promena jezika postane trivijalna. 

Ja konkretno ne bih ovde da koristim Python jer je malo teži za podesiti za Windows korisnike, i jako je strog što se tiče sintakse, što dovodi do toga da više gubimo vreme na potrebe jezika u početku, nego na to da napravimo nešto što radi(neko će reći da je to prednost). A Javascript ne bih iz razloga što je cilj ove dokumentacije više da se vidi šta se dešava "ispod haube".

### Šta će vam ovaj tekst pokazati

Ideja je da svako može savladati osnovne pojmove programiranje, ma koliko mu to delovalo strano. Ovde ću preleteti neke osnovne pojmove, komande i sintakse, i usput ću davati "domaće zadatke" koje ćete rešavati sami. Naravno, ako se zapne negde, možete mi pisati, pa ćemo pogledati šta nije jasno.

Jedna napomena samo, uveliko ćemo preskakati u početku neke sigurnosne osnove radi brzine. Kada budete radili na pravim projektima biće bitno učiti o bezbednosti. Možda i jedan od budućih tekstova bude imao osvrt na to.

Ako ste polaznici kursa, ova dokumentacija će vam pomoći da nadoradite znanje iz kursa, da ga obnovite i da iste pojmove vidite objašnjene uz nove primere.

### Potrebno predznanje(ukratko: skoro pa ništa)

Za potrebe ovog teksta ću pretpostaviti da znate instalirati jednostavne programe(XAMPP), osnovni rad sa fajlovima na računaru(pravljenje foldera, kopiranje fajlova, itd) i osnovno snalaženje na internetu(google, linkovi, itd.). Sve u svemu, ako čitate ovo, verovatno već znate sve što vam treba.

### Potrebni programi

* XAMPP ako ste na Windowsu, Apache ako ste na Linuxu ili MacOS-u. 
* Program za rad sa kodom po izboru(Notepad++, Sublime Text 3 i slično).

### Saveti za savladavanje materije

* Nemojte copy/paste primere i _code_. Mnogo će vam pre ući u naviku ako *SVE* budete prekucavali. U momentima ćete imati čudne, nejasne greške, ali to je priroda posla. Umesto da kopirate _code_, probajte pronaći grešku i rešiti je.
* Nemojte preskakati sekcije. Iako nisu linearno i direktno povezane, imaćete poteškoća sa savladavanjem materije ako budete imali rupe u znanju. Što dalje budete nastavili tako, to će teže i ići. Ponovite sekciju više puta dok nije jasna, i vratite se na već pređene sekcije po potrebi.
* Ako sekcija nije jasna i posle drugog pokušaja, pišite mi. Veoma je moguće da je sekcija nepotpuna ili jednostavno nejasna. Lako mi je da preskočim neki korak koji uzimam zdravo za gotovo posle toliko godina rada, ali zato mi treba povratna informacija od *Vas* da to ispravim.
* Ako zaglavite na nekom zadatku, nemojte odmah tražiti pomoć od drugog. Probajte i sami da rešite.

### Traženje pomoći

* Obavezno pokušajte prvo sami rešiti problem. Ponovite materiju pa probajte opet.
* Ako niste uspeli rešiti, spremite se da odgovorite na sledeća pitanja:
 * "Šta si do sada probao/la?"
 * "U kom momentu(na kom redu) se dešava nešto što ti nije jasno?"