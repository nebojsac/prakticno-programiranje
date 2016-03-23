# Osnove nizova

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

Zadaci: 
* Napravi niz ```$daniNedelje``` da sadrži dane od Ponedeljka do Nedelje. 
* Ispiši ceo niz sa ```print_r()```. A sad ispiši samo jedan elemenat, na primer "sredu", sa ```echo```.
* Sad napravi niz indeksiran tekstom, za broj meseca(npr, ```'septembar'=>9```, za zimske mesece. Dakle ```$zimskiMeseci```. Posle toga ispiši sa ```echo``` samo vrednost indeksiranu tekstom ```'decembar'```
