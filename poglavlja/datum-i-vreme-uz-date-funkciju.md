# Datum i vreme uz date() funkciju

Jedna od ugrađenih kompleta PHP funkcija jesu funkcije koje služe za manipulaciju datumima. Upoznaćemo se sa njima sada jer one prodstavljaju i dobar izvor dinaminčnih podataka.

Vreme se u programiranju uglavnom računa u UTC formatu, koji predstavlja broj sekundi od prvog januara, 1970-e, na engleskom ```UTC timestamp```. Za nas ljude to nije koristan format, iako računar to koristi za (nesavršenu)računicu. Srećom, postoji funkcija ```date()``` koja nam pomaže da dobijemo "čitljiviji" format. Počnimo sa nekim tipičnijim primerima. Ukucajte sledeće u novi fajl ako želite, naprimer date.php, i pristupite mu preko browsera.

```php
<?php  
$currentYear = date('Y');
echo 'Trenutna godina je ' . $currentYear;
?>
```

Funkcija ```date()``` vraća trenutni datum u formatu koji tražimo. U ovom slučaju smo tražili format ```'Y'```, što znači da nam treba trenutna godina. Ako želimo ceo datum i vreme, možemo koristiti:


```php
<?php  
$currentDate = date('Y-m-d H:i:s');
echo $currentDate;
?>
```

Sad smo dobili puni prikaz datuma i vremena, u formatu koji odgovara bazama podataka, a i najbolji je za sortiranje(više o tome kasnije). Format je znači ```godina-mesec-dan sat:minuta:sekunda```. Svako slovo koje ubacimo u ```date()``` predstavlja neki deo datuma kojeg želimo prikazati, a ostali simboli(razmaci, crtice i dvotačke) ostaju gde jesu u formatu. Sem ovoga, možemo raditi neke zanimljivije stvari, poput:


```php
<?php  
$currentDayOfWeek = date('l');
echo 'Today is ' . $currentDayOfWeek;
?>
```

Sad smo dobili nešto poput ```Today is Monday``` zavisno od toga kojeg dana u nedelji pokrećete ovaj k**o**d. Nećemo dalje prelaziti moguće parametre, pretpostavljam da ste shvatili poentu. Da biste videli sve moguće parametre, možete pogledati ovde: http://php.net/manual/en/function.date.php (ili ukucajte "php date" u Google).

Par zadataka pre nego što nastavimo:
* Koristite ```date()``` i uputstva sa linka da odjednom ispišete ceo datum u formatu koji se koristi u Srbiji, npr, 13.06.2014.
* Isto tako ispišite trenutno vreme u formatu 15:45
* Uzmite koliko je sad sati(u formatu bez vodeće nule, znači 1,2,3...22,23) i stavite u promenljivu ```$currentTime```. Napišite k**o**d koji proverava da li je ```$currentTime``` veće od 20 i manje od 8. Ako je taj uslov ispunjen, ispišite ```"Idi spavaj!"```. U suprotnom neka se ispiše koliko je trenutno sati.

Do sada smo radili sa trenutnim vremenom i datumom, ali postoji način da se manipuliše sa vremenom koje unapred odredimo.