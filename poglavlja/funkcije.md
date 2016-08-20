# Funkcije

Jedan od prvih koraka u pravljenju efikasnijeg koda, sa što manje dupliciranih redova, jeste korišćenje funkcija.

Funkcije su male celine koda koje možete "pozivati" drugde u vašem programu. PHP ima ugrađene funkcije koje možete koristiti(poput ```date()```), ali možete i sami praviti svoje.

Generalno govoreći, one uzimaju neke ulazne parametre(tzv. argumente) i vraćaju neke podatke, povratne vrednosti(eng. "return values"). Ako se desi da istih par redova koda kopirate po vašem projektu, znači da je vreme da se taj kod umota u funkciju.

Jednostavniji primer, želimo sav tekst, kojeg ispisujemo u toku rada programa, da se oiviči određenim simbolima, i stavlja u sopstvene redove:

```php
<?php

	echo '<br /> ===> ' . 'Početak programa'  . ',';

	for ($i = 0; $i <= 10; $i++) {
		echo '<br /> ===> ' . $i . ',';
	}

	echo '<br /> ===> ' . 'KRAJ'  . ',';
?>
```

Ne znam za vas, ali meni je bilo dovoljno naporno to napisati jednom, a ne svaki put kada se treba ispisati. Iako je primer banalan ovaj put, u pravim projektima ćete imati slične potrebe koje uključuju HTML kod, o kojem ćemo možda kasnije više pisati.

Sad ćemo napraviti našu funkciju koja će gorenavedeno raditi za nas.

```php
<?php

	echo '<br /> ===> ' . 'Početak programa'  . ',';

	for ($i = 0; $i <= 10; $i++) {
		echo '<br /> ===> ' . $i . ',';
	}

	echo '<br /> ===> ' . 'KRAJ'  . ',';

	function ispis($text) {
		echo '<br /> ===> ' . $text  . ',';
	}
?>
```

Nekoliko detalja pre nego što nastavimo:
* Definisanje funkcije se radi sa ključnom reči ```function```. Pre nje mogu biti i druge ključne reči, ali o tome više kasnije.
* Posle ```function``` napišemo naziv funkcije, u ovom slučaju ```ispis```.
* Sama definicija funkcije može stojati bilo gde u fajlu, mada u praksi obično su funkcije grupisane u određenim fajlovima.
* Samim definisanjem funkcije (kada ispred imate ```function```) se ona ne pokreće, dakle, ne radi ništa još u našem primeru.
* Unutar zagrada idu argumenti koje ta funkcija prima ```($text)```. Na to možete gledati poput ulaznih signala, odnosno informacija sa kojima funkcija radi.

Da ne dužim dalje sa suvim informacijama, da pokažem kako se koristi nova funkcija:

```php
<?php

	ispis('Početak programa');

	for ($i = 0; $i <= 10; $i++) {
		echo ispis($i);
	}

	echo ispis('KRAJ');

	function ispis($text) {
		echo '<br /> ===> ' . $text  . ',';
	}
?>
```
Dakle, sa ```function ispis($text)``` delom smo **definisali** funkciju. To znači da smo napravili takozvani nacrt koji nam govori šta ona radi. Taj blok k**o**da sa ```function``` sam po sebi neće raditi ništa. Zato funkciju moramo pozvati, kao što smo pre pozivali ```echo``` i ```date()```.

Pozivanje funkcije se radi **bez** ```function```. Ali pošto definicija naše funkcije kaže da imamo jedan ulazni parametar ```$text```, pri svakom pozivanju naše ```ispis()``` funkcije moramo i proslediti neke podatke.

U primeru se vidi da našoj funkciji možemo proslediti promenljivu ```$i``` na primer, a možemo i direktno neki tekst ubaciti, kao što radimo sa ```'KRAJ'```.


