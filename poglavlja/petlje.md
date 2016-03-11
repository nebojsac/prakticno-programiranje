# Petlje

Kad počnete raditi na nekom projektu ubrzo ćete doći do situacije ili logike koja se ponavlja više puta uz manje izmene. Drugim rečima, to su šablonske situacije. Kada bi za gornji digitron hteli dodati još jednu promenljivu, to ne bi bilo jako teško, iako bi se dotakli većeg dela k**o**da. Da vam je to posao, prvi put bi ste verovatno tako i uradili, uz malo copy/paste akcije. Prekosutra bi vam se javio klijent da želi još 3 promenljive, i ovaj put već niste sigurni da li želite da radite sve ručno. Za nedelju dana bi se klijent možda javio da želi da digitron radi sa _proizvoljnim_ brojem promenljivih. Tada ste već primorani da pravite "pametniji" k**o**d, i da koristiti petlje.

Počećemo sa nekim osnovnim primerima koje ćemo proširivati sve dok ne budemo mogli rešiti problem kalkulatora i proizvoljnog broja promenljivih.

```php
<?php
for ($i = 0; $i < 10; $i++) {
	echo $i;
}
?>
```

Ovaj primer će ispisati brojeve od 0 do 9 na ekranu. Da malo pojasnimo strukturu ovog k**o**da:
* ```$i = 0``` stvaramo novu promenljivu $i, i kažemo da joj je početna vrednost 0. Nju koristimo kao brojač.
* ```$i < 10``` je uslov za ovu petlju. Dok god je ovaj uslov ispunjen, mi ćemo raditi ono što je unutar petlje(u ovom slučaju ispis).
* ```$i++``` predstavlja šta će se desiti svaki put kad se napravi "krug" u petlji. U ovom slučaju povećavamo brojač $i za 1 svaki put.

Znači, neki šablon za for petlje bi bio:

```php
<?php
for (brojač; uslov; radnjaPosleSvakogKruga) {
	// kod koji se izvršava svaki put
}
?>
```

Malo ćemo korigovati petlju da ispisuje brojeve u zasebne redove radi preglednost. Dodaćemo html element za novi red na kraj svakog ispisa:

```php
<?php
for ($i = 0; $i < 10; $i++) {
	echo $i;
	echo '<br />';
}
?>
```

Podsetite se gore šta koji deo ```for``` petlje znači i probajte sami odraditi sledeće zadatke:
* Napravite da ispis brojeva krene od 1.
* Napravite da ispis brojeva ide do 10.
* Napravite da ispis brojeva ide **od** 10 do 0. Savet: isto kao što postoji ```$i++```, postoji i ```$i--```.

## Matematika u petljama

Jedan od prvih matematičkih zadataka za vežbanje programiranje jeste ispisivanje Fibonačijevih brojeva. Fibonačijev niz brojeva počinje sa 0 i 1, a svaki sledeći broj predstavlja zbir prethodna dva. Dakle početak je 0,1,1,2,3,5,8,itd. Ograničimo se na prvih 50 brojeva. On se može rešiti na više načina, a jedan od tih načina uključuje petlje. Ako mislite da ga možete sami rešiti, predlažem vam da probate pre nego što nastavite tu. Ja ću vas u ovoj sekciji provesti korak po korak kroz rešavanje tog zadatka.

