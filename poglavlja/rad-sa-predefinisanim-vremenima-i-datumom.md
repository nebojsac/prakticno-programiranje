# Rad sa predefinisanim vremenima i datumom

Iako je zanimljivo raditi sa promenljivim datumom kojeg dobijamo sa ```date()```, u praksi se češće koristi uz njen drugi parametar, koji određuje sa kojim vremenom radimo.

Među vama dostupnim podacima na projektima će te skoro sigurno imati datume i vremena. Bilo to vreme registracije na sajtu, vreme slanja poruke ili vreme poslednjeg plaćanja. 

Ako bismo napisali neki proizvoljni opis parametara ```date()``` funkcije, to bi bio: ```date($formatDatuma, $trenutnoVreme)```. Dakle, sa prvim parametrom smo već upoznati, i on može biti kombinacija slova i simbola uz pomoć kojih dobijamo željeni format, od kojih je(bar na serveru) najčešći ```Y-m-d H:i:s```. 

Drugi parametar, se podrazumeva da je u pitanju trenutno vreme, ako ga ne damo. Znači ```default``` vrednost je trenutno vreme. U prethodnom poglavlju imamo primere za to, poput ```echo date('Y');``` za ispis trenutne godine. Ako želimo da koristimo drugi parametar, on mora biti broj u obliku ```Unix``` vremena, koje je napamet teško pisati, i generalno se koriste pomoćne funkcije za to. Da počnemo sa primerom:

```php
<?php
$unixTime = strtotime('2016-04-01');
$registrationDate = date('M jS', $unixTime);

echo 'The user registered on ' . $registrationDate;
?>
```

Rezultat ovog bi trebao da bude ```The user registered on Apr 1st```. Nova funkcija nam je ```strtotime()``` koja pretvara dati tekst(odnosno ```string```) u Unix vreme. To nam je potrebno za pozivanje ```date()``` funkcije na način koji će nam dati očekivani rezultat. 

Format ```M jS``` već vidite šta ispisuje: Skraćeni oblik naziva meseca ```M```, pa broj dana u mesecu ```j```, i na kraju ```S``` sufix za dan u mesecu(st,nd,th). Koji će se dan/mesec ispisati zavisi od tog drugog parametra.

Takođe možemo izračunavati i relativne datume uz pomoć ```strtotime()```, jer sem brojčanih datuma ume da tumači i reči.

```php
<?php
$unixTime = strtotime('2 weeks ago');
$twoWeeksAgo = date('M jS', $unixTime);

echo 'Two weeks ago it was ' . $twoWeeksAgo;
?>
```

Ovaj primer bi trebao da vam ispiše koji je datum bio pre dve nedelje. Još neki interesantni tekstualni primeri kojeg prepoznaje ta funkcija:

* 'next Monday'
* 'next year'
* '5 days ago'

Ima ih još mnogo, ali nema smisla ih ispisati ovde. Po potrebi se mogu naći na Google-u.

Takođe vredi podsetiti da možemo sve ovo ispisati u jednom redu. Iako je generalno bolje razdvajati funkcije radi čitljivosti, ```date()``` funkcija je sama po sebi dovoljno jasna u kombinaciji sa ```strtotime()``` da to ima smisla u ovom slučaju:

```php
<?php
echo 'Two weeks ago it was ' . date('M jS', strtotime('2 weeks ago'));
?>
```

Uopšte nam ni promenljive ne trebaju tu, možemo direktno pozivati ove funnkciju u ```echo``` redu. A sada ste vi na redu:

* U promenljivu ```$myBirthday``` stavite datum vašeg rođenja.
* U promenljivu ```$myBirthdayUnixTime``` isti taj datum u Unix vremenskom formatu, koristeći se ```$myBirthday``` promenljivom.
* U promenljivu ```$now``` stavite trenutno vreme u Unix vremenskom formatu(savet, kombinovanjem ```date()``` i ```strtotime()``` funkcija, ovo je malko teže). Ako zapnete, koristite google.
* Unix vremenski format predstavlja broj sekundi od određenog datuma. Uz pomoć podataka koje imate, izračunajte koliko je sekundi prošlo od vašeg rođenja. Za bonus izračunajte koliko je dana prošlo od tada.