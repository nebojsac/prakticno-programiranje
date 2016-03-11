# POST i GET

O ovome se može dosta pisati, ali ovo će biti dovoljno za početak:

**POST** metoda slanja podataka na drugu stranu obično znači da se podaci šalju preko neke html forme, poput Login-a za neki sajt. Forma mora biti i podešena da koristi POST metodu. Primer forme za slanje, i PHP koda za primanje, POST podataka:
```php
<form method="POST">
	username:<input type="text" name="username" placeholder="korisničko ime"/>
	password:<input type="password" name="password" />
	<input type="submit" value="Pošalji" />
</form>
<?php
$username = $_POST['username'];
$password = $_POST['password'];

// ta dva reda gore će izbacivati grešku ako ti podaci ne postoje. Da se to izbegne koristite:
if (isset($_POST['username'])) { // isset() funkcija vraća "false" boolean ako ne postoji dati podatak
	$username = $_POST['username'];

	echo '<br /> $username je :' . $username;
} 
if (isset($_POST['password'])) {
	$password = $_POST['password'];

	echo '<br /> $password je :' . $password;
} 
?>
```

Pvi deo predstavlja HTML code. U vašem browseru bi trebalo da se pojave ta dva polja koja su tipična za mnoge sajtove koja možete koristiti za testiranje ovog gore k**o**da. Od svega toga, za sada, treba samo da znate vezu između tih polja i php k**o**da za ispis. Nećemo se mnogo zadržavati na ovome:
* Pojedinačni html "tagovi" se nalaze između ```<``` i ```>```. Npr ```<form>```. 
* Tagovi označavaju početak i kraj nekog elementa. Tag za zatvaranje počinje sa ```</```, npr ```</form>```.
* Svaki element se sastoji iz taga za otvaranje i taga za zatvaranje(```<form><form>```) ali se može pisati skraćeno tako što se na kraj prvog taga stavi ```/>```, npr: ```<input type="text" />``` ili ```<br />```.
* Elementi mogu imati atribute. Npr, u ovom elementu ```<input type="password" name="password" />``` atributi su ```type``` i ```name```. 
* ```type``` atribut nam govori kog je tipa ovo polje za unos. Ako je ```text``` onda vidimo šta pišemo. Ako je ```password``` onda ne vidimo dok unosimo tekst, odnosno šifru.
* ```name``` nam govori naziv ```$_POST``` promenljive kada se podaci pošalju. Npr, ako za ```<input type="password" name="password" />```, do sadržaja tog polja posle slanja ćemo doći uz pomoć ```$_POST['password']```. U pitanju je promenljiva tipa "niz", ali više o tome posle.

Ova poslednja stavka vam je jedina bitna za sada, ali zato je i pročitajte ponovo.

U gornjem primeru koristimo novu funkciju, ```isset()```. Ona se koristi za proveru postojanja neke promenljive ili nekog podatka. Da bi bolje razumeli to, pogledajmo sledeći k**o**d:

```php
<?php

$godina = 2016;

if (isset($godina)) {
	echo 'Promenljiva $godina postoji.';
} else {
	echo 'Promenljiva $godina postoji.';
}

echo '<br />';

if (isset($mesec)) {
	echo 'Promenljiva $mesec postoji.';
} else {
	echo 'Promenljiva $mesec postoji.';
}
?>
```
Pokrenite taj primer da vidite šta se ispiše. Ako pogledate ```isset($godina)```, to se može čitati kao "Da li je postoji promenljiva $godina?", odnosno "Da li je setovana/podešena?". ```isset()``` funkcija kao takva vraća istinitost(boolean), dakle, ```true``` ili ```false```. Ako promenljiva postoji, vraća ```true```. U ovom primeru smo podesili promenljivu ```$godina``` na početku, dakle, ona postoji. Ali promenljivu ```$mesec``` nismo nigde podesili, dakle, ona ne postoji. ```isset()``` se najčešće koristi kod slanja podataka POST i GET metodom, radi provere.

**GET** metoda slanja podataka je praktično slanje podataka kroz adresu stranice. Obratite pažnju koja je adresa u browseru gde testirate kod. Verovatno počinje sa ```localhost``` jer radite u Xampu, pa onda sledi ```/folder/``` ili ```/prakticno/```, nakon čega je fajl u kojem radite, poput ```test.php```, ```index.php``` ili ```get.php```. Primera radi, ako imate adresu koja se završava sa get.php, vi na nju možete nakačiti još podataka preko GET metode koristeći upitnik pre prvog podatka, i ampersand **&** pre svakog sledećeg. Pretpostaviću da vam je ovaj code na adresi http://localhost/prakticno/get.php - Primer bi bio adresa http://localhost/prakticno/get.php?id=123&action=edit. U tom slučaju možete pristupiti podacima uz ovaj kod:

