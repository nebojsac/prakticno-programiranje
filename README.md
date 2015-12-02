# Praktično programiranje
Početnički tutorijal za programiranje u PHP-u.

## Uvod
Svrha ovog teksta je da se programiranje približi apsolutnim početnicima u cilju da razbije taj prvobitni strah od nepoznatog.

Kliknite tu da preskočite do praktičnih primera

### Zašto PHP?

### Šta će vam ovaj tekst pokazati

## Podešavanje radnog okruženja

Za pokretanje PHP-a na vašem lokalnom okruženju(tj. vašem kućnom ili laptop računaru) trebaće vam Apache, a on na Windowsu dolazi u kompletu sa XAMPP. Iako je cilj ovog tutorijala da sve predstavi na srpskom, neke stvari nema smisla prevoditi, pa ću samo davati linkove ka njima. Da bi skinuli XAMPP za Windows krenite od ove adrese:

http://www.wikihow.com/Install-XAMPP-for-Windows

U pitanju je 10 koraka u slikama. Ako budete zapeli na nekom koraku, slobodno mi pišite. Nakon što ste to uradili, u browseru otvorite ovaj link da potvrdite da radi:
http://localhost
Na toj adresi bi trebalo da se pojavi //TODO

Ako ste na drugom operativnom sistemu, pristup je drugačiji. //TODO linkovi

### Program za rad

Dobar broj programera će vas religiozno ubeđivati da je njihov odabir programa najbolji. Ja vas pozivam da isprobate vremenom više njih i vidite koji vam najviše leži. Za potrebe ovog tutorijala ću vam dati i svoj predlog, a to je Sublime Text 3. On je brz, modularan i radi na svim operativnim sistemima. Ja ga koristim za sve svoje potrebe programiranja, kao i za pisanje ovog tutorijala. Na kraju dana, nije bitno kojeg odaberete, ali ako ste početnik, predložiću vam ipak Sublime Text 3, jer ću vam vremenom dati i gomilu saveta/prečica za njega. Jedina mana jeste da, ako ga koristite besplatno, dobijate povremeno popup podsetnik da ga kupite. Ja sa njim radim već koju godinu sa namerom da ga kupim već, ali očigledno me ne ometa dovoljno u radu :)

Ako vam se već na prvu ruku ne bude svideo, još neki dobri besplatni izbori su Notepad++(samo Win) i Eclipse(sve platforme).

## Počnimo sa kodom!

### Echo

Ićićemo pristupom "kucaj prvo, pitaj posle", dakle, prvo ćemo pripremiti primer, pa ćemo onda ići u objašnjavanje.
Za početak, u vašem programu za rad(u daljem tekstu "editoru") u nov prazan tab otkucajte sledeće:

```php
<?php
echo 'Dobar dan';
```
To sačuvajte(CTRL + S) i fajl stavite u vaš XAMPP htdocs folder //TODO /prakticno/ pod imenom index.php. U browseru otvorite sledeću adresu:

http://localhost/prakticno/index.php

U browseru bi trebali videti tekst "Dobar dan"(bez navodnika). Sa ovim smo potvrdili da PHP radi kod vas kako treba. A sad, prvo objašnjenje:

**<?php** označava početak PHP koda. To je "php open tag". Bez toga, sve što je u fajlu bi bilo tretirano kao običan tekst.

**echo** služi za ispis na ekran(u ovom slučaju). Posle njega možete napisati neki tekst, i staviti pod navodnike. Probajte i sami sa nečim drugim. Radi i sa jednostrukim i sa dvostrukim navodnicima. Na kraj svakog reda koda u PHP-u treba da se nalaz tačka-zarez, u suprotnom ćete dobiti grešku. (Tačnije bi bilo reći na kraju svake komande, ali nećemo komplikovati sad)

Ajmo sledeći korak. Vreme da se upoznamo sa promenljivama. Prekucajte sledeći kod u vaš index.php fajl, sačuvajte ga, i osvežite stranicu u browseru.
```php
<?php
$ime = "Nebojša";
echo 'Zdravo' . $ime;
```
**$ime** je promenljiva. Umesto "ime" tu može biti skoro bilo šta(ograničenja možete naći na netu), ali za početak ćemo se držati teksta, bez razmaka. Vežbe radi, ubacite tu svoje ime.

**Tačka(.)** se u ovom slučaju koristi za spajanje dva teksta, radi lakšeg ispisa. Ne mora biti razmak između tačke i susednih karaktera, ali ja stavljam radi preglednosti koda.

### Vežba 1 - tekst(string) i promenljive
U programiranju, za tekst se obično kaže da je on **string**, čisto da budete upoznati sa tim pojmom. **string** je ustvari niz pojedinačnih karaktera. 
**Promenljive** će vam biti glavni pojam za podatke u vašem kodu. U promenljive se pohranjuju podaci raznih tipova i veličina i koriste se za baratanje sa i poređenje tih podataka.

Prva lagana vežba u ovom tekstu će biti da uradite sledeće:
* Popravite kod za ispis imena, da ima razmak između "Zdravo" i ispisanog imena.
* Proširite rečenicu. Neka ispiše nešto kao "Zdravo Nebojša, divan dan, zar ne?"

### Uslovi 
Ne bismo daleko stigli sa samim ispisom promenljiva. Da bi naši programi radili naprednije stvari i donosili odluke na osnovu podataka, moramo imati uslove. Uslove možete vokalizovati na sledeći način **"Ako je ovaj uslov ispunjen, uradi sledeće. Ako nije, uradi nešto drugo."**. No, ajde da se bacimo na primer. Možete pisati u isti fajl za sada, kada budemo imali više materijala, rasporedićemo na više fajlova.

```php
<?php
$ime = 'Nebojša';
$brojGodina = 27;

if ($brojGodina < 18) {
	echo $ime . ', pa ti nemaš ni 18 godina!';
} else {
	echo $ime . ', pa ti si već odrasla osoba.'
}
```

Oke, imamo tu sad više novih pojmova. Za početak, imamo novu promenljivu **$brojGodina** i u nju stavljamo celi broj(tj. integer, govoreći programerski). U daljem kodu taj broj koristimo u našem uslovu i poredimo ga sa brojem 18. Kad bi vokalizovali ovaj kod, glasio bi "Ako je $brojGodina manji od 18, ispiši prvu rečenicu, u suprotnom ispiši drugu". 

Litičaste zagrade {} se koriste za odvajanje celina koda koje obuhvata neki uslov. U ovom primeru "if" i "else" deo imaju samo po jedan red koda unutar njih, ali tu obično bude i više. Kao šablon za korišćenje IF uslova, može vam koristiti ovo:
```php
<?php
if ($nekiUslov) {
	// uradi sledeće ako je uslov ispunjen
} else {
	// uradi sledeće ako uslov nije ispunjen
}
```
Vežbe radi, probajte uraditi sledeće:
* Promenite $brojGodina tako da ispiše drugu rečenicu kad osvežite stranicu.
* Zamenite dva ispisana teksta u kodu, da prvi bude za "odraslu osobu". Ispravite uslov da i dalje tačno ispisuje.

### Napredniji Uslovi
Tu može još dosta da se priča, ali za početak će biti dovoljno još par varijanti da vidimo:

TODO IF/ELSEIF

TODO AND/OR

TODO < > >= <= == [=== != !===]