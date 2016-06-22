# Podešavanje radnog okruženja MacOS

Za pokretanje PHP-a na vašem lokalnom okruženju(tj. vašem računaru) trebaće vam web server. Postoji puno različitih
načina da se instalira web server na MacOS. Najjednostavniji način instalacije je da se iskoristi Mac-ov ugrađeni server
pomoću alata koji se zove Laravel Valet [https://laravel.com/docs/5.2/valet].


Da bi to instalirali potrebni su nam neki dodatni alati o kojima cemo kasnije razgovarati:

Otvorite Terminal koji se nalazi u: Appliations/Utilities/Terminal.app
(Prečica: CMD + SPACE i ukucajte Terminal)


Prvo ćemo instalirati Package manager za MacOs zvani BREW (Menadžer paketa/programa)

Prekopirajte sledeći text u vaš terminal i pritisnite enter (ukoliko zatraži vas password upišite ga)
```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```


Sledeće ćemo instalirati Package manager za PHP
```bash
curl -sS https://getcomposer.org/installer | php
```


Nakon toga pomerićemo fajl u poseban direktorijum, da bi ga mogli koristiti globalno (iz bilo koje lokacije na raćunaru)
```bash
sudo mv composer.phar /usr/local/bin/composer
```


Mac dolazi sa zastarelom verzijom PHP-a. Pa ćemo ga unaprediti pomoću prethodno instaliranog BREW-a

Prvo ćemo updejtovati BREW:
```bash
brew update
```

I onda instalirati najnoviji PHP
```bash
brew install homebrew/php/php70
```

Pošto smo osnovne programe instalirali, sad ćemo instalirati Valet. Valet je mini server manager za Mac. Pokrenite obe linije pojedinačno.
```bash
composer global require laravel/valet
```

```bash
export PATH=$PATH:~/.composer/vendor/bin
```


Vecina developera drži sve svoje projekte na jednom mestu. Pa ćemo i mi isto uraditi. U vašem user direktorijumu, napravićemo folder Projects i onda ćemo sve buduće projekte koje radimo da čuvamo u taj folder. (Primer: Projects/lekcija_1/...)

Sledeće komande pokrećite jednu po jednu liniju, te komande će ući u vas glavni direktorijum, kreirati direktorijum Projects i ući u njega.

```bash
cd
mkdir Projects
cd Projects
```

Da bi mogli da pristupim ovim direktorijumima preko browser-a, instaliraćemo Valet (upišite password kad ga zatraži instalacija)

```bash
valet install
```

Nakon uspešne instalacije, treba da damo Valet-u do znanja gde su nam projekti.

```bash
valet park
```


I instalacija je gotova. PHP je podešen i sad bi vam web server trebao raditi. Da bi testirali pokrenite slece komande:

```bash
mkdir proba

echo "<?php echo 'Yaay, ovo radi!'; ?>" > proba/index.php
```

Nakon toga, otvorite vas browser i stranicu: http://proba.dev

Trebalo bi da vidite samo text: Yaay, ovo radi!


## Program za rad

Dobar broj programera će vas religiozno ubeđivati da je njihov odabir programa najbolji.
Ja vas pozivam da isprobate vremenom više njih i vidite koji vam najviše leži.
Za potrebe ovog tutorijala ću vam dati i svoj predlog, a to je Sublime Text 3.
On je brz, modularan i radi na svim operativnim sistemima. Ja ga koristim za sve svoje potrebe programiranja,
kao i za pisanje ovog tutorijala. Na kraju dana, nije bitno kojeg odaberete, ali ako ste početnik,
predložiću vam ipak Sublime Text 3, jer ću vam vremenom dati i gomilu saveta/prečica za njega.
Jedina mana jeste da, ako ga koristite besplatno, dobijate povremeno popup podsetnik da ga kupite.
Ja sa njim radim već koju godinu sa namerom da ga kupim već, ali očigledno me ne ometa dovoljno u radu :)

Ako vam se već na prvu ruku ne bude svideo, još neki dobri besplatni izbori su Notepad++(samo Win) i Eclipse(sve platforme).