```php
<?php
if (isset($_GET['id'])) { // isset() funkcija vraća "false" boolean ako ne postoji dati podatak
	$id = $_GET['id'];
} else {
	$id = 0;
}
if (isset($_GET['action'])) {
	$action = $_GET['action'];
} else {
	$action = 'neispravan';
}

echo '$id je ' . $id;
echo '<br />';
echo '$action je' . $action; 
?>
```

Na ekranu bi trebalo da vidite ```$id je 123``` i ```$action je edit```. Ako vidite ```$id je 0``` i ```$action je neispravan``` onda ste zaboravili dodati ```?id=123&$action=edit``` na kraj adrese u browseru. Da probamo još malo pojasniti šta se tu dešava:

? - sa upitnikom označavamo da je ovo kraj imena fajla (get.php, ili štagod) i da tu počinju ```GET``` promenljive. 
GET promenljive idu u parovima ```ime``` i ```vrednost```, odnosno ```ime=vrednost```. Pod ```ime``` bi bilo tačnije reći ```index```, ali možete reći da vam je taj levi deo jednakost ```ime=vrednost``` oznaka ```GET``` promenljive. Sa desne strane te jednakost ide vrednost koju dodeljujete. Dakle, ako imate adresu ```get.php?ime=vrednost```, onda toj ```GET``` promenljivoj pristupate na sledeći način:

```php
<?php
echo $_GET['ime'];
?>
```
Promenite sad ```ime``` u adresi u nešto drugo, npr ```broj```, i isto to stavite u kod ```echo $_GET['broj'];```, da vidite o čemu pričam. Sad menjajte desnu stranu jednakosti u neki broj, i opet osvežite stranicu, da vidite kako se menja. 

Isto tako možete imati više ```GET``` promenljivih u adresi, npr: http://localhost/prakticno/get.php?http://localhost/prakticno/get.php?id=123&action=edit&ime=Stevo. Svaka ```GET``` promenljiva se odvaja sa ```&``` od prethodne, znači ```?id=123&action=edit&ime=Stevo```. Sad ću odvojiti GET promenljive da bude malko preglednije, ali i neispravno: ```? id=123 & action=edit & ime=Stevo```. Da vidimo šta se tu dešava, ubacićemo ih sve u echo:
```php
<?php
echo 'id: ' . $_GET['id'];
echo '<br />'; // ovo je samo novi red radi preglednosti
echo 'action: ' . $_GET['action'];
echo '<br />';
echo 'ime: ' . $_GET['ime'];
?>
```

Ovaj kod ispisuje vrednosti GET promenljivih, ako ih ima, ali će izbaciti greške ako one ne postoje. Zato koristimo isset() funkciju iz prvog koda:
```php
<?php
if (isset($_GET['id']) AND isset($_GET['action']) AND isset($_GET['ime'])) {
	echo 'id: ' . $_GET['id'];
	echo '<br />'; // ovo je samo novi red radi preglednosti
	echo 'action: ' . $_GET['action'];
	echo '<br />';
	echo 'ime: ' . $_GET['ime'];
} else {
	echo 'Nesto fali';
}
?>
```
Ako na ekranu piše ```Nesto fali```, onda morate proveriti da li u adresi u browseru imate sve tri promenljive. isset() funkcija proverava da li određena promenljiva postoji, i vraća ```true``` ili ```false``` na osnovu toga. U ovom primeru ćemo ispisati sve promenljive samo ako save promenljive postoje. Ako bilo koja fali, ispisaće ```Nesto fali```. Probajte sledeće:

* Ubacite svoje ime u promenljivu ```ime```
* Zamenite promenljivu ```action``` sa promenljivom ```akcija```, a vrednost joj promenite u ```izmena```.
* Dodajte još jednu GET promenljivu na adresu i ispišite je na ekranu sa kodom.
* Vežbajte. Počnite sa novim fajlom, od nule, nek se zove ```getproba.php```. Napišite prvo k**o**d koji ispisuje vrednost GET promenljive ```boja```. Stavite taj k**o**d za ispis unutar **if** bloka koji proverava da li ta promenljiva postoji. Ako ne postoji, nek se ispiše ```ne postoji```. Isprobajte vaš k**o**d sa i bez GET promenlijve ```boja```. 

Postoje situacije u kojima je obavezno koristi POST metoda, poput registracije i logina, i situacije u kojima je bolje koristiti GET metodu, kao što je izlistavanje podataka, pretraga, itd.

**NAPOMENA** podaci koji su primljeni preko POST ili GET metode obavezno tretirati kao nebezbedne. Maliciozni korisnici mogu da menjaju njihov sadržaj i jedan su od najlakših načina da se hakuje sajt ako nije zaštićen. Srećom, nije se teško obezbediti od toga, samo treba imati ovo na umu. Bezbednost ćemo kasnije pokriti.
