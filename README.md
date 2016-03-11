# Praktično programiranje
Početnički tutorijal za programiranje u PHP-u. Autor: Nebojša Horvat Cinger

# Kratak Sadržaj

1. [Uvod](#uvod)
 * [Imajte na umu](#imajte-na-umu)
 * [Zašto PHP?](#Zašto-php)
 * [Šta će vam ovaj tekst pokazati](Šta-će-vam-ovaj-tekst-pokazati)
 * [Potrebno predznanje(ukratko: skoro pa ništa)](#potrebno-predznanjeukratko-skoro-pa-ništa)
 * [Potrebni programi](#potrebni-programi)
 * [Saveti za savladavanje materije](#saveti-za-savladavanje-materije)
2. [Podešavanje radnog okruženja](#podešavanje-radnog-okruženja)
 * [Program za rad](#program-za-rad)
 * [Folder za rad](#folder-za-rad)
 * [Tipični problemi (TODO)](#tipični-problemi-todo)
* [Počnimo sa kodom!](#počnimo-sa-kodom)
 * [Echo](#echo)
 * [Uslovi (IF/ELSE)](#uslovi-ifelse)
 * [Napredniji Uslovi](#napredniji-uslovi)
  * [Ukratko o boolean vrednostima](#ukratko-o-boolean-vrednostima)
 * [Logičke operacije](#logičke-operacije)
 * [Kratak pregled tipova podataka/promenljivih](#kratak-pregled-tipova-podatakapromenljivih)
  * [Više o Boolean(istinitost)](#vise-o-booleanistinitost)
  * [Malo o strogoj jednakosti](#malo-o-strogoj-jednakosti)
* [Slanje podataka sa jedne stranice na drugu](#slanje-podataka-sa-jedne-stranice-na-drugu)
* [Osnove nizova](#osnove-nizova)
* [Pravimo digitron sa ovim što znamo](#pravimo-digitron-sa-ovim-sto-znamo)
 * [Jednostavna HTML forma](#jednostavna-html-forma)
* [Petlje](#petlje)
 * [Matematika u petljama](#matematika-u-petljama)
 * [While petlja](#while-petlja)
* [Datum i vreme uz date() funkciju](poglavlja/datum-i-vreme-uz-date-funkciju.md)


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

## Podešavanje radnog okruženja

Za pokretanje PHP-a na vašem lokalnom okruženju(tj. vašem kućnom ili laptop računaru) trebaće vam Apache, a on na Windowsu dolazi u kompletu sa XAMPP. Iako je cilj ovog tutorijala da sve predstavi na srpskom, neke stvari nema smisla prevoditi, pa ću samo davati linkove ka njima. Da bi skinuli XAMPP za Windows krenite od ove adrese, i obratite pažnju na putanju na koju se instalira instalira:

http://www.wikihow.com/Install-XAMPP-for-Windows

U pitanju je 10 koraka u slikama. Ako budete zapeli na nekom koraku, slobodno mi pišite. Nakon što ste to uradili, u browseru otvorite ovaj link da potvrdite da radi:
http://localhost
Na toj adresi bi trebalo da se pojavi ekran sa XAMPP for Windows porukom.

Ako ste na drugom operativnom sistemu, pristup je drugačiji, ali poenta je da namestite ili pokrenete Apache.

### Program za rad

Dobar broj programera će vas religiozno ubeđivati da je njihov odabir programa najbolji. Ja vas pozivam da isprobate vremenom više njih i vidite koji vam najviše leži. Za potrebe ovog tutorijala ću vam dati i svoj predlog, a to je Sublime Text 3. On je brz, modularan i radi na svim operativnim sistemima. Ja ga koristim za sve svoje potrebe programiranja, kao i za pisanje ovog tutorijala. Na kraju dana, nije bitno kojeg odaberete, ali ako ste početnik, predložiću vam ipak Sublime Text 3, jer ću vam vremenom dati i gomilu saveta/prečica za njega. Jedina mana jeste da, ako ga koristite besplatno, dobijate povremeno popup podsetnik da ga kupite. Ja sa njim radim već koju godinu sa namerom da ga kupim već, ali očigledno me ne ometa dovoljno u radu :)

Ako vam se već na prvu ruku ne bude svideo, još neki dobri besplatni izbori su Notepad++(samo Win) i Eclipse(sve platforme).

### Folder za rad

Ako ste na Windowsu i instalirali ste XAMPP, otvorite My Computer i idite u folder **C:\xampp\xampp\htdocs** i napravite svoj neki folder za rad, na primer "prakticno". Trebaće vam takvo neko mesto za držanje fajlova.

### Tipični problemi (TODO)

#### Ne znam pokrenuti XAMPP

#### XAMPP radi ali "Apache" pokazuje grešku sa PORTom

#### Ne znam pokrenuti primer u browseru

#### U browseru vidim isto što u editoru



## Počnimo sa kodom!

### Echo

"Kucaj prvo, pitaj posle", dakle, prvo ćemo pripremiti primer, pa ćemo onda ići u objašnjavanje.
Za početak, u vašem programu za rad(u daljem tekstu "editoru") u nov prazan tab otkucajte sledeće:

```php
<?php
echo 'Dobar dan';
?>
```
To sačuvajte(prečicom CTRL + S, ili idite na File - Save) i fajl stavite u vaš XAMPP htdocs folder C:\xampp\xampp\htdocs\prakticno\ pod imenom **index.php**. U browseru otvorite sledeću adresu:

http://localhost/prakticno/index.php

U browseru bi trebali videti tekst "Dobar dan"(bez navodnika). Sa ovim smo potvrdili da PHP radi kod vas kako treba. A sad, prvo objašnjenje:

**<?php** označava početak PHP koda. To je "php open tag". Bez toga, sve što je u fajlu bi bilo tretirano kao običan tekst.

**echo** služi za ispis na ekran(u ovom slučaju). Posle njega možete napisati neki tekst, i staviti pod navodnike. Probajte i sami sa nečim drugim. Radi i sa jednostrukim i sa dvostrukim navodnicima. 

Na kraj svakog reda koda u PHP-u treba da se nalazi tačka-zarez **;** u suprotnom ćete dobiti grešku. (Tačnije bi bilo reći na kraju svake komande, ali nećemo komplikovati sad)

**?>** označava kraj PHP koda. Generalno je neobavezan u fajlovima koji sadrže isključivo php kod.

Ajmo sledeći korak. Vreme da se upoznamo sa promenljivama. Prekucajte sledeći kod u vaš index.php fajl, sačuvajte ga, i osvežite stranicu u browseru.
```php
<?php
$ime = 'Nebojša';
echo 'Zdravo' . $ime;
?>
```
U browseru bi trebalo da vidite tekst "ZdravoNebojša".
**$ime** je promenljiva, što se u PHPu prepozna tako što ima dolar znak **$** ispred. Umesto "ime" tu može biti skoro bilo šta(ograničenja možete naći na netu), ali za početak ćemo se držati teksta, bez razmaka. Vežbe radi, ubacite tu svoje ime i osvežite stranicu.

**Tačka(.)** se u ovom slučaju koristi za spajanje dva teksta, radi lakšeg ispisa. Ne mora biti razmak između tačke i susednih karaktera, ali ja stavljam radi preglednosti koda.

U programiranju, za tekst se obično kaže da je on **string**, čisto da budete upoznati sa tim pojmom. **string** je ustvari niz pojedinačnih karaktera i predstavlja **tip** promenljive tj. podatka.

**Promenljive** će vam biti glavni pojam za podatke u vašem kodu. U promenljive se pohranjuju podaci raznih tipova i veličina i koriste se za baratanje sa i poređenje tih podataka. Zamislite to kao kutiju u koju možete staviti bilo šta. Na stranu kutije napišete šta drži, na primer **$knjiga**, i možete u nju staviti "Harry Potter", ili zameniti sa "Twilight"(_nemojte_). Promenljive se koriste za privremeno držanje podataka da bi se sa njima kasnije mogle raditi zanimljivije stvari(ispis, proračuni, odlučivanje, itd.)

Prva lagana vežba u ovom tekstu će biti da uradite sledeće:
* Popravite kod za ispis imena, da ima razmak između "Zdravo" i ispisanog imena. Zapamtite, **echo** ispisuje ono što je unutar navodnika i promenljive.
* Proširite rečenicu. Neka ispiše nešto kao "Zdravo Nebojša, divan dan, zar ne?". Možete proširiti postojeći red koda, ili dodati novi ispod.

### Uslovi (IF/ELSE)
Ne bismo daleko stigli sa samim ispisom promenljiva. Da bi naši programi radili naprednije stvari i donosili odluke na osnovu podataka, moramo imati uslove. Uslove možete vokalizovati na sledeći način **"Ako je ovaj uslov ispunjen, uradi sledeće. Ako nije, uradi nešto drugo."**. No, ajde da se bacimo na primer. Možete pisati u isti fajl za sada, kada budemo imali više materijala, rasporedićemo na više fajlova.

```php
<?php
$ime = 'Nebojša';
$brojGodina = 27;

if ($brojGodina < 18) {
	echo $ime . ', pa ti nemaš ni 18 godina!';
} else {
	echo $ime . ', pa ti si već odrasla osoba.';
}
?>
```

Oke, imamo tu sad više novih pojmova. Za početak, imamo novu promenljivu **$brojGodina** i u nju stavljamo celi broj(tj. integer, govoreći programerski). U daljem kodu taj broj koristimo u našem uslovu i poredimo ga sa brojem 18. Kad bi vokalizovali ovaj kod, glasio bi "Ako je $brojGodina manji od 18, ispiši prvu rečenicu, u suprotnom ispiši drugu".

Litičaste zagrade ```{}``` se koriste za odvajanje celina koda koje obuhvata neki uslov. U ovom primeru "if" i "else" deo imaju samo po jedan red koda unutar njih, ali tu obično bude i više. Kao šablon za korišćenje IF uslova, može vam koristiti ovo(dve kose crte // označavaju redove sa komentarima u kodu, koji se ne izvršavaju):
```php
<?php
if ($nekiUslov) {
	// uradi sledeće ako je uslov ispunjen
} else {
	// uradi sledeće ako uslov nije ispunjen
}
?>
```

Takođe, kao što vidite, kad su neki redovi koda deo neke celine, ili nekog uslova, onda ih "uvučemo" za jedan TAB(to vam je to dugme na tastaturi iznad CAPS LOCK-a). Iako to nije obavezno da bi kod radio, to je standard jer olakšava pregled strukture koda.

U uslovu koristimo matematičko poređenje "manje od", tj. simbol <. Neki drugi simboli za poređenje su:
* > "veće od"
* == "jednaka vrednost"
* != "različita vrednost"
* >= "veće ili jednako"
* <= "manje ili jednako"
* === "stroga jednakost", malo napredniji pojam kojeg ćemo ostaviti za kasnije.

Vežbe radi, uradite sledeće:
* Promenite **$brojGodina** tako da ispiše drugu rečenicu kad osvežite stranicu.
* Zamenite dva ispisana teksta u kodu, da prvi bude za **"odraslu osobu"**. Izmenite uslov da ispisuje tačnu rečenicu na osnovu broja godina.

### Napredniji Uslovi
Tu može još dosta da se priča, ali za početak će biti dovoljno još par primera uslova.

```php
<?php
$razred = 1;
$skola = '';

if ($razred <= 8) {
	$skola = 'osnovna škola';
} elseif ($razred <= 12) {
	$skola = 'srednja škola';
} elseif ($razred > 12) {
	$skola = 'fakultet';
}
echo $razred . '. razred je ' . $skola . '.';
?>
```

Novost ovaj put je **elseif** uslov. Logika ovde je takva da se prvo proveri uslov "manje ili jednako sa 8", pa ako taj uslov nije ispunjen, ide na sledeći, "manje ili jednako sa 12", i tek ako ni taj nije ispunjen, stiže na poslednji uslov "veće od 12". Ako ni poslednji uslov nije ispunjen, izlazimo iz ovog grananja, ništa od komandi unutar ovih uslova neće biti pokrenuto. Da smo stavili još na kraj običan **else** bez ikakvih dodatnih poređenje, onda bi komande unutar tog **else** bloka bile pokrenute samo ako ni jedan prethodni uslov nije ispunjen.

Vežbe vezane za ovo:
* Menjajte promenljivu **$razred**, tako da vidite sve moguće rečenice.
* Zašto smo morali koristiti "manje ili jednako" simbol <= umesto običnog "manje" simbola? 
* Ako bismo promenili prvi i drugi uslov tako da koriste simbol za manje <, koje vrednosti bi mogli staviti u **$razred** da na kraju **$skola** ostane prazan string ''?

#### Ukratko o boolean vrednostima

Boolean je binarni tip promenljive, što znači da obuhvata samo dve moguće vrednosti. Najtačnije je predstaviti ih sa ```true``` i ```false```, ali ekvivalenti su i ```1``` i ```0```. Možete o njima misliti kao o tačnosti, "istinito" i "neistinito", "tačno" i "netačno", "da" i "ne". 

Iako trenutno ne znate šta su boolean vrednosti, vi ste već baratali sa njima. Kao što matematičke operacije daju određene brojčane vrednosti, tako operacije poređenja ```<,>,==,<=,>=,!=``` daju boolean vrednosti. 

```php 
<?php
$razred = 1;
echo $razred . '<br />'; // 1
var_dump($razred); // var_dump je funkcija koja pred vrednosti ispiše i tip vrednost: integer(1) u ovom slučaju

$razred = ($razred + 2);
var_dump($razred); // integer(3)

$osnovnaSkola = ($razred < 9);
var_dump($razred); // boolean(true) - u ovom slučaju dobijamo vrednost "true" zato što je poređenje tačno, 3 je manje od 9. 

if ($osnovnaSkola) {
	echo '<br />Osnovna skola je u pitanju';
} else {
	echo '<br />Nije osnovna skola u pitanju';
}
?>
```
Treba obratiti pažnju na ekvivalente boolean vrednosti. Kada stavimo neku vrednost u uslov, odnosno u ```if()``` i slične funkcije, ta vrednost se pretvara u boolean za potrebe "odlučivanja" u toj funkciji. Na primer, ```1``` je isto što i ```true```, a ```0``` isto što i ```false```. Prazan string, ```$prazno='';``` tj tekst koji je ustvari "ništa" se tretira kao ```false``` a bilo kakav drugi tekst kao ```true```. Sa tim na umu, sledeće je validan kod.

```php 
<?php
$broj = 1; // promenite ovo u 0 i u druge brojeve, da vidite rezultate

if ($broj) {
	echo 'broj nije nula';
} else {
	echo 'broj je nula';
}
?>
```
### Logičke operacije

E sad dolazi jedna od meni zanimljivijih pojmova. Šanse su da ćete se sa ovim često susretati, a ponekad sa veoma komplikovanim i dugačkim uslovima, pa bi vredelo da se zadržite na ovom poglavlju dok ga ne savladate.

Poenta "IF/ELSE" blokova je donošenje odluka u kodu na osnovu podataka. Tipični primer je sistem za Login(prijavljivanje) na sajtovima u kojem se unešeni podaci porede sa podacima iz baze. Ali za takav primer nam trebaju još neka znanja koja će tek kasnije doći, pa ćemo se za sada skoncentrisati na neke pristupačnije primere. Zato u zadacima koje radimo podaci budu upisani pri početku programa, gde bi inače bili dobijani iz drugih izvora(iz baze, sa forme itd).

Ako niste imali predmete poput Digitalne Tehnike ili Računarstva, mnogo ovog će vam delovati strano, ali verujte mi da se svodi na par jednostavnih pravila, i da ima smisla kada vokalizujete kod. 

```php
<?php
$razred = 1;
$skola = '';

if ($razred >= 1 AND $razred <= 8) {
	$skola = 'osnovna škola';
} 

if ($razred >= 9 AND $razred <= 12) {
	$skola = 'srednja škola';
} 

if ($razred >= 13 AND $razred <= 16) {
	$skola = 'fakultet';
}

if ($razred < 1 OR $razred > 16) {
	$skola = 'nedefinisana skola';
}

echo $razred . '. razred je ' . $skola . '.';
?>
```
Namerno smo ponovili (pomalo neprecizan) primer od malopre, i namerno smo odvojili if/elseif uslove u zasebne if uslove, da biste videli da je logika slična. Par novih pojmova, pa da ih pređemo:

* **AND** je logički operater sa bukvalnim prevodom **i**. Kada ga stavimo između dve vrednosti, on vraća "tačno" odnosno **true** vrednost ako su vrednosti sa obe strane njega tačne, tj istinite. Npr. ako je razred "5" onda čitate "Ako je razred(5) veći ili jednak sa 1, **i** ako je razred(5) manji ili jednak sa 8, tada je uslov ispunjen".

* **OR** je logički operater čiji prevod je **ili**. Kada ga stavimo između dve vrednosti, dovoljno je da makar jedna od njih bude tačna, to jest **true**, da bi ukupan uslov bio tačan.

* Naišli smo na nov pojam, a to je tačnost. Dotaćiću se ovoga još kasnije, ali za sada je dovoljno da znate da je to novi tip vrednosti zvan **boolean**, kojeg ćemo za potrebe ovih vežbi nazivati "tačnost". Moguće vrednosti su **true** i **false**, koje dobijamo nakon logičkih operacija. Drugi tipovi vrednosti imaju ekvivalente, na primer, jedinica **1** je isto što i **true** kad se stavi u uslov, a nula **0** je isto što i **false**.

* Gore navadeni AND i OR se mogu koristiti kombinovano više puta u uslovima, a postoje i XOR i NOR koje nećemo sada prelaziti. Kod komplikovanijih uslova je korisno stavljati zagrade () radi lakšeg odvajanja logičkih celina.

Vežba će biti vezana za sledeći kod:
```php
<?php
// prvi:
if ((true AND false) AND true) {
	echo 'true';
} else {
	echo 'false';
}

// drugi:
if ((true AND true) AND true AND (false OR true)) {
	echo 'true';
} else {
	echo 'false';
}

// treći:
if (false OR (true AND false))) {
	echo 'true';
} else {
	echo 'false';
}
?>
```
* Pre nego što pokrenete kod, šta će biti ispis?
* Kod drugog uslova, šta možemo promeniti od booleana, da bi uslov bio **false**?
* Da li vam je jasno šta se tu dešava? Ako bi zamenili svaki **true** sa **(3 > 1)**, da li bi to promenilo prvobitni ispis? Zašto?

### Kratak pregled tipova podataka/promenljivih

```php
<?php
$broj = 13; 					// integer

$tekst = 'Ma šta mi napriča?!'; // string

$istinitost = true;				// boolean

// ostali tipovi:
$brojSaDecimalom = 3.14;		// float

$niz = array(1, 2, 5, 16);		// array

$prazno = null;					// NULL
?>
```
**integer** je celi broj. Može biti i negativan.
**string** je tekst. 
**boolean** je binarna istinitost, da ili ne, **true** ili **false**.
**float** je broj sa decimalom.
**array** je niz podataka odjednom. Može biti i višedimenzionalni.
**null** je "ništa". Nije 0, nije prazan tekst '' i nije prazan niz array(). Jednostavno, ništa. Često i rezultat grešaka u izvršavanju.

#### Više o Boolean(istinitost)

Boolean vrednosti su super kada trebate pratiti binarna stanja. Primeri bi bili $otvoreno, $aktivan, $obrisano, $blokiran. Bilo šta što može imati vrednosti "da" i "ne", odnosno **true** i **false**.

E sad, vredi skrenuti pažnju na to da svaka vrednost ima svoju ekvivalentnu Boolean vrednost. Na primer, 0 je jednaka **false** dok je bilo koji broj veći od nule jednak **true**. Prazan niz ili string su **false**, a ako nisu prazni onda su **true**. Ne znači vam to puno ovako nasuvo, ali trudiću se da ubacujem ovo u buduće primere, da vidite šta se dešava.

#### Malo o strogoj jednakosti

Dva znaka jednakosti **==** se koriste kada poredimo dve vrednosti, i to je često sasvim dovoljno, ali morate biti svesni da ima ograničenja i neočekivana ponašanja. Jedan tipičan primer:
```php
<?php
if (0 == '') {
	echo 'Jednaki su';
}
?>
```
Kao što sam spomenuo za istinitost, nula je ekvivalentno **false**, kao i prazan string, dakle, u ovom slučaju, su jednaki. Ako ne budete svesni toga uješće vas za dupe! Najbolji način da izbegnete ovu, i druge slične situacije, jeste da koristite strogo poređenje **===**. 

**===** poredi i **tip** i **vrednost**, za razliku od == koje samo poredi vrednost. String sa nulom '0' i integer nula 0 nisu jednaki kad se porede sa njim. Generalno je bolje da koristite taj vid poređenja. Isto tako imate strogo poređenje nejednakosti **!==**, kao i obično poređenje nejednakosti **!=** koji imaju svoju svrhu.
```php
<?php
if (0 !== '') {
	echo 'Nisu jednaki.';
}
?>
```

## Slanje podataka sa jedne stranice na drugu

O ovome se može dosta pisati, ali ovo će biti dovoljno za početak:

**POST** metoda slanja podataka na drugu stranu obično znači da se podaci šalju preko neke html forme, poput Login-a za neki sajt. Forma mora biti i podešena da koristi POST metodu. Primer forme za slanje, i PHP koda za primanje, POST podataka:
```php
<form method="POST">
	username:<input type="text" name="username" placeholder="korisničko ime"/>
	password:<input type="password" name="password" />
	<input type="submit" value="Pošalji" />
</form>
<?php
$username = $_POST['username'];
$password = $_POST['password'];

// ta dva reda gore će izbacivati grešku ako ti podaci ne postoje. Da se to izbegne koristite:
if (isset($_POST['username'])) { // isset() funkcija vraća "false" boolean ako ne postoji dati podatak
	$username = $_POST['username'];

	echo '<br /> $username je :' . $username;
} 
if (isset($_POST['password'])) {
	$password = $_POST['password'];

	echo '<br /> $password je :' . $password;
} 
?>
```

Pvi deo predstavlja HTML code. U vašem browseru bi trebalo da se pojave ta dva polja koja su tipična za mnoge sajtove koja možete koristiti za testiranje ovog gore k**o**da. Od svega toga, za sada, treba samo da znate vezu između tih polja i php k**o**da za ispis. Nećemo se mnogo zadržavati na ovome:
* Pojedinačni html "tagovi" se nalaze između ```<``` i ```>```. Npr ```<form>```. 
* Tagovi označavaju početak i kraj nekog elementa. Tag za zatvaranje počinje sa ```</```, npr ```</form>```.
* Svaki element se sastoji iz taga za otvaranje i taga za zatvaranje(```<form><form>```) ali se može pisati skraćeno tako što se na kraj prvog taga stavi ```/>```, npr: ```<input type="text" />``` ili ```<br />```.
* Elementi mogu imati atribute. Npr, u ovom elementu ```<input type="password" name="password" />``` atributi su ```type``` i ```name```. 
* ```type``` atribut nam govori kog je tipa ovo polje za unos. Ako je ```text``` onda vidimo šta pišemo. Ako je ```password``` onda ne vidimo dok unosimo tekst, odnosno šifru.
* ```name``` nam govori naziv ```$_POST``` promenljive kada se podaci pošalju. Npr, ako za ```<input type="password" name="password" />```, do sadržaja tog polja posle slanja ćemo doći uz pomoć ```$_POST['password']```. U pitanju je promenljiva tipa "niz", ali više o tome posle.

Ova poslednja stavka vam je jedina bitna za sada, ali zato je i pročitajte ponovo.

U gornjem primeru koristimo novu funkciju, ```isset()```. Ona se koristi za proveru postojanja neke promenljive ili nekog podatka. Da bi bolje razumeli to, pogledajmo sledeći k**o**d:

```php
<?php

$godina = 2016;

if (isset($godina)) {
	echo 'Promenljiva $godina postoji.';
} else {
	echo 'Promenljiva $godina postoji.';
}

echo '<br />';

if (isset($mesec)) {
	echo 'Promenljiva $mesec postoji.';
} else {
	echo 'Promenljiva $mesec postoji.';
}
?>
```
Pokrenite taj primer da vidite šta se ispiše. Ako pogledate ```isset($godina)```, to se može čitati kao "Da li je postoji promenljiva $godina?", odnosno "Da li je setovana/podešena?". ```isset()``` funkcija kao takva vraća istinitost(boolean), dakle, ```true``` ili ```false```. Ako promenljiva postoji, vraća ```true```. U ovom primeru smo podesili promenljivu ```$godina``` na početku, dakle, ona postoji. Ali promenljivu ```$mesec``` nismo nigde podesili, dakle, ona ne postoji. ```isset()``` se najčešće koristi kod slanja podataka POST i GET metodom, radi provere.

**GET** metoda slanja podataka je praktično slanje podataka kroz adresu stranice. Obratite pažnju koja je adresa u browseru gde testirate kod. Verovatno počinje sa ```localhost``` jer radite u Xampu, pa onda sledi ```/folder/``` ili ```/prakticno/```, nakon čega je fajl u kojem radite, poput ```test.php```, ```index.php``` ili ```get.php```. Primera radi, ako imate adresu koja se završava sa get.php, vi na nju možete nakačiti još podataka preko GET metode koristeći upitnik pre prvog podatka, i ampersand **&** pre svakog sledećeg. Pretpostaviću da vam je ovaj code na adresi http://localhost/prakticno/get.php - Primer bi bio adresa http://localhost/prakticno/get.php?id=123&action=edit. U tom slučaju možete pristupiti podacima uz ovaj kod:

```php
<?php
if (isset($_GET['id'])) { // isset() funkcija vraća "false" boolean ako ne postoji dati podatak
	$id = $_GET['id'];
} else {
	$id = 0;
}
if (isset($_GET['action'])) {
	$action = $_GET['action'];
} else {
	$action = 'neispravan';
}

echo '$id je ' . $id;
echo '<br />';
echo '$action je' . $action; 
?>
```

Na ekranu bi trebalo da vidite ```$id je 123``` i ```$action je edit```. Ako vidite ```$id je 0``` i ```$action je neispravan``` onda ste zaboravili dodati ```?id=123&$action=edit``` na kraj adrese u browseru. Da probamo još malo pojasniti šta se tu dešava:

? - sa upitnikom označavamo da je ovo kraj imena fajla (get.php, ili štagod) i da tu počinju ```GET``` promenljive. 
GET promenljive idu u parovima ```ime``` i ```vrednost```, odnosno ```ime=vrednost```. Pod ```ime``` bi bilo tačnije reći ```index```, ali možete reći da vam je taj levi deo jednakost ```ime=vrednost``` oznaka ```GET``` promenljive. Sa desne strane te jednakost ide vrednost koju dodeljujete. Dakle, ako imate adresu ```get.php?ime=vrednost```, onda toj ```GET``` promenljivoj pristupate na sledeći način:

```php
<?php
echo $_GET['ime'];
?>
```
Promenite sad ```ime``` u adresi u nešto drugo, npr ```broj```, i isto to stavite u kod ```echo $_GET['broj'];```, da vidite o čemu pričam. Sad menjajte desnu stranu jednakosti u neki broj, i opet osvežite stranicu, da vidite kako se menja. 

Isto tako možete imati više ```GET``` promenljivih u adresi, npr: http://localhost/prakticno/get.php?http://localhost/prakticno/get.php?id=123&action=edit&ime=Stevo. Svaka ```GET``` promenljiva se odvaja sa ```&``` od prethodne, znači ```?id=123&action=edit&ime=Stevo```. Sad ću odvojiti GET promenljive da bude malko preglednije, ali i neispravno: ```? id=123 & action=edit & ime=Stevo```. Da vidimo šta se tu dešava, ubacićemo ih sve u echo:
```php
<?php
echo 'id: ' . $_GET['id'];
echo '<br />'; // ovo je samo novi red radi preglednosti
echo 'action: ' . $_GET['action'];
echo '<br />';
echo 'ime: ' . $_GET['ime'];
?>
```

Ovaj kod ispisuje vrednosti GET promenljivih, ako ih ima, ali će izbaciti greške ako one ne postoje. Zato koristimo isset() funkciju iz prvog koda:
```php
<?php
if (isset($_GET['id']) AND isset($_GET['action']) AND isset($_GET['ime'])) {
	echo 'id: ' . $_GET['id'];
	echo '<br />'; // ovo je samo novi red radi preglednosti
	echo 'action: ' . $_GET['action'];
	echo '<br />';
	echo 'ime: ' . $_GET['ime'];
} else {
	echo 'Nesto fali';
}
?>
```
Ako na ekranu piše ```Nesto fali```, onda morate proveriti da li u adresi u browseru imate sve tri promenljive. isset() funkcija proverava da li određena promenljiva postoji, i vraća ```true``` ili ```false``` na osnovu toga. U ovom primeru ćemo ispisati sve promenljive samo ako save promenljive postoje. Ako bilo koja fali, ispisaće ```Nesto fali```. Probajte sledeće:

* Ubacite svoje ime u promenljivu ```ime```
* Zamenite promenljivu ```action``` sa promenljivom ```akcija```, a vrednost joj promenite u ```izmena```.
* Dodajte još jednu GET promenljivu na adresu i ispišite je na ekranu sa kodom.
* Vežbajte. Počnite sa novim fajlom, od nule, nek se zove ```getproba.php```. Napišite prvo k**o**d koji ispisuje vrednost GET promenljive ```boja```. Stavite taj k**o**d za ispis unutar **if** bloka koji proverava da li ta promenljiva postoji. Ako ne postoji, nek se ispiše ```ne postoji```. Isprobajte vaš k**o**d sa i bez GET promenlijve ```boja```. 

Postoje situacije u kojima je obavezno koristi POST metoda, poput registracije i logina, i situacije u kojima je bolje koristiti GET metodu, kao što je izlistavanje podataka, pretraga, itd.

**NAPOMENA** podaci koji su primljeni preko POST ili GET metode obavezno tretirati kao nebezbedne. Maliciozni korisnici mogu da menjaju njihov sadržaj i jedan su od najlakših načina da se hakuje sajt ako nije zaštićen. Srećom, nije se teško obezbediti od toga, samo treba imati ovo na umu. Bezbednost ćemo kasnije pokriti.

## Osnove nizova

Čisto da bi razumeli šta se tu dešava da spomenemo nizove(eng. arrays). Niz je skup podataka i možete ga držati u jednoj promenljivoj. Podaci su takoreći **indeksirani** i pristupa im se na osnovu tih indeksa koji mogu biti brojevi ili stringovi(odnosno tekst). Neki jednostavniji primeri koje možete kod sebe isprobati:

```php
<?php
// u ovom slučaju, niz bude automatski indeksiran brojevima, redom kojem su upisani u niz
$neparniBrojevi = array(1,3,5,7,9);

// ovaj gore automatski indeksiran niz je identičan sledećem:
$neparniBrojevi = array(0 => 1, 1 => 3, 2 => 5, 3 => 7, 4 => 9);

// čitljivije je ako takav niz pišemo u više redova:
$neparniBrojevi = array(
	0 => 1, 
	1 => 3, 
	2 => 5, 
	3 => 7, 
	4 => 9
);


// ispis celog niza na ekran:
print_r($neparniBrojevi);

// ispis prvog elementa(tj. broja) u nizu:
echo $neparniBrojevi[0]; // Indeksiranje kreće od nule. Ovaj kod će ispisati broj 1
echo $neparniBrojevi[1]; // Ispisaće broj 3

// programatično ispisivanje niza:
// Funkcija count() vraća broj elemenata u nizu, što nam govori koliko dugo da budemo u petlji
for ($i = 0; $i <= count($neparniBrojevi); $i++) {
	echo $neparniBrojevi[$i];
}

// Nizovi mogu biti indeksirani tekstom, kao npr:
$neparniBrojevi = array(
	'jedan' => 1, 
	'tri' => 3, 
	'pet' => 5, 
	'sedam' => 7, 
	'devet' => 9
);

// Takav niz ne možemo ispisati sa gornjim for() primerom, ali vratićemo se na to. Za sada možemo ovako ispisati:
print_r($neparniBrojevi);

// A možemo i pojedinačne elemente ispisati koristeći njihov indeks. Na primer:
echo $neparniBrojevi['tri']; // 3


?>
```
Poenta ovog pregleda je da su POST i GET promenljive nizovi, i sva pravila nizova važe i za njih. To je sve što trebate znati vezano za nizove za sledeći zadatak, a kasnije ćemo se vratiti na rad sa nizovima.


## Pravimo digitron sa ovim što znamo

### Jednostavna HTML forma

Ne želim puno da se zadržavam na HTML-u za sada, ali da bi prestali čačkati promenljive u codu(a ne želim da radimo u terminalu) trebamo koristi HTML forme. Prekopirajte sledeći k**o**d kod vas u index.php:
```php
<html>
	<head>
		<title>HTML Calculator</title>
	</head>
	<body bgcolor= "#000000" text= "gold">
		<form name="digitron" action="index.php" method="POST">
			<input type="text" name="prvaPromenljiva" placeholder="Prva Promenljiva" />
			<input type="text" name="drugaPromenljiva" placeholder="Druga Promenljiva" />
			<br />

			<input id="operacija1" type="radio" name="operacija" value="+" /> <label for="operacija1">Sabiranje</label>
			<br />
			<input id="operacija2" type="radio" name="operacija" value="-" /> <label for="operacija2">Oduzimanje</label>
			<br />
			<input id="operacija3" type="radio" name="operacija" value="*" /> <label for="operacija1">Množenje</label>
			<br />
			<input id="operacija4" type="radio" name="operacija" value="/" /> <label for="operacija4">Deljenje</label>
			<br />

			<input type="submit" value="Izračunaj" />
			<input type="reset" value="Reset">
		</form>

		<br />
		Rezultat je:
		<?php 

		if (isset($_POST)) {

		}

		?>
		 
	</body>
</html>
```

Ok, ićićemo redom sad. HTML formu više nećemo dirati, sad ćemo raditi na sa PHP codom, korak po korak. znači, trenutno stanje je:
```php
<?php 

if (isset($_POST)) {

}
?>
```

Ovaj kod se sastoji samo od jedne jedine provere, a to je, kad bi vokalizovali "Da li postoji $_POST promenljiva?". Ako postoji, znači da smo slali podatke POST metodom uz pomoć forme. Ako ne postoji, verovatno smo tek učitali stranicu. Unutar ovog IF uslova ćemo dalje raditi na logici.

Sledeći korak jeste da uhvatimo sve podatke sa forme:
```php
<?php 

if (isset($_POST)) {

	$prvaPromenljiva = $_POST['prvaPromenljiva'];
	$drugaPromenljiva = $_POST['drugaPromenljiva'];
	$operacija = $_POST['operacija'];
}
?>
```

Ovo je suvo da suvlje ne može. To je minimalan kod koji radi što smo tražili: hvata podatke sa forme. Ali to nije dovoljno, moramo i neke provere da uradimo. Za početak, dodaćemo proveru dal su svi podaci poslati:

```php
<?php 

if (isset($_POST)) {

	if (isset($_POST['prvaPromenljiva']) AND isset($_POST['drugaPromenljiva']) AND isset($_POST['operacija'])) {
		$prvaPromenljiva = $_POST['prvaPromenljiva'];
		$drugaPromenljiva = $_POST['drugaPromenljiva'];
		$operacija = $_POST['operacija'];
	} else {
		echo 'Greška! Nisu svi podaci poslati';
	}
}
?>
```
Da se podsetimo, **isset()** vraća **true** ako dati podatak postoji. Dakle, ako su sve tri POST promenljive poslate, nastavićemo sa radom. Ako nisu, ispisaćemo grešku. Takođe isset() podržava proveru više promenljivih odjednom, npr. isset($a, $b, $c), što pomaže čitljivosti.

Dakle, potvrdili smo da su podaci poslati. Ajde da proverimo da li imaju smisla. Želimo da budemo sigurni da su promenljive brojevi(a ne slova) a da "operacija" spada u jednu od operacija koje imamo na formi:

```php
<?php 

if (isset($_POST)) {

	if (isset($_POST['prvaPromenljiva']) AND isset($_POST['drugaPromenljiva']) AND isset($_POST['operacija'])) {
		$prvaPromenljiva = $_POST['prvaPromenljiva'];
		$drugaPromenljiva = $_POST['drugaPromenljiva'];
		$operacija = $_POST['operacija'];

		$dozvoljeneOperacije = array('+', '-', '*', '/');

		if (is_numeric($prvaPromenljiva) AND is_numeric($drugaPromenljiva) AND in_array($operacija, $dozvoljeneOperacije)) {
			// operacije idu tu
		} else {
			echo 'Greška! Poslati podaci nisu validni.';
		}

	} else {
		echo 'Greška! Nisu svi podaci poslati';
	}
}
?>
```
Da vidimo šta smo gore uradili imamo dve nove funkcije: is\_numeric() proverava dal je vrednost broj. A in\_array() proverava proverava da li se prvi parametar nalazi u drugom parametru. Definisali smo promenljivu $dozvoljeneOperacije kao niz operacija koje očekujemo i proveravamo dal je poslata $operacija jedna od njih. Ovo je i koristan pristup sigurnosti, jer se POST i GET podacima ne može verovati i u njima maliciozni korisnik može da pošalje šta god poželi. Zbog toga su provere bitne.

Radi preglednosti, izdvojiću samo k**o**d za operacije u sledećih nekoliko navrata. Možete smatrati da to ide unutar gore dodatog **if** bloka.

Sad kad imamo sve podatke, možemo raditi i neke operacija nad njima. Za slučaj sabiranja:

```php
<?php

if ($operacija == '+') {
	$rezultat = $prvaPromenljiva + $drugaPromenljiva;
}

?>
```
Znači, da bude jasnije, proveravamo da li je operacija +, odnosno sabiranje, i ako je taj uslov ispunjen, sabiramo promenljive. Koristeći isti šablon, napravićemo i ostale tri operacije:

```php
<?php

if ($operacija == '+') {
	$rezultat = $prvaPromenljiva + $drugaPromenljiva;
} elseif ($operacija == '-') {
	$rezultat = $prvaPromenljiva - $drugaPromenljiva;
} elseif ($operacija == '*') {
	$rezultat = $prvaPromenljiva * $drugaPromenljiva;
} elseif ($operacija == '/') {
	$rezultat = $prvaPromenljiva / $drugaPromenljiva;
}   

?>
```
Ali nešto tu još nedostaje. Postoji jedna posebna situacija, a to je da ne smemo deliti sa nulom. Dodaćemo još jedan uslov tamo, kao i poruku sa greškom.

```php
<?php

$rezultat = "";

if ($operacija == '+') {
	$rezultat = $prvaPromenljiva + $drugaPromenljiva;
} elseif ($operacija == '-') {
	$rezultat = $prvaPromenljiva - $drugaPromenljiva;
} elseif ($operacija == '*') {
	$rezultat = $prvaPromenljiva * $drugaPromenljiva;
} elseif ($operacija == '/') {
	if ($drugaPromenljiva != 0) {
		$rezultat = $prvaPromenljiva / $drugaPromenljiva;
	} else {
		echo 'Došlo je do Greške. Ne možemo deliti sa nulom.';
	}
}

echo $rezultat;

?>
```
Sa tim smo napravili naš jednostavan digitron. U budućim vežbama ćemo naučiti neke funkcije koje će nam pomoći da napravimo kod koji je modularniji(lakše se proširuje) i bolji za održavanje.

Što se vežbe tiče, pozivam Vas da razmislite o tome kako bi rešili sledeće:
* Kako bi izgledao kod za kvadraturu, odnosno dizanje vrednosti na kvadrat?
* Probajte izmeniti kod tako da se tekst "Rezultat" ne prikazuje uopšte, ukoliko nisu poslati podaci.
* Probajte dodati treću promenljivu u formu i neka ona učestvuje u svim operacijama.
* Probajte ispraviti kod, tako da u slučaju kada pošaljemo nulu kao drugu promenljivu, ne ispiše $rezultat.

Razmislite, zašto bi bio problem dodati još 5 promenljivih? Kod bi se stalno morao proširivati i postojao bi sve nezgrapniji i nečitkiji. Jedan od načina sa kojim bi to mogli rešiti jeste stavljanje dela koda u petlju.

## Petlje

[Preseljeno u poseban fajl](poglavlja/petlje.md)

## Datum i vreme uz date() funkciju

[Preseljeno u poseban fajl](poglavlja/datum-i-vreme-uz-date-funkciju.md)

## Napredniji rad sa nizovima

### Asocijativni nizovi

### Foreach petlja

### Višedimenzionalni nizovi

## Funkcije

### Neke ugrađene PHP funkcije

### Naše funkcije

### Argumenti vs Parametri

### Povratne vrednosti

### Rekurzija (napredno)