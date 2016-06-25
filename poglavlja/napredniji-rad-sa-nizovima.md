# Napredniji rad sa nizovima

Pošto ovo poglavlja pretpostavlja određena predznanja o nizovima, poželjno bi bilo da se podsetite kako rade nizovi uz pomoć ranijeg poglavlja [Osnove Nizova](osnove-nizova.md).

Nizovi su jako korisni za organizovanje podataka, i u PHP-u su veoma fleksibilni i dolaze uz pregršt već postojećih funkcija koje vam olakšavaju rad sa njima. Počećemo od jednostavnijeg primera opet, u ovom slučaju dani u nedelji:

```php
<?php

$weekDays = [
	'Ponedeljak',
	'Utorak',
	'Sreda',
	'Četvrtak',
	'Petak',
	'Subota',
	'Nedelja'
];

print_r($weekDays);

echo 'Prvi dan je ' . $weekDays[0];
?>
```

Za početak smo napravili niz dana u nedelji. Započeli smo brojanje od nule jer, podsetite se, u programiranju redno brojanje počinje od nule. Ovaj k**o**d zasad ispisuje sve dane u nedelji koje smo ručno uneli, i još na kraju ispiše naziv prvog dana u nizu. Trenutno su svi elementi ovog niza stringovi, odnosno tekst.

Da napravimo problematiku zanimljivijom, u nastavku ćemo iskoristiti ovaj niz za pravljenje rasporeda, a to ćemo uraditi tako što ćemo na mesto svakog tekstualnog dana u nedelji, staviti po niz.

```php
<?php

$tasks = [
	'Ponedeljak' => ['izneti smeće'],
	'Utorak' => ['zvati babu'],
	'Sreda' => ['teretana, noge'],
	'Četvrtak' => ['oprati kola', 'pokositi travu'],
	'Petak' => ['teretana, ruke'],
	'Subota' => ['shopping'],
	'Nedelja' => []
];

print_r($tasks);

echo 'Prvog dana treba ' . $tasks['Ponedeljak'][0];
?>
```

Da se podsetimo, ```echo``` je koristan ako želimo ispisati neki tekst, ili vrednost neke promenljive, ali nije dovoljan za nizove. ```echo $tasks``` bi samo ispisalo ```Array```, što nam i nije mnogo korisno. Zato koristimo ```print_r()```. Ali elementi niza su isti kao "obične" promenljive, pa ako koristimo indeks niza, onda možemo koristiti ```echo```. Primetite da je ovo niy koji sadrži u sebi sedam pod-nizova. Glavni niz je indeksiran tekstualno ```'Ponedeljak', 'Utorak'...``` dok su pojedinačni podnizovi samo popunjeni, što im automatski daje brojčane indekse, počevši od nule.

Takođe, obratite pažnju kako su različite vrednosti podnizova. ```'Ponedeljak'``` ima jedan element, ```'Četvrtak'``` ima dva a ```'Nedelja'``` nema ni jedan, odnosno sadrži prazan niz ```[]```. Primera radi, možemo ih tako pojedinačno ispisati:

```php
<?php

$tasks = [
	'Ponedeljak' => ['izneti smeće'],
	'Utorak' => ['zvati babu'],
	'Sreda' => ['teretana, noge'],
	'Četvrtak' => ['oprati kola', 'pokositi travu'],
	'Petak' => ['teretana, ruke'],
	'Subota' => ['shopping'],
	'Nedelja' => []
];

echo 'Ponedeljak:';
print_r($tasks['Ponedeljak']);

echo 'Četvrtak:';
print_r($tasks['Četvrtak']);

echo 'Nedelja:';
print_r($tasks['Nedelja']);

?>
```

U slučaju podniza 'nedeljA' je možda korisniije koristiti ```var_dump()```, ali to ostavljam vama da isprobate na tom i ostalim podnizovima.

## Nizovi i for() petlja

Neizbežna kombinacija u vašem kodu će biti nizovi i petlje. Iz tog razloga Vam preporučujemm da dobro savladate ovu sekciju. Iako u startu deluje malo teže, kad vam jednom 'klikne', viedećete da i nije tako strašno.

Za početak, uzećemo niz od gore, i ispisaćemo ga celog, element po element:


```php
<?php

$weekDays = [
	'Ponedeljak',
	'Utorak',
	'Sreda',
	'Četvrtak',
	'Petak',
	'Subota',
	'Nedelja'
];

print_r($weekDays[0]);
print_r($weekDays[1]);
print_r($weekDays[2]);
print_r($weekDays[3]);
print_r($weekDays[4]);
print_r($weekDays[5]);
print_r($weekDays[6]);

?>
```

Jasno je da je ovaj način ispisivanja pojedinačnih elemenata nizova nepraktičan. Zamislite sad da imate niz koji nije fiksne veličine, poput nekog niza ```$daysOfTheMonth``` koji sadrži sve dane, brojčano u određenom mesecu. To će nekad biti 30, nekad 31, a nekad i 28 ili 29 elemenata. Sa ovim problemom ćete se susresti kad budete pravili forme na kojima korisnik može da bira datum rođenja, na primer.

