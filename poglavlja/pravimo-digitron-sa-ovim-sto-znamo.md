# Pravimo digitron sa ovim što znamo

## Jednostavna HTML forma

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