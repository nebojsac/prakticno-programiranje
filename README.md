# Praktično programiranje

Početnički tutorijal za programiranje u PHP-u. Autor: Nebojša Horvat Cinger


[![Pridružite se chat-u na https://gitter.im/nebojsac/prakticno-programiranje](https://badges.gitter.im/nebojsac/prakticno-programiranje.svg)](https://gitter.im/nebojsac/prakticno-programiranje?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

# Kratak Sadržaj

1. [Uvod](#uvod)
 * [Imajte na umu](#imajte-na-umu)
 * [Zašto PHP?](#Zašto-php)
 * [Šta će vam ovaj tekst pokazati](#Šta-će-vam-ovaj-tekst-pokazati)
 * [Potrebno predznanje(ukratko: skoro pa ništa)](#potrebno-predznanjeukratko-skoro-pa-ništa)
 * [Potrebni programi](#potrebni-programi)
 * [Saveti za savladavanje materije](#saveti-za-savladavanje-materije)
2. Podešavanje radnog okruženja
 * [Windows](poglavlja/podešavanje-radnog-okruženja.md)
 * [MacOS](poglavlja/podešavanje-radnog-okruženja-MasOS.md)
 * [Program za rad](poglavlja/podešavanje-radnog-okruženja.md#program-za-rad)
 * [Folder za rad](poglavlja/podešavanje-radnog-okruženja.md#folder-za-rad)
3. [Počnimo sa kodom!](poglavlja/pocnimo-sa-kodom.md)
 * [Echo](poglavlja/pocnimo-sa-kodom.md#echo)
 * [Uslovi (IF/ELSE)](poglavlja/pocnimo-sa-kodom.md#uslovi-ifelse)
 * [Napredniji Uslovi](poglavlja/pocnimo-sa-kodom.md#napredniji-uslovi)
  * [Ukratko o boolean vrednostima](poglavlja/pocnimo-sa-kodom.md#ukratko-o-boolean-vrednostima)
 * [Logičke operacije](poglavlja/pocnimo-sa-kodom.md#logičke-operacije)
 * [Kratak pregled tipova podataka/promenljivih](poglavlja/pocnimo-sa-kodom.md#kratak-pregled-tipova-podatakapromenljivih)
  * [Više o Boolean(istinitost)](poglavlja/pocnimo-sa-kodom.md#vise-o-booleanistinitost)
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
 * [Asocijativni nizovi](#asocijativni-nizovi)
 * [Foreach petlja](#foreach-petlja)
 * [Višedimenzionalni nizovi](#višedimenzionalni-nizovi)

## Teme u najavi

* [Tipični problemi](#tipični-problemi-todo)
 * Ne znam pokrenuti XAMPP
 * XAMPP radi ali "Apache" pokazuje grešku sa PORTom
 * Ne znam pokrenuti primer u browseru
 * U browseru vidim isto što u editoru
* [Funkcije](#funkcije)
 * [Naše funkcije](#naše-funkcije)
 * [Argumenti vs Parametri](#argumenti-vs-parametri)
 * [Povratne vrednosti](#povratne-vrednosti)
 * [Rekurzija (napredno)](#rekurzija-napredno)
* [Klase](#klase)
 * [Atributi, Metode, Vidljivost](#atributi-metode-vidljivost)

## Uvod

Svrha ovog teksta je da se programiranje približi apsolutnim početnicima u cilju da razbije taj prvobitni strah od nepoznatog. Kad se pohvataju osnovni pojmovi poput promenljivih, uslova, logičkih operacija, petlji, funkcija i klasa, lakše je i preći na bilo koji drugi jezik po potrebi.

### Imajte na umu

Ovaj tekst je "rad u toku", što znači da je nesavršen, nedovršen i nedovoljan. Ako je ovaj tekst došao do vas, pozivam vas da mi šaljete predloge, kritike i utiske na nebojsac@gmail.com, ili nađite drugi kontakt na http://nickcinger.com. Takođe, nemojte baš sa svakim deliti(npr. na fejsbuk) pogotovo u ovom nedovršenom stanju. Tretirajte ovaj fajl kao kopiju za evaulaciju/unapređenje. Radije bih da za sada ovo koriste u početku samo ljudi koji su spremni podeliti utiske samnom. A kasnije se nadam da će biti dostupno i pristupačno svima.

### Zašto PHP?

* Lak za početi
* Brzo i jednostavno se vide opipljivi rezultati (web stranice)
* Među najkorišćenijim jezicima na svetu
* Jako fleksibilan za rad, puno dopušta (što bi neki rekli da je mana, ali za učenje je prednost što se mene tiče)
* I naravno, zato što je meni najbliži :)

Svako ima svog favorita, mnogi će vam reći da su Python i Javascript bolji izbori za početak. Ja smatram da je svejedno sa kojim krenete, jer kada savladate osnove i svarite neke naprednije pojmove, promena jezika postane trivijalna. 

Ja konkretno ne bih ovde da koristim Python jer je malo teži za podesiti za Windows korisnike, i jako je strog što se tiče sintakse što dovodi do toga da više gubimo vreme na potrebe jezika u početku, nego na to da napravimo nešto što radi(neko će reći da je to prednost). A Javascript ne bih iz razloga što je meni lično zanimljivije da programiram na strani servera nego na strani browsera, a ne mogu reći da sam veliki poznavalac Node.js-a.

### Šta će vam ovaj tekst pokazati

Ideja je da svako može savladati osnovne pojmove programiranje, ma kolko mu to delovalo strano. Ovde ću preleteti neke osnovne pojmove, komande i sintakse, i usput ću davati "domaće zadatke" koje ćete rešavati sami. Naravno, ako se zapne negde, možete mi pisati, pa ćemo pogledati šta nije jasno.

Jedna napomena samo, uveliko ćemo preskakati u početku neke sigurnosne osnove radi brzine. Kada budete radili na pravim projektima biće bitno učiti o bezbednosti. Možda i jedan od budućih tekstova bude imao osvrt na to.

### Potrebno predznanje(ukratko: skoro pa ništa)

Za potrebe ovog teksta ću pretpostaviti da znate instalirati jednostavne programe(XAMPP), osnovni rad sa fajlovima na računaru(pravljenje foldera, kopiranje fajlova, itd) i osnovno snalaženje na internetu(google, linkovi, itd.). Sve u svemu, ako čitate ovo, verovatno već znate sve što vam treba.

### Potrebni programi

* XAMPP ako ste na Windowsu, Apache ako ste na Linuxu ili MacOS-u. 
* Program za rad sa kodom po izboru.

### Saveti za savladavanje materije

* Nemojte copy/paste primere i k**o**d. Mnogo će vam pre ući u naviku ako *SVE* budete prekucavali. U momentima ćete imati čudne, nejasne greške, ali to je priroda posla. Umesto da kopirate k**o**d, probajte pronaći grešku i rešiti je.
* Nemojte preskakati sekcije. Iako nisu linearno i direktno povezane, imaćete poteškoća sa savladavanjem materije ako budete imali rupe u znanju. Što dalje budete nastavili tako to će teže ići. Ponovite sekciju više puta dok nije jasna.
* Ako sekcija nije jasna i posle drugog pokušaja, pišite mi. Veoma je moguće da je sekcija nepotpuna ili jednostavno nejasna. Lako mi je da preskočim neki korak koji uzimam zdravo za gotovo posle toliko godina rada, ali zato mi treba povratna informacija od *Vas* da to ispravim.
