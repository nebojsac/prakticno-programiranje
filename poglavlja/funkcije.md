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

//TODO parametri vs argumenti
//TODO pozovemo funkciju u sve 4 kombinacije
//TODO prosirimo funkciju da ima lepsi ispis (a + b = rez)
//TODO variable scope
//TODO default vrednost parametra
//TODO calculatorDivide(), return values





//TODO: zadaj zadatke