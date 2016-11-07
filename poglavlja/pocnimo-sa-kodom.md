# Počnimo sa kodom!

## Echo

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

```echo``` služi za ispis na ekran(u ovom slučaju). Posle njega možete napisati neki tekst, i staviti pod navodnike. Probajte i sami sa nečim drugim. Radi i sa jednostrukim i sa dvostrukim navodnicima. 

Na kraj svakog reda koda u PHP-u treba da se nalazi tačka-zarez ```;``` u suprotnom ćete dobiti grešku. (Tačnije bi bilo reći na kraju svake komande, ali nećemo komplikovati sad)

```?>``` označava kraj PHP koda. Generalno je neobavezan u fajlovima koji sadrže isključivo php kod.

Ajmo sledeći korak. Vreme da se upoznamo sa promenljivama. Prekucajte sledeći kod u vaš index.php fajl, sačuvajte ga, i osvežite stranicu u browseru.
```php
<?php
$name = 'Nebojša';
echo 'Zdravo' . $name;
?>
```
U browseru bi trebalo da vidite tekst "ZdravoNebojša".
```$name``` je promenljiva, što se u PHPu prepozna tako što ima dolar znak ```$``` ispred. Umesto ```name``` tu može biti skoro bilo šta(ograničenja možete naći na netu), ali za početak ćemo se držati teksta, bez razmaka. Vežbe radi, ubacite tu svoje ime i osvežite stranicu.

**Tačka(.)** se u ovom slučaju koristi za spajanje dva teksta, radi lakšeg ispisa. Ne mora biti razmak između tačke i susednih karaktera, ali ja stavljam radi preglednosti koda.

U programiranju, za tekst se obično kaže da je on ```string```, čisto da budete upoznati sa tim pojmom. ```string``` je ustvari niz pojedinačnih karaktera i predstavlja **tip** promenljive tj. podatka.

**Promenljive** će vam biti glavni pojam za podatke u vašem kodu. U promenljive se pohranjuju podaci raznih tipova i veličina i koriste se za baratanje sa i poređenje tih podataka. Zamislite to kao kutiju u koju možete staviti bilo šta. Na stranu kutije napišete šta drži, na primer ```$knjiga```, i možete u nju staviti "Harry Potter", ili zameniti sa "Twilight"(_nemojte_). Promenljive se koriste za privremeno držanje podataka da bi se sa njima kasnije mogle raditi zanimljivije stvari(ispis, proračuni, odlučivanje, itd.)

Prva lagana vežba u ovom tekstu će biti da uradite sledeće:
* Popravite kod za ispis imena, da ima razmak između "Zdravo" i ispisanog imena. Zapamtite, ```echo``` ispisuje ono što je unutar navodnika i promenljive.
* Proširite rečenicu. Neka ispiše nešto kao "Zdravo Nebojša, divan dan, zar ne?". Možete proširiti postojeći red koda, ili dodati novi ispod.

## Uslovi (IF/ELSE)
Ne bismo daleko stigli sa samim ispisom promenljiva. Da bi naši programi radili naprednije stvari i donosili odluke na osnovu podataka, moramo imati uslove. Uslove možete vokalizovati na sledeći način **"Ako je ovaj uslov ispunjen, uradi sledeće. Ako nije, uradi nešto drugo."**. No, ajde da se bacimo na primer. Možete pisati u isti fajl za sada, kada budemo imali više materijala, rasporedićemo na više fajlova.

```php
<?php
$name = 'Nebojša';
$age = 27;

if ($age < 18) {
	echo $name . ', pa ti nemaš ni 18 godina!';
} else {
	echo $name . ', pa ti si već odrasla osoba.';
}
?>
```

Oke, imamo tu sad više novih pojmova. Za početak, imamo novu promenljivu ```$age``` i u nju stavljamo celi broj(tj. integer, govoreći programerski). U daljem kodu taj broj koristimo u našem uslovu i poredimo ga sa brojem 18. Kad bi vokalizovali ovaj kod, glasio bi "Ako je $age manji od 18, ispiši prvu rečenicu, u suprotnom ispiši drugu".

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
* Promenite ```$age``` tako da ispiše drugu rečenicu kad osvežite stranicu.
* Zamenite dva ispisana teksta u kodu, da prvi bude za **"odraslu osobu"**. Izmenite uslov da ispisuje tačnu rečenicu na osnovu broja godina.

## Napredniji Uslovi

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

Novost ovaj put je ```elseif``` uslov. Logika ovde je takva da se prvo proveri uslov "manje ili jednako sa 8", pa ako taj uslov nije ispunjen, ide na sledeći, "manje ili jednako sa 12", i tek ako ni taj nije ispunjen, stiže na poslednji uslov "veće od 12". Ako ni poslednji uslov nije ispunjen, izlazimo iz ovog grananja, ništa od komandi unutar ovih uslova neće biti pokrenuto. Da smo stavili još na kraj običan ```else``` bez ikakvih dodatnih poređenje, onda bi komande unutar tog ```else``` bloka bile pokrenute samo ako ni jedan prethodni uslov nije ispunjen.

Vežbe vezane za ovo:
* Menjajte promenljivu ```$razred```, tako da vidite sve moguće rečenice.
* Zašto smo morali koristiti "manje ili jednako" simbol ```<=``` umesto običnog "manje" simbola? 
* Ako bismo promenili prvi i drugi uslov tako da koriste simbol za manje ```<```, koje vrednosti bi mogli staviti u ```$razred``` da na kraju ```$skola``` ostane prazan string ```''```? Pomoć: dakle, ako su uslovi ```($razred < 8)```, ```($razred < 12)``` i ```($razred > 12)```, koja vrednost za ```$razred``` nije pokrivena?

### Ukratko o boolean vrednostima

Boolean je binarni tip promenljive, što znači da obuhvata samo dve moguće vrednosti. Najtačnije je predstaviti ih sa ```true``` i ```false```, ali ekvivalenti su i ```1``` i ```0```. Možete o njima misliti kao o tačnosti, "istinito" i "neistinito", "tačno" i "netačno", "da" i "ne". 

Iako možda trenutno ne znate šta su boolean vrednosti, vi ste već baratali sa njima. Kao što matematičke operacije daju određene brojčane vrednosti, tako operacije poređenja ```<,>,==,<=,>=,!=``` daju boolean vrednosti. 

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
## Logičke operacije

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
if (false OR (true AND false)) {
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

### Više o Boolean(istinitost)

Boolean vrednosti su super kada trebate pratiti binarna stanja. Primeri bi bili $otvoreno, $aktivan, $obrisano, $blokiran. Bilo šta što može imati vrednosti "da" i "ne", odnosno **true** i **false**.

E sad, vredi skrenuti pažnju na to da svaka vrednost ima svoju ekvivalentnu Boolean vrednost. Na primer, 0 je jednaka **false** dok je bilo koji broj veći od nule jednak **true**. Prazan niz ili string su **false**, a ako nisu prazni onda su **true**. Ne znači vam to puno ovako nasuvo, ali trudiću se da ubacujem ovo u buduće primere, da vidite šta se dešava.

### Malo o strogoj jednakosti

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