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

$weekDays = [
	'Ponedeljak' => ['izneti smeće'],
	'Utorak' => ['zvati babu'],
	'Sreda' => ['teretana, noge'],
	'Četvrtak' => ['oprati kola', 'pokositi travu'],
	'Petak' => ['teretana, ruke'],
	'Subota' => ['shopping'],
	'Nedelja' => []
];

print_r($weekDays);

echo 'Prvog dana treba ' . $weekDays['Ponedeljak'][0];
?>
```

Da se podsetimo, ```echo``` je koristan ako želimo ispisati neki tekst, ili vrednost neke promenljive, ali nije dovoljan za nizove. ```echo $weekDays``` bi samo ispisalo ```Array```, što nam i nije mnogo korisno. Zato koristimo ```print_r()```. Ali elementi niza su isti kao "obične" promenljive, pa ako koristimo indeks niza, onda možemo koristiti ```echo```. Primetite da je ovo niy koji sadrži u sebi sedam pod-nizova. Glavni niz je indeksiran tekstualno ```'Ponedeljak', 'Utorak'...``` dok su pojedinačni podnizovi samo popunjeni, što im automatski daje brojčane indekse, počevši od nule.

Takođe, obratite pažnju kako su različite vrednosti podnizova. ```'Ponedeljak'``` ima jedan element, ```'Četvrtak'``` ima dva a ```'Nedelja'``` nema ni jedan, odnosno sadrži prazan niz ```[]```. Primera radi, možemo ih tako pojedinačno ispisati:

```php
<?php

$weekDays = [
	'Ponedeljak' => ['izneti smeće'],
	'Utorak' => ['zvati babu'],
	'Sreda' => ['teretana, noge'],
	'Četvrtak' => ['oprati kola', 'pokositi travu'],
	'Petak' => ['teretana, ruke'],
	'Subota' => ['shopping'],
	'Nedelja' => []
];

echo 'Ponedeljak:';
print_r($weekDays['Ponedeljak']);

echo 'Četvrtak:';
print_r($weekDays['Četvrtak']);

echo 'Nedelja:';
print_r($weekDays['Nedelja']);

?>
```

U slučaju 'nedelje' je možda korisniije koristiti ```var_dump()```, ali to ostavljam vama da isprobate na tom i ostalim podnizovima.

//TODO:
// for petlja za ispis dana
// foreach petlja za ispis spisaka