Funkcija koju bih vam preporučio i za budući lakši rad je sledeća:
```php
<?php

	pr('Početak programa');

	for ($i = 0; $i <= 10; $i++) {
		echo pr($i);
	}

	echo pr('KRAJ');

	function pr($podaci) {
		echo '<pre>';
		print_r($podaci);
		echo '</pre>';
	}
?>
```
* Ova funkcija služi za preglednije ispisivanje podataka na ekran. Naročito je korisna kad se koristi za ispis nizova.
* Nazvali smo je kratko ```pr()``` jer ćemo je često koristiti. Inspirisana je istoimenom funkcijom iz CakePHP-a, i kasnije ćemo je proširiti dodatno.

## Funkcija za digitron

Možemo čak i da se pozabavimo i sa funkcijom za digitron. Jedno od ranijih poglavlja je podrazumevalo pisanje digitrona.
Iako je poenta tog poglavlja bilo savladavanje POST i GET metoda slanja podataka, sama logika digitrona može da posluži
kao dobar primer primene funkcija.

Da se podsetimo kako radi digitron iz ranijeg poglavlja: Šalju se dva broja, i odabrana operacija, i na osnovu poslatih parametara
se dobija određeni rezultat na ekranu. Na primer, unesemo brojeve ```1``` i ```3``` u formu, i na formi izaberemo
```sabiranje```, nakon čega na ekranu dobijamo ```Rezultat je 4```. E sad, zamislite da želite više takvih operacija
odjednom da uradite sa sličnim kodom. Da vam kažem, "Uzmite ta dva broja koja dobijete, i dva puta odradite množenje,
tri puta sabiranje, i jednom deljenje, sa sve ispisima na ekranu.". Kada biste to radili bez funkcija, to bi značilo
mnogo dupliciranog koda. A sem toga, čim bi se potrebe zadatka promenile(npr, brojnost operacija), morali bi ste
drastično da menjate i kod.

Da bi pokazali kako nam funkcije mogu pomoći u toj situaciji, pretvorićemo par operacija u funkcije.

```php
<?php

$firstNumber = 1;
$secondNumber = 3;
$operation = 'add';

if ($operation == 'add') {

} elseif ($operation == 'subtract') {

} elseif ($operation == 'multiply') {

} elseif ($operation == 'divide') {

} else {

}

?>
```

Za početak smo samo postavili kostur zadatka. Pripremili smo promenljive koje ćemo koristiti, kao i osnovnu logiku za
razlikovanje operacija. Nastavićemo da proširujemo kod, bez korišćenja funkcija prvenstveno:

```php
<?php

$firstNumber = 1;
$secondNumber = 3;
$operation = 'add';

if ($operation == 'add') {
	$result = $firstNumber + $secondNumber;
} elseif ($operation == 'subtract') {
	$result = $firstNumber - $secondNumber;
} elseif ($operation == 'multiply') {
	$result = $firstNumber * $secondNumber;
} elseif ($operation == 'divide') {
	$result = $firstNumber / $secondNumber;
} else {
	$result = 'Pogresna operacija.';
}

echo 'Rezultat je: ' . $result;

?>
```

Sad zamislite da želite da dobijete rezultat na više različitih kombinacija brojeva. Nepraktično bi bilo koristiti neku
petlju, a neodrživo bi bilo kopirati isti kod više puta, pogotovo ako uzmemo u obzir da ćemo ga hteti proširivati.
Za početak, prebacićemo sav značajan kod u novu funkciju koju ćemo nazvati ```calculator()```.

```php
<?php

function calculator()
{
	$firstNumber = 1;
	$secondNumber = 3;
	$operation = 'add';

	if ($operation == 'add') {
		$result = $firstNumber + $secondNumber;
	} elseif ($operation == 'subtract') {
		$result = $firstNumber - $secondNumber;
	} elseif ($operation == 'multiply') {
		$result = $firstNumber * $secondNumber;
	} elseif ($operation == 'divide') {
		$result = $firstNumber / $secondNumber;
	} else {
		$result = 'Pogresna operacija.';
	}

	echo 'Rezultat je: ' . $result;
}

?>
```

Kad bi ovaj code pokrenuli ne bi ništa dobili na ekranu. Ovo se zove "definicija funkcije" i daje se prepoznati
po ključnoj reči ```function``` ispred imena funkcije. Ovaj kod se sam po sebi neće izvršiti bez izričitog pozivanja.
O njemu možete razmišljati kao o nekom planu izvršavanja, ili o šablonu koji možete lako više put iskoristiti. Ime je
proizvoljno dok god se ne sudara sa ključnim rečima iz PHP-a. Nakon imena stavljate zagrade ```()``` unutar kojih ćemo
nešto i stavljati kasnije. Sam sadržaj funkcije, odnosno kod koji se izvršava u okviru funkcije, se stavlja u litičaste
zagrade ```{}```. Da bi kod bio pregledniji, važi isto pravilo kao i kod drugih blokova koda, uvucite sadržaj između
para litičastih zagrada za širinu još jednog TAB-a(pritisnete TAB na tastaturi).

Što se tiče samog pozivanja, to izgleda ovako:

```php
<?php

calculator(); // pozivamo funkciju u ovom momentu

function calculator()
{
	$firstNumber = 1;
	$secondNumber = 3;
	$operation = 'add';

	if ($operation == 'add') {
		$result = $firstNumber + $secondNumber;
	} elseif ($operation == 'subtract') {
		$result = $firstNumber - $secondNumber;
	} elseif ($operation == 'multiply') {
		$result = $firstNumber * $secondNumber;
	} elseif ($operation == 'divide') {
		$result = $firstNumber / $secondNumber;
	} else {
		$result = 'Pogresna operacija.';
	}

	echo 'Rezultat je: ' . $result;
}

?>
```

Funkcija se poziva ipisivanjem njenog imena, uz zagrade, što u ovom slučaju znači ```calculator()```. Vredi napomenuti
da nije bitno gde se definiše funkcija u odnosu na pozivanje. I sad recimo možemo lako tri puta pozvati funkciju:


```php
<?php

calculator();
echo '<br />'; //stavili smo razmake radi preglednosti
calculator();
echo '<br />';
calculator();

function calculator()
{
	$firstNumber = 1;
	$secondNumber = 3;
	$operation = 'add';

	if ($operation == 'add') {
		$result = $firstNumber + $secondNumber;
	} elseif ($operation == 'subtract') {
		$result = $firstNumber - $secondNumber;
	} elseif ($operation == 'multiply') {
		$result = $firstNumber * $secondNumber;
	} elseif ($operation == 'divide') {
		$result = $firstNumber / $secondNumber;
	} else {
		$result = 'Pogresna operacija.';
	}

	echo 'Rezultat je: ' . $result;
}

?>
```

To ne deluje naročito korisno. Funkcija koja uvek radi istu stvar sa istim podacima može biti korisna, ali to sada nije
slučaj. Da bi smo imali funkciju koja radi sa dinamičnim podacima, moramo koristiti parametre i argumente. To su u
suštini ulazni podaci za vašu funkciju.

```php
<?php

calculator(1, 3, 'add');

function calculator($firstNumber, $secondNumber, $operation)
{

	if ($operation == 'add') {
		$result = $firstNumber + $secondNumber;
	} elseif ($operation == 'subtract') {
		$result = $firstNumber - $secondNumber;
	} elseif ($operation == 'multiply') {
		$result = $firstNumber * $secondNumber;
	} elseif ($operation == 'divide') {
		$result = $firstNumber / $secondNumber;
	} else {
		$result = 'Pogresna operacija.';
	}

	echo 'Rezultat je: ' . $result;
}

?>
```

## Argumenti vs Parametri

Vredi se osvrnuti malo na razliku između parametara i argumenata. Najjednostavnije objašnjenje jeste da su argumenti
podaci koje šaljemo funkciji, a parametri su promenljive u koje se ti podaci smeštaju. Ako pogledamo prethodni primer,
u tom slučaju su parametri funkcije ```$firstNumber```, ```$secondNumber``` i ```$operation```. A u pozivu funkcije 
```calculator(1, 3, 'add')``` su ```1```, ```3``` i ```'add'``` argumenti.

Da ne bude zabune, promenljive se mogu koristiti i u toku pozvanja funkcije, kao što smo to i do sada radili sa 
```var_dump``` i ```print_r()``` funkcijama. Npr, sledeća dva poziva funkcije ```calculator()``` su ista:

```php
<?php 
// u oba slucaja koristimo iste argumente:

calculator(1, 3, 'add');

$a = 1;
$b = 3;
$op = 'add';
calculator($a, $b, $op);
?>
```

Kada napravimo neku funkciju, prva prednost je ta što je sada možemo testirati u više varijanti, u samo par redova. Pa 
ajde onda ovu funkciju da testiramo:


```php
<?php

function calculator($firstNumber, $secondNumber, $operation)
{

	if ($operation == 'add') {
		$result = $firstNumber + $secondNumber;
	} elseif ($operation == 'subtract') {
		$result = $firstNumber - $secondNumber;
	} elseif ($operation == 'multiply') {
		$result = $firstNumber * $secondNumber;
	} elseif ($operation == 'divide') {
		$result = $firstNumber / $secondNumber;
	} else {
		$result = 'Pogresna operacija.';
	}

	echo 'Rezultat je: ' . $result . '<br />';
}


calculator(1, 3, 'add');
calculator(1, 3, 'subtract');
calculator(1, 3, 'multiply');
calculator(1, 3, 'divide');
calculator(1, 0, 'divide');

?>
```

Sad smo isprobali sve moguće rezultate(ne računajući one koji dovode do PHP greške). Ali sada imamo malo nečitak ispis:

```
Rezultat je: 4
Rezultat je: -2
...
```

Vežba: Bilo bi korisnije kada bismo videli koje brojeve, koje operacije koriste. Promenite funkciju tako da ispis bude:

```
Rezultat operacije 1 add 3 je 4
Rezultat operacije 1 subtract 3 je 2
...
```

Možete to i lepše uraditi ako ste raspoloženi za vežbu: da ispiše matematički, npr: ``` 1 + 3 = 4 ```.

## Variable Scope

Još jedna značajna stavka kod funkcija jeste ponašanje promenljivih, odnosno njihov doseg(eng: scope). Pogledajmo
sledeći primer:

```php
<?php
function calculator($firstNumber, $secondNumber, $operation)
{

	if ($operation == 'add') {
		$result = $firstNumber + $secondNumber;
	} elseif ($operation == 'subtract') {
		$result = $firstNumber - $secondNumber;
	} elseif ($operation == 'multiply') {
		$result = $firstNumber * $secondNumber;
	} elseif ($operation == 'divide') {
		$result = $firstNumber / $secondNumber;
	} else {
		$result = 'Pogresna operacija.';
	}

	echo 'Rezultat je: ' . $result . '<br />';
}


calculator(1, 3, 'add');
?>
```

Primera radi, ako bismo probali van funkcije da koristimo promenlijvu ```$result```, dobili bi grešku da ta promenljiva
ne postoji. Znači sledeći primer bi izbacio grešku:

```php
<?php
function calculator($firstNumber, $secondNumber, $operation)
{

	if ($operation == 'add') {
		$result = $firstNumber + $secondNumber;
	} elseif ($operation == 'subtract') {
		$result = $firstNumber - $secondNumber;
	} elseif ($operation == 'multiply') {
		$result = $firstNumber * $secondNumber;
	} elseif ($operation == 'divide') {
		$result = $firstNumber / $secondNumber;
	} else {
		$result = 'Pogresna operacija.';
	}

	echo 'Rezultat je: ' . $result . '<br />';
}


calculator(1, 3, 'add');
echo $result; // dolazi do greške

?>
```