Da bismo napravili dinamično rešenje za ovakav ispis, koristićemo ```for``` petlju.

```php
<?php

$weekDays = [
	'Ponedeljak',
	'Utorak',
	'Sreda',
	'Četvrtak',
	'Petak',
	'Subota',
	'Nedelja'
];

$sizeOfArray = 7;

for ($i = 0; $i < $sizeOfArray; $i++) {
	print_r($weekDays[$i]);
}
?>
```

Da pojasnimo šta se tu dešava:
 * Ulazimo u petlju i podešavamo brojač ```$i``` na nulu.
 * Uslov za trajanje petlje će biti da ```$i``` bude manje od 7, odnosno ```$i < $sizeOfArray```, što znači da će u poslednjem krugu biti 6, dok još ispunjava uslov.
 * Nakon svakog 'kruga' u petlji ćemo povećati ```$i``` za jedan, uz ```$i++```.

Za slučaj da Vam nije jasno kako ova petlja radi, "raspakovaću" dešavanja u kod koji radi istu stvar, ali bez petlje. Imajte na umu, ovo nije kod koji biste videli u praksi, ali Vam možda pomogne da shvatite šta se dešava:

```php
<?php

$weekDays = [
	'Ponedeljak',
	'Utorak',
	'Sreda',
	'Četvrtak',
	'Petak',
	'Subota',
	'Nedelja'
];

// početak petlje:
$i = 0;

// prvi krug:
print_r($weekDays[$i]);
$i = $i + 1; // $i++

// drugi krug:
print_r($weekDays[$i]); // $i je u ovom trenutku 1
$i = $i + 1; // $i++

// treći krug:
print_r($weekDays[$i]); // $i je u ovom trenutku 2
$i = $i + 1; // $i++

// četvrti krug:
print_r($weekDays[$i]); // $i je u ovom trenutku 3
$i = $i + 1; // $i++

// peti krug:
print_r($weekDays[$i]); // $i je u ovom trenutku 4
$i = $i + 1; // $i++

// šesti krug:
print_r($weekDays[$i]); // $i je u ovom trenutku 5
$i = $i + 1; // $i++

// sedmi krug:
print_r($weekDays[$i]); // $i je u ovom trenutku 6
$i = $i + 1; // $i++
// $i je sada 7

// Na kraju sedmog kruga, uslov ($i < 7) više nije ispunjen, pa se petlja prekida.
?>
```

Bitne informacije iz ovoga:
 * Petlja se izvršava dok god je uslov ispunjen.
 * Na _kraju_ svakog kruga u petlji se povećava brojač ```$i```

Da se vratimo sada malo na korišćenje same petlje. U Ranijem primeru u ```for ($i = 0; $i < $sizeOfArray; $i++) {``` 
koristimo promenljivu ```$sizeOfArray``` da bismo ograničili pelju. Pre same petlje u promenljivu ```$sizeOfArray``` 
stavljamo broj 7, koji u kombinaciji sa uslovom ```$i < $sizeOfArray``` dovodi do toga da se petlja ponovi ukupno sedam 
puta. U praksi će biti nepraktično ručno davati takve vrednosti, jer neće raditi sa nizovima različitih velicina.
Ako bismo obrisali jedan dan iz niza došlo bi do greške, zbbog nepostojećeg sedmog elementa. A ako bismo dodali osmi 
element, on ne bi bio ispisan bez da promenimo vrednost ```$sizeOfArray``` promenljive(oba primera možete i sami 
isprobati).

Za potrebe ovog problema, upoznaćemo se sa još jednom ugrađenom PHP funkcijom: ```count()```. U opisu funkcije na php.net sajtu stoji da ona prima niz kao ulazni parametar, a vraća broj elemenata tog niza. Dakle, ako bismo u našem primeru sa danima u nedelji to iskoristili, dobićemo broj 7:

```php
<?php

$weekDays = [
	'Ponedeljak',
	'Utorak',
	'Sreda',
	'Četvrtak',
	'Petak',
	'Subota',
	'Nedelja'
];

$sizeOfArray = count($weekDays);

for ($i = 0; $i < $sizeOfArray; $i++) {
	print_r($weekDays[$i]);
}
?>
```

Sa tim dobijamo dinamičniji kod, i sada kad menjamo niz ```$weekDays``` ne moramo više posebno menjati 
```$sizeOfArray```.

Sem što možemo ispisivati sadržaj nizova uz pomoć petlje, možemo i dodavati ili oduzimati elemente. Za sledeći primer 
koristićemo neke od datumskih funkcija koje smo upoznali ranije:

```php
<?php

$lengthOfMonth = date('t');
$daysInMonth = [];

for ($i = 0; $i < $lengthOfMonth; $i++) {
	$daysInMonth[] = $i;
}

print_r($daysInMonth);

?>
```

Ovaj kod radi sledeće:
* Deklariši promenljivu ```$lengthOfMonth``` kao dužinu trenutnog meseca(28, 29, 30 ili 31).
* Deklariši ```$daysInMonth``` kao prazan niz.
* Neka petlja napravi broj krugova jednak broju ```$lengthOfMonth```.
* U svakom krugu neka se smesti tadašnja vrednost ```$i``` na kraj niza ```$daysInMonth```.

Za moguće paramatere ```date()``` funkcije se uvek možete konsultovati sa php.net dokumentacijom. Nemate razloga da ih 
učite napamet. Što se tiče samog niza, red ```$daysInMonth = []``` ga inicijalizuje kao prazan niz ```[]```. A u samoj
petlji imamo malo drugačiji redosled ```$daysInMonth[] = $i```, i u tom slučaju se vrednost promenljive ```$i```
dodaje na kraj niza.

Ovaj kod nije savršen, ali ostavljeno je vama da ga ispravite:

* Ne postoji nulti dan u mesecu. Ispravite kod da ispiše postojeće "dane" za trenutni mesec.
* Nakon što se ispiše sadržaj niza ispišite i broj elemenata u datom nizu: "Ovaj niz ima x elemenata."
* Podsetite se kako rade ```date()``` i ```strtotime()``` funkcije, pa uradite sličan ispis za prošli mesec, umesto
trenutnog.

## Nizovi i foreach() petlja

Foreach petlja predstavlja malo drugačiji pristup rada sa nizovima. Da krenemo sa jednostavnijim primerom. Za početak,
foreach petlja je korisnija za rad sa asocijativnim nizovima, odnosno nizovima koji nemaju brojeve za indekse.

```php
<?php

$weekDays = [
	'Ponedeljak',
	'Utorak',
	'Sreda',
	'Četvrtak',
	'Petak',
	'Subota',
	'Nedelja'
];

foreach ($weekDays as $day) {
	print_r($day);
}

?>
```

U svom najosnovnijem obliku, foreach petlja radi sa nekim nizom, i prolazi kroz njega, elemenat po elemenat, nezavisno
od indeksa. Kao što vidite, nemamo ni brojač ```$i```, ni ```count()```, ni uslov. Jednostavno, foreach napravi onoliko
krugova koliko ima u nizu ```$weekDays```. U svakom krugu uzme elemenat koji je trenutno na redu, i stavi ga u
promenljivu sa desne strane ```as``` reči, za potrebu trenutnog kruga. ```$day``` može da se zove i drugačije, ali
generalno pravilo koje možete koristiti jeste da format bude: ```foreach ($množina as $jednina)```, npr
```foreach ($numbers as $number)``` ili ```foreach ($cities as $city)``` itd.

Ali pošto je niz ```$weekDays``` i dalje indeksiran brojevima ```[0=>'Ponedeljak', 1=>'Utorak'...]``` nemamo neke
potrebe da koristimo ```foreach()```. Zato, nastavićemo sad na primer gde je ```foreach()``` korisniji.

```php
<?php

$translatedWeekDays = [
	'Monday' => 'Ponedeljak',
	'Tuesday' => 'Utorak',
	'Wednesday' => 'Sreda',
	'Thursday' => 'Četvrtak',
	'Friday' => 'Petak',
	'Saturday' => 'Subota',
	'Sunday' => 'Nedelja'
];

foreach ($translatedWeekDays as $key => $value) {
	echo $key . ' - ' . $value . '<br />';	
}

?>
```

Kada radimo sa asocijativnim nizovima, odnosno nizovima koji su indeksirani tekstom ili drugim vrednostima, tada 
```foreach``` dolazi do izražaja. Za svaki krug ```foreach``` petlje se spremaju dve vrednosti:
* U ```$key``` promenljivu se smešta vrednost indeksa datog elementa.
* U ```$value``` promenljivu se smešta vrednost elementa.
U gornjem ovom primeru, engleski nazivi za dane se smatraju indeksima(```key``` na engleskom), a srpski nazivi
predstavljaju vrednost na tim indeksima. Kao i inače, ```foreach``` petlja će se vrteti dok ne prođe sve elemente.

Radi vežbe i podsećanja na prethodne sekcije:
* Promenite ispis da bude ```'Monday' je na srpskom "Ponedeljak".```. Obratite pažnju da ipisani dani budu unutar
navodnika.
* Dodajte na na svaki krug petlje da se ispiše ```Engleska verzija ima više slova.``` ili 
```Srpska verzija ima više slova.```, zavisno od toga da li je reč duža na srpskom ili na engleskom. (savet: koristite 
```strlen()``` funkciju).
* [Teži zadatak] Uzmite niz ```$tasks``` iz ranijeg primera, i napišite kod koji će ispisati sledeće:

```
Ponedeljak: izneti smeće.
Utorak: zvati babu.
Sreda: teretana, noge.
Četvrtak: oprati kola, pokositi travu.
Petak: teretana, ruke,
Subota: shopping.
Nedelja: slobodan dan.
```
Savet: Petlja može da se koristi unutar druge petlje.