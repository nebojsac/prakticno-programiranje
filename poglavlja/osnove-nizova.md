# Osnove nizova

Čisto da bi razumeli šta se tu dešava da spomenemo nizove(eng. arrays). Niz je skup podataka i možete ga držati u jednoj promenljivoj. Podaci su takoreći **indeksirani** i pristupa im se na osnovu tih indeksa koji mogu biti brojevi ili stringovi(odnosno tekst). 

Počnimo sa par nizova:

```php
<?php
$emptyArray = [];
echo "prazan niz je:";
print_r($emptyArray);

$arrayWithOneElement = [999]
echo 'Niz sa jednim elementom:';
print_r($arrayWithOneElement);


$oddNumbers = [1, 3, 5, 7, 9];
echo 'Neparni brojevi:';
print_r($oddNumbers);

?>
```
* ```print_r()``` je funkcija sa kojom možemo ispisati sadržaj niza na ekran. Poprilično je nepregledno, ali imamo bolje rešenje u sledećem primeru.
* ```var_dump()``` može da se koristi kao potencijalna alternativa za ispis celog niza.
* Niz se definiše sa uglastim zagradama ```[]```. U starijim verzijama PHP-a se definisao ```array()```, ali je sa uglastim zagradama preglednije.
* Niz može sadržati druge tipove podataka, dakle, brojeve, tekstove, pa čak i druge nizove(podnizove).

Što se tiče vašeg programa, svaki elemenat niza ima svoj "index". To možete smatrati njegovim rednim brojem. Na primer, ako imamo niz ```[123, 156]```, njihovi redni brojevi su 0 i 1 - jer u programiranju, redni brojevi kreću od nule. 

Postoji način da na ekranu lakše vidimo redne brojeve u nizu, ako koristimo malo dodatnog html-a, tagove ```<pre></pre>```. Ispisivaćemo njih oko nizova koje ispisujemo. Izmenjeni prvi primer je onda:


```php
<?php
$emptyArray = [];
echo "prazan niz je:";
echo "<pre>";
print_r($emptyArray);
echo "</pre>";

$arrayWithOneElement = [999]
echo 'Niz sa jednim elementom:';
echo "<pre>";
print_r($arrayWithOneElement);
echo "</pre>";


$oddNumbers = [1, 3, 5, 7, 9];
echo 'Neparni brojevi:';
echo "<pre>";
print_r($oddNumbers);
echo "</pre>";

?>
```

* Ako stavimo tagove ```<pre></pre>``` oko ispisanih nizova, cela stvar postane preglednija.
* Sad su indeksi u nizovima očigledni, prikazani su sa leve strane simbola ```=>```. 
* Prazan niz nema ništa, niz sa jednim elementom ima samo indeks ```0```, a neparni brojevi imaju redne brojeve od 0 do 4.

Indeksi su korisni za ispis pojedinačnih elemenata nizova:

```php
<?php
$oddNumbers = [1, 3, 5, 7, 9];

echo $oddNumbers[0];
?>
```
* Pristupamo prvom elementu niza tako što posle promenljive koja drži taj niz stavimo uglaste zagrade sa rednim brojem elementa: ```$oddNumbers[0]```
* Ispis jednog elementa niza možemo raditi sa echo.
* Ako probamo pristupiti nepostojećem elementu, odnosno ako koristimo redni broj koji ne postoji kao indeks u tom nizu, doćiće do greške, npr: ```$oddNumbers[5]```. 
* Trenutno niz ima samo 5 elemenata, dakle, najveći redni broj je 4, jer počinju od nule.

Ako želimo i ostale elemente ispisati:

```php
<?php
$oddNumbers = [1, 3, 5, 7, 9];

echo $oddNumbers[0];
echo $oddNumbers[1];
echo $oddNumbers[2];
echo $oddNumbers[3];
echo $oddNumbers[4];
?>
```
Ostaviću vama da ovaj i sledeći ispis napravite preglednijim.

Da podsetim, nizovi mogu imati i druge tipove podataka. Na primer:

```php
<?php
$oddNumbers = ['jedan', 'tri', 'pet', 'sedam', 'devet'];

var_dump($oddNumbers);
?>
```

Ako samo definišemo elemente niza, kao što smo do sada radili, PHP će ih sam indeksirati rednim brojevima, počevši od nule. Ali možemo i sami podesiti i indekse:

```php
<?php
$oddNumbers = [
	1 => 'jedan', 
	3 => 'tri', 
	5 => 'pet', 
	7 => 'sedam', 
	9 => 'devet'
];

var_dump($oddNumbers);
?>
```

* Sad nam se tekstualni elmenti poklapaju sa indeksima, jer smo precizirali i indekse. 
* Kada unutar niza ```[]``` koristimo "strelicu" ```=>```, mi definišemo indeks i podatak. Sa leve strane ide indeks, a sa desne podatak.
* Sad smo definisali niz u više redova koda radi preglednosti, ali to ne utiče na sadržaj. Isti bi efekat bio da smo pisali ```$oddNumbers[1=>'jedan', 3=>'tri' ...]```, samo bi bilo manje čitko.
* Koristeći niz ```$oddNumbers``` kojeg smo gore definisali, kako biste na ekran ispisali samo ```sedam```?

Bitno je znati da indeksi nizova ne moraju biti brojevi, već mogu i oni sami biti tekstovi:

```php
<?php
$oddNumbers = [
	'jedan' =>  1, 
	'tri' =>  3, 
	'pet' =>  5, 
	'sedam' =>  7, 
	'devet' =>  9
];

var_dump($oddNumbers);
?>
```

* Isto kao i do sada, da bi ispisali jedan element, koristimo njegov indeks.
* Na primer, da bi pristupili elementu ```9```, koristimo ```$oddNumbers['devet']``` - obratite pažnju da su navodnici potrebni, jer je u pitanju tekst, a ne integer(broj).

Ovaj pregled je bitan jer su POST i GET promenljive nizovi, i sva pravila nizova važe i za njih. To je sve što trebate znati vezano za nizove za sledeći zadatak, a kasnije ćemo se vratiti na rad sa nizovima.

Zadaci: 

* Napravi niz ```$daysOfTheWeek``` da sadrži dane od Ponedeljka do Nedelje, kao tekstualne podatke. 
* Ispiši ceo niz sa ```var_dump```. A sad ispiši samo jedan elemenat, na primer "sredu", sa ```echo```.
* Sad napravi niz indeksiran tekstom, za broj meseca(npr, ```'septembar'=>9```, za zimske mesece. Dakle ```$winterMonths```. Posle toga ispiši sa ```echo``` samo vrednost indeksiranu tekstom ```'decembar'```