Ali ajde da se vratimo na neki manji primer. Obična funkcija za ispisivanje imena i pozdravljanja:

```php
<?php

$myName = 'Nick';
greetings($myName);

function greetings($name) {
	echo 'Hi ' . $name . '!';
}
?>
```

Ovaj primer radi kako treba. Ali ako bismo probali koristiti ```$myName``` unutar funkcije, ili ```$name``` van nje,
dobili bi smo greške.

```php
<?php

$myName = 'Nick';
greetings($myName);

function greetings($name) {
	echo 'Hi ' . $name . '!';

	// $myName ne postoji unutar funkcije
	echo '$myName is ' . $myName;
}

// $name ne postoji van funkcije
echo '$name is ' . $name;

?>
```

Zapamtite, za funkciju jedino postoje promenljive koje ona dobije preko parametara, i koja unutar sebe definiše.
Isto tako, code koji se izvršava nema pristup promenljivama koje su definisane u funkcijama koje se pozivaju. 
(Izuzetak su globalne promenljive, ali više o njima neki drugi put)

## Default values

Prethodna funkcija ```function greetings($myName)``` će nam izbaciti grešku u slučaju da joj ne prosledimo neki podatak za
taj jedan parametar. Na primer, kad bismo je pozvali ovako: ```greetings()``` izbacila bi grešku da funkcija očekuje
jedan parametar. To je zato što se taj parametar smatra obaveznim.

Postoji i način da se određeni parametri tretiraju kao neobavezni. Na primer:

```php
<?php

greetings();

function greetings($name = '') {
	echo 'Hi ' . $name . '!';

	echo '$myName is ' . $myName;
}

?>
```

U ovom slučaju, promenljiva ```$name``` će biti prazan string ako ništa nije prosleđeno u funkciju. To nije strašno
korisno sada, ali bar ne izbacuje grešku. Možemo staviti i određenu vrednost da ima, ne mora to biti prazan string:

```php
<?php

greetings();

function greetings($name = 'Unknown') {
	echo 'Hi ' . $name . '!';

	echo '$myName is ' . $myName;
}

?>
```

Ovaj code će sada ispisati ```$myName is: Unknown``` što može biti korisno u određenim situacijama. Isto tako možemo
davati podrazumevane vrednosti većem broju parametara u funkciji, npr:

```php
<?php
function calculator($firstNumber, $secondNumber = 0, $operation = 'add')
{

	if ($operation == 'add') {
		$result = $firstNumber + $secondNumber;
	} elseif ($operation == 'subtract') {
		$result = $firstNumber - $secondNumber;
	} elseif ($operation == 'multiply') {
		$result = $firstNumber * $secondNumber;
	} elseif ($operation == 'divide') {
		$result = $firstNumber / $secondNumber;
	} else {
		$result = 'Pogresna operacija.';
	}

	echo 'Rezultat je: ' . $result . '<br />';
}


calculator(1);
calculator(3, 3);
calculator(4, 3, 'subtract');

?>
```

Izmenili smo funkciju ```calculator()``` tako da je obavezan samo prvi parametar. Druga dva imaju 'default' vrednosti
```0``` i ```'add'``` u slučaju da nisu prosleđeni argumenti na tim pozicijama. U slučaju da pozivamo funkciju sa svim
argumentima, tada će ona koristiti vrednosti koje smo prosledili.

## Return

Funkcije koje ispisuju podatke imaju svoju svrhu, poput ```print_r()``` i ```var_dump```, ali velika većina funkcija
ne ispisuje vrednost direktno na ekran. Većina funkcija vraća neku vrednost, nakon čega programerer može da odluči da li
da taj podatak ispiše ili da radi još nešto sa njim.

Primer takve funkcije je ```date()```. Ako samo napišemo samo ```date('Y');```, to samo po sebi neće ispisati trenutnu
godinu. Proračun će se desiti u pozadini, ali neće biti ispisan na ekran. Da bi ispisali rezultat morali  bi koristiti
```echo date('Y');```. Počnimo sa nekim veoma jednostavnim primerima:

```php
<?php
function getTheNumberThree() {
	return 3;
}
?>
```

Funkcija ```getTheNumberThree()``` nije naročito korisna, ali je koristimo da bi videli šta radi ```return```. Na
primer, ako bismo pozvali ovu funkciju samo, ne bi došlo do ispisa na ekranu. Zato nam treba ```echo```.

```php
<?php
function getTheNumberThree() {
	return 3;
}

getTheNumberThree(); // nece ispisati nista na ekran

$number = getTheNumberThree();
echo $number; // tu vec dobijamo ispis 3

echo getTheNumberThree(); // a mozemo i preskociti promenljivu, i direktno koristiti funkciju uz echo

?>
```

Znači, za razliku od dosadašnjih funkcija koje smo pisali, ova ne ispisuje direktno na ekran, nego nam vraća neku
vrednost. Sad ćemo to primeniti na naš digitron.


```php
<?php
function calculator($firstNumber, $secondNumber = 0, $operation = 'add')
{

	if ($operation == 'add') {
		$result = $firstNumber + $secondNumber;
	} elseif ($operation == 'subtract') {
		$result = $firstNumber - $secondNumber;
	} elseif ($operation == 'multiply') {
		$result = $firstNumber * $secondNumber;
	} elseif ($operation == 'divide') {
		$result = $firstNumber / $secondNumber;
	} else {
		$result = 'Pogresna operacija.';
	}

	$message = 'Rezultat je: ' . $result . '<br />';

	return $message;
}

//Napomena: morali smo dodati echo da bi došlo do ispisa
echo calculator(1);
echo calculator(3, 3);
echo calculator(4, 3, 'subtract');

?>
```

Hmm, ali ipak nije baš smisleno da funkcija za digitron vraća poruku u slučaju računanja(osim ako se nešto neočekivano
desilo). Promenićemo naš digitron da vraća samo rezultat matematičke operacije.

```php
<?php
function calculator($firstNumber, $secondNumber = 0, $operation = 'add')
{

	if ($operation == 'add') {
		$result = $firstNumber + $secondNumber;
	} elseif ($operation == 'subtract') {
		$result = $firstNumber - $secondNumber;
	} elseif ($operation == 'multiply') {
		$result = $firstNumber * $secondNumber;
	} elseif ($operation == 'divide') {
		$result = $firstNumber / $secondNumber;
	} else {
		$result = 0; // smatraćemo da je rezultat nula u slučaju deljenja sa nulom
	}

	return $result;
}

$result = calculator(100, 50);
echo 'Rezultat je ' . $result;

echo '<br />';
echo $calculator($result, 2, 'multiply'); // koristiom rezultat prošle operacije i množimo ga sa 2

?>
```

Ova funkcija za digtron ima više smisla. Programer koji je koristi sada može da odluči šta će raditi sa rezultatom.
Može ga odmah ispisati ako treba, a može da nastavi da koristi taj rezultat za dalje operacije.

Sad kad znamo za ```return```, možemo pisati više manjih funkcija, koje će se nadovezivati sa rezultatima. Napisaćemo
funkcije koje će vršiti određene operacije na nekom nizu, i vraćati rezultat.


```php
<?php

function removeStrings($array) {
	foreach ($array as $key => $value) {
		if (is_string($value)) {
			unset($array[$key]);
		}
	}
	return $array;
}

function getArraySum($array) {
	$sum = 0;
	foreach ($array as $key => $value) {
		$sum = $sum + $value;
	}
	return $sum;
}

$array1 = [
	1,
	200,
	'555',
	33,
	'333-333',
	'John',
	'<>'
];

$arrayWithoutStrings = removeStrings($array1);

echo getArraySum($arrayWithoutStrings);

?>
```

Gde god je moguće koristite ```return``` u vašim funkcijama. Kao takve su mnogo korisnije i fleksibilnije.

## Include

Još jedna stavka pre nego što pređemo na zadatke. ```include()``` je veoma korisna funkcija za organizovanje coda.
Njena svrha je da, tako reći, "uključite" određeni PHP fajl unutar drugog php fajla. Neki jednostavan primer:

```php
<?php
// ispisbrojeva.php - ime fajla

$one = 'jedan';
$two = 'dva';
$three = 'tri';

echo $one . $two . $three;

?>
```

Gornji code će ispisati ```jedandvatri```. Izmenićemo ga da koristi ```include()``` i dva fajla.

```php
<?php
// brojevi.php

$one = 'jedan';
$two = 'dva';
$three = 'tri';

?>
```


```php
<?php
// ispis.php

include('brojevi.php');

echo $one . $two . $three;

?>
```

Da bi gornji code sa dva fajla radio, ovi fajlovi moraju biti u istom folder, ali inače to nije obavezno. 
```include()``` možete smatrati kao način da sav vode iz nekog drugog fajla koristite u trenutnom fajlu iz kojeg
pozivate ```include()```. Ovo postaje naročito korisno na projektima na kojima imate više fajlova, u kojima želite
koristiti iste funkcije. Uz pomoć ```include()``` možete napisati sve vaše funkcije u jedan fajl, i onda taj fajl
pozivati sa ```include()``` u fajlovima u kojima su vam potrebne.

Na primer, ako uzmemo našu funkciju za digitron i stavimo je u fajl sa imenom ```functions.php```, moćemo je koristiti
u drugom fajlu u kojem koristimo ```include()```.

```php
<?php
// functions.php

function calculator($firstNumber, $secondNumber = 0, $operation = 'add')
{

	if ($operation == 'add') {
		$result = $firstNumber + $secondNumber;
	} elseif ($operation == 'subtract') {
		$result = $firstNumber - $secondNumber;
	} elseif ($operation == 'multiply') {
		$result = $firstNumber * $secondNumber;
	} elseif ($operation == 'divide') {
		$result = $firstNumber / $secondNumber;
	} else {
		$result = 0; // smatraćemo da je rezultat nula u slučaju deljenja sa nulom
	}

	return $result;
}
?>
```

```php
<?php
include('functions.php');

echo calculator(1, 3);

?>
```


Zadaci za vežbu:

* Uzeti postojeću ```calculator()``` funkciju i zameniti određene operacije u njoj sa novim, manjim funkcijama. Red sa
sabiranjem zamenite sa novom funkcijom ```getSum()``` koja samo sabira dva broja i vraća rezultat. 

* Na isti način, napisati funkcije ```getDifference()``` i  ```getProduct()``` i iskoristiti ih gde ima smisla. 

* Sve ove funkcije držite u zasebnom fajlu ```functions.php```, i taj fajl "uključite" u fajl sa kojim radite.

* Napišite funkciju ```removeZeroes()``` koja za unešeni niz vrati isti taj niz, samo bez nula.

* Napišite funkciju koja briše sve brojeve iz niza koji su manji od nule ```removeNegatives()```. Ulazni parametar je
niz, a treba da vrati taj niz bez negativnih brojeva.

* Sad kada imate te dve funkcije, pozovite ih jednu za drugom, na istom nizu, npr: ```$array1 = [1, 0, -5, 10]```.
Nakon pozivanja obe funkcije, ispišite krajnji rezultat na ekran, koji bi trebao da bude niz sa elementima 1 i 10.