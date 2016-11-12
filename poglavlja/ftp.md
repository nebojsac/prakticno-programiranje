# Rad preko FTP-a

`FTP` je skraćeno za `File Transfer Protocol`, što u prevodu predstavlja specifikaciju za prenos fajlova preko interneta.
Bez da idemo u jako sitne tehničke detalje, potrudiću se da objasnim zašto vam je `FTP` bitan za mnogo poslova.

Iako se ne koristi na svim poslovima, šanse su da će više vaših prvih poslova uključivati rad preko FTP-a, pogotovo ako
ga nađete preko neke freelance platforme.

Da bi neki sajt bio dostupan preko interneta, on mora biti postavljen na nekom serveru. Za manje poslove i sajtove, to
uglavnom bude neki _Shared_ hosting tipa GoDaddy, HostGator ili NameCheap. Oni su idealni za malo blogove i vizit-karta
sajtove jer su povoljni(oko $5 mesečno) i može ih i netehnička osoba postaviti(vaš budući klijent).

Bez da detaljišem dalje, u takvoj situaciji vi biste verovatno dobili zadatak da popravite postojeći sajt preko FTP-a.
Da biste to izveli, trebate preuzeti sa interneta neki program za FTP. Iako možete ovo raditi uz pomoć Total Commandera,
ja bih vam preporučio da koristite FileZilla Client(alternativno, CoreFTP).

Suština je ista kao prebacivanje fajlova na računaru. U FTP programu obično imate dve strane, od kojih leva predstavlja
fajlove na vašem računaru, a desna fajlove na serveru. Da biste pristupili serveru, obavezni su vam sledeći podaci:

* `host` (ili hostname) - Obično bude domen sajta, sa poddomenom 'ftp'. Primer: 'ftp.nickcinger.com
* `username` - Korisničko ime za pristup. Primer: 'nebojsa@nickcinger.com' ili samo 'nebojsa'
* `password` - Lozinka za pristup.

Kada imate ove podatke, možete ih uneti u vaš odabrani FTP program da biste pristupili serveru. FileZilla, npr, ima
`Quick Connect` opciju u gornjem delu, gde možete uneti ove podatke i odmah se povezati, a možete i korstiti `Site Manager`
opciju da sačuvate više ovakvih pristupa, za lako korišćenje kasnije(što vam i preporučujem).

Kad se povežete, sa desne strane ćete imate fajlove na serveru. Najčešće se "početak" sajta (koren domena) nalazi u
folderu `public_html` ili `www` pa bih vam preporučio da tamo počnete. Da biste bili sigurni da ste na dobrom mestu,
napravite probni fajl, npr `test.php`, i stavite u njega nešto jednostavno, npr `123`, i `Upload` ga na server.
Trebalo bi da bude dostupan na adresi `imedomena.com/test.php`. Ako jeste, onda ste na dobrom mestu.

**Napomena:** Ako vam klijent da `cPanel` pristup umesto `FTP`-a, onda ste u situaciji da sami sebi morate namestiti `FTP`
pristup. To se radi tako što nađete opciju `FTP Accounts`, i napravite novi `account` na početnoj putanji `/`. U tom
slučaju, sami određujete `username` i `password`, a `hostname` ćete pronaći pod opcijom `Configure FTP client`. 

## Menjanje sajta

Postoji više pristupa rada na nekom sajtu preko FTP-a. Navešću vam tu par najčešćih.

### Direktan rad na serveru

Jedna opcija je da radite direktno na fajlovima koji su na serveru. Ovo se treba izbegavati ako je sajt trenutno aktivan
odnosno posećivan, jer možete veoma lako napraviti problem vlasniku i korisnicima sajta. Nažalost, ponekad ni nemate
drugu opciju, pogotovo ako sajt radi sa bazom podataka za koju nemate pristup, ili je nepraktično preuzeti ceo sadržaj.

### Lokalni rad na kopiji

U idealnoj situaciji vi ćete moći imati lokalnu kopiju sajta, pogotovo ako ga radite od nule, na kojoj ćete moći menjati
šta god je potrebno. U ovoj situaciji, kada završite određenu turu rada, vi sve menjane fajlove pošaljete gore na server.

#### DISCLAMER

Iako bih svakom preporučio da nauče druge tehnike rada na sajtovima, ponekad je FTP jedina opcija. Sem toga, smatram da 
je kontraproduktivno učiti početnike kako da koriste SSH, SVN, CI i druge modernije tehnike. Vremenom će se bolje
tehnike moći naučiti i primenjivati.