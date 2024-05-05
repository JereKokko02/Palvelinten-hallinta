# x) Lue ja tiivistä

- Valitsin Tero Karvisen artikkelin "Control Windows with Salt" (Katso lähde 1)

- Artikkelissa opetetaan asentamaan ja käyttämään salttia windowsilla (minion).
- Ohjeet esim firefoxin ja steamin asennukseen windowsiin saltilla.
- Saltin käyttäminen paikallisesti windowsissa.
- Windows state jolla saa asennettua paljon eri ohjelmia.
- Lopussa ongelmanratkaisua.


# a) Saltti windowsille

Olin asentanut saltin windowsille jo aikaisemmin:
![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/95c496f2-aa76-4253-b830-fdd159a733db)


# b) Kerää koneesta tietoa grains.items moduulilla.

Tällä hetkellä olen jumissa tehtävässä, sillä minun windows-minion ei suostu työskentelemään master-koneen kanssa. Saltti on täysin oikein konffattu ja avaimien vaihto onnistui koneiden välillä mutta edes test.ping ei välity windows-minionille. Tämä on sangen eriskummallista sillä:

- Configi tehty oikein (varmistettu useaan otteeseen)
- oikeat portit ovat aukaistu (4505-4506)
- Avaimien vaihto onnistui
- toinen linux minioni toimii masterin kanssa
- windowskoneen manuaalinen pingaaminen onnistuu
- linuxin kello on kunnossa
- kaikki tarvittavat oikeudet on annettu saltille windowssilla
- minioni on vielä kerran asennettu puhtaasti uudelleen ja vanhat tiedot poistettu
- Asensin vielä Debian11/bullseyelle saman salt version manuaalisesti tätä ohjetta noudattaen: https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/debian.html#install-salt-on-debian-11-bullseye-amd64. Tämäkään ei ratkaissut ongelmaa.




## Master kone saa vain ilmoituksen että minioni ei palannut ajoissa, mikä ei suoraan kerro sitä, mikä siinä on vikana:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/8b044cf4-c1cb-437d-9e50-f058eb22f3b1)

Windowssissa toimii kuitenkin paikallisesti "salt-call --local test.ping" eli saltti siis tosiaan toimii paikallisesti, mutta ei halua kommunikoida masterin kanssa


## SALTTIA SUORITETAAN MINION-KONEESSA

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/630b8851-f993-4451-a51b-46070f34aa74)

## PORTIT 4505-4506 OVAT AUKI 

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/e2da4162-3874-45da-8119-9cd6ceb71c58)

## MINION KONEEN VIRHELOKI:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/8c8091ee-1ad6-42d0-9f01-643e653afb91)

## LOPPUYHTEENVETO

Olen yrittänyt ratkaista tätä tehtävää jo yli viikon ajan, mutta en ole silti saanut koneita tekemään yhteistyötä. Tämä tarkoittaa sitä, että en pysty tekemään tehtävä eteenpäin. Tämä johtuu joko omasta vähäisestä ymmärryksestä salttia kohtaan, inhimillisestä virheestä jota en ole huomannut. tai omalla windows-koneellani on yksi asetus tai väärä kirjain jossakin kohtaa sen tiedostoissa.

Minion lokissa esiintyviin virheilmoituksiin ei löydy netissä ainakaan omien hakutuloksien perusteella dokumentointia, eikä kukaan muukaan käyttäjä ole kohdannut samaa ongelmaa kuin minä. Ongelman ratkaisua vaikeuttaa vielä se, että netissä ei ole muutenkaan dokumentoitu saltin käyttö windowssissa yhtä perusteellisesti kuin linuxissa (en itsekään pidä windowssista niin ymmärrän tämän täysin). Joudun nyt siis toistaiseksi hyväksymään tappioni, mutta yritän vielä saada ratkaisun ongelmaani.




























# Lähteet

1. https://terokarvinen.com/2018/control-windows-with-salt/
