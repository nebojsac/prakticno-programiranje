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

Nastaviće se...