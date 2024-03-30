x) 
- Saltin komentojen ajaminen paikallisessa verkossa. Miten asennetaan, kuinka testataan + mitä komentoja käytetään.
- Ohjeet Github tilin luomiseen, sekä reposetoryn tekemiseen. Ohjeet siis miten tehtävät palautetaan kurssilla.
- Raportin tekeminen sekä sen kriteerit. Raportointityypit, viittausohjeet + yleisiä pahoja mokia mitä ei saa missään nimessä tehdä.

## a)
- En osannut tässä vaiheessa ajaa mitään saltin komentoja windowsissa.
## b)
- Testasin asentumisen onnistumisen ajamalla Windowsin powershellissa komennon: vagrant --version. Tämä palautti vagrantin version (2.4.1).
## c)
- Tein vagrantilla uuden koneen ajamalla ensin powershellin kautta komennot: $ vagrant init debian/bullseye64 $ vagrant up $ vagrant ssh jotka sain suoraan tehtävien ohjeiden vinkeistä. Näillä komennoilla luotiin uusi vagrantfile jonka perusteella uusi virtuaalikone luodaan, luotiin itse virtuaalikone ja otettiin siihen yhteys ssh:n avulla. 

a) 
- asensin salt-minionin uudelle linux virtuaalikoneelle komennolla sudo apt-get install salt-minion ja katsoin komennolla whereis salt-minion sen asennussijainnin josta pääsin avaamaan nanolla sen.
b)
c)