Za početak, nastavićemo gde smo stali, i produžiti petlju do 50:
```php
<?php
for ($i = 0; $i < 50; $i++) {
	echo $i;
	echo '<br />';
}
?>
```
E sad, ovo nije tačno ono što nama treba. Uz brojač ```$i``` ćemo pratiti koliko krugova smo napravili u petlji, ali ispis vrednosti tog brojača nam ne treba. Ispis trebamo početi sa 0 i 1, i svaki sledeći broj treba biti zbir prethodna dva. E sad, samo uraditi ```echo '0,2';``` nam neće puno pomoći. Moram biti u mogućnosti da sabiramo te brojeve, i zbog toga ćemo ih staviti u promenljive pre nego što ih ispišemo.
```php
<?php
$prethodniBroj = 0;
$trenutniBroj = 1;

echo $prethodniBroj . '<br />';
echo $trenutniBroj . '<br />';
for ($i = 0; $i < 50; $i++) {

}
?>
```
Petlju smo ispraznili jer nam nije koristio taj k**o**d. Sad želimo započeti ispisivanje Fibonačijevog niza. Dakle, rekli smo da je on zbir prethodna dva broja, iliti trenutnog i prethodnog broja. Napravićemo novu promenljivu $rezultat, čisto da bi mogli lakše pratiti šta se dešava. 
```php
<?php
$prethodniBroj = 0;
$trenutniBroj = 1;

echo $prethodniBroj . '<br />';
echo $trenutniBroj . '<br />';
for ($i = 0; $i < 50; $i++) {
	$rezultat = $prethodniBroj + $trenutniBroj;
	echo $rezultat . '<br />';
}
?>
```
Da li vidite problem u ovom k**o**du i bez pokretanja? Da, uvek će sabirati 0 i 1. Dakle, moramo malo džonglirati vrednosti. Zamislite da pravimo mentalnu belešku koji je "trenutni" a koji "prethodni" broj - počeli smo sa 0 i 1(možete sami na papiru pratiti logiku, možda pomogne). Saberemo ih, i dobijemo niz 0,1,1. Sada, mentalno moramo da se "pomerimo". Dakle, sada gledamo desnu jedinicu kao "trenutni" a levu jedinicu kao "prethodni" broj. Njih sabiramo, i dobijamo niz 0,1,1,2. Ponavljamo mentalno pomeranje pa 2 postaje novi "trenutni" broj, i tako dalje. 

To što smo radili sa "mentalnim beleškama" u prethodnom paragrafu, sada trebamo uraditi u k**o**du:
```php
<?php
$prethodniBroj = 0;
$trenutniBroj = 1;

echo $prethodniBroj . '<br />';
echo $trenutniBroj . '<br />';
for ($i = 0; $i < 50; $i++) {
	$rezultat = $prethodniBroj + $trenutniBroj;
	echo $rezultat . '<br />';

	$prethodniBroj = $trenutniBroj;
	$trenutniBroj = $rezultat;
}
?>
```
Da li vam je jasno šta se tu desilo? Ako nije, probajte da vokalizujete k**o**d, red po red, ponavljajući u petlji. Logika ide ovako:
* Prethodni broj je 0, a trenutni 1. Ispišemo njih pre petlje ```0,1```
* Brojac počinje od nule. Petlju ponavljamo dok brojač ne dođe do 50, i svakog kruga povećavamo brojač.
* Počinjemo prvi krug, brojač $i je 0.
* Rezultat je zbir ta dva broja, ispisujemo ga ```0,1,1```
* Vrednost trenutnog broja(1) smeštamo u promenljivu $prethodniBroj.
* Vrednost rezultata(1) smeštamo u promenljivu $trenutniBroj.
* Počinjemo drugi krug, brojač $i je 1.
* Rezultat je zbir ta dva broja, ispisujemo ga, na ekranu u ovom momentu stoji ```0,1,1,2```
* Vrednost trenutnog broja(1) smeštamo u promenljivu $prethodniBroj.
* Vrednost rezultata(2) smeštamo u promenljivu $trenutniBroj.
* Počinjemo treći krug, brojač $i je 2.
* Rezultat je zbir ta dva broja, ispisujemo ga, na ekranu u ovom momentu stoji ```0,1,1,2,3```
* Vrednost trenutnog broja(2) smeštamo u promenljivu $prethodniBroj.
* Vrednost rezultata(3) smeštamo u promenljivu $trenutniBroj.
* I tako sve dok je brojač manji od 50, kao što je navedeno u uslovu.

Pokušajte sledeće zadatke rešiti sami:
* Rekli smo da želimo ispisati 50 brojeva u Fibonačijevom nizu. Trenutno to nije slučaj. Koliko se trenutno brojeva ispiše, i kako ti ispraviti?
* Kako bi ste ograničili petlju tako da se zaustavi nakon što se ispiše broj veći od 100?

## While petlja

```for``` petlja je dobra kada imati predvidivi broj elemenata u nizu, ili ako njihov broj možete i izračunati. Ali nekad vam je brojač suvišan i želite da se petlja ponavlja dok se ne ispuni neki drugačiji uslov. Za takve situacije možete koristiti ```do-while``` petlju, koja bi u prevodu značila "ponavljaj dok", odnosno "ponavljaj dok je uslov ispunjen". Krenimo sa primerom:

```php
<?php
$broj = 0;

do {
	$broj = $broj + 2;
} while (($broj % 7) == 0);

echo 'Promenljiva $broj je sada ' . $broj;
?>
```

Na početku kažemo da ```$broj``` ima vrednost ```0```, i ulazimo u ```do-while``` petlju. Obratite pažnju, prvo smo ušli u prvi krug petlje, posle se dešava provera.

```%``` je moduo, to je matematička operacija koja vraća ostatak deljenja, i koristi se za proveru da li je neki broj deljiv sa nekim drugim. A deljiv je ako je ostatak deljenja 0 (a da pritom i sam broj nije 0). Na primer, 20 % 3 daje 2, a 20 % 10 daje 0. U ovom primeru radimo ```($broj % 7) == 0``` što znači da proveravamo da li je ```$broj``` deljiv sa 7.

Unutar petlje u toku svakog kruga, u ```$broj``` stavljamo vrednost ```$broj + 2```, što efektivno znači da uvećavamo ```$broj``` za 2. 

Pomoći ću vam da vizualizujete šta se tu dešava, dodaćemo još ispisa:

```php
<?php
$broj = 0;

do {
	$broj = $broj + 2;
	echo '$broj je ' . $broj . '<br />';
} while (($broj % 7) == 0);

echo 'Promenljiva $broj je sada ' . $broj;
?>
```

Kad god vam nije skroz jasno šta se dešava ubacite ```echo``` da vidite šta je u kojoj promenljivoj u kojem momentu. ```<br />``` je html k**o**d za novi red, pa to pomaže da ispis bude pregledniji.

U delu za uslov kod ```while``` mogu da idu i veći uslovi sa ```AND``` i ```OR```, koje smo spominjali gore. Recimo da ne želimo da se petlja završi na broju 14. Proširićemo uslov:

```php
<?php
$broj = 0;

do {
	$broj = $broj + 2;
	echo '$broj je ' . $broj . '<br />';
} while (($broj % 7) == 0 AND ($broj > 50));

echo 'Promenljiva $broj je sada ' . $broj;
?>
```

Sada će petlja ići sve dok je ```$broj``` manji od 50, i dok nije deljiv sa 7. Naravno, morate paziti šta radite, jer ako zadate nemoguć uslov, npr da $broj bude manji od 0 iako se samo povećava, možete dobiti beskonačnu petlju. Tada će se Apache privremeno zapucati i nećete moći ništa raditi dok on ne odluči da prekine proces. Mada je moja preporuka tada da sami ručno zaustavite i ponovo pokrenete Apache u Xamp Control panelu.

Vredi spomenuti da ```do-while``` ima i druge formate, u kojima se uslov proverava na početku:
```php
<?php
$broj = 0;

while (($broj % 7) == 0 AND ($broj > 50)) {
	$broj = $broj + 2;
	echo '$broj je ' . $broj . '<br />';
}

echo 'Promenljiva $broj je sada ' . $broj;
?>
```

Par zadataka za vas:
* Promenite jedan od ovih primera tako ne izađe iz petlje dok ```$broj``` ne bude paran, i veći od 98. 
* Probajte napraviti ```for``` petlju koja radi istu stvar, tj koja počinje od nule i povećava ```$broj``` dok ne bude paran i veći od 98.
