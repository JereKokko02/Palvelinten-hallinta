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

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/8b044cf4-c1cb-437d-9e50-f058eb22f3b1)

Windowssissa toimii paikallisesti "salt-call --local test.ping" eli saltti siis tosiaan toimii paikallisesti, mutta ei halua kommunikoida masterin kanssa





Tätä vielä vaikeuttaa se, että saltin sivuilla ja yleisestikin netissä on hyvin vähän tietoa windows minionin ongelmanratkaisusta/toiminnasta


























# Lähteet

1. https://terokarvinen.com/2018/control-windows-with-salt/
