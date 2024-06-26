# X) Lue ja tiivistä

### Karvinen 2021: Two machine virtual network with debian 11 bullseye and vagrant.
- Ohje kahden virtuaalikoneen luomiseen vagrantilla.
- Vagrantfilen muuttamiseen ohje.
- Ohjeet luotujen koneiden testaamiseen mm pingaamalla ja ssh:lla.
- Yleisiä ongelmia lopussa.

### Karvinen 2018: Salt quickstart - salt stack master and slave on ubuntu linux.
- Ohje saltin asennukseen (slave ja minion) ubuntu linuxissa.
- Millä komeinnoilla asennetaan salt-master ja salt-minion.
- Mitä tekee Saltissa master? ja mitä tekee saltissa minion?
- Miten testataan (cmd.run grains. jne).
- Lopussa listattuna komentoja joita master voi ajaa minionille.

### Karvinen 2014: Hello salt infra-as-code
- Infraa koodina salttia käyttäen.
- Moduulin luominen salttiin.
- Miten moduuli ajetaan? (sudo salt-call --local state.apply).
- Moduulin indempotenssi.
- Lopussa listattuna muutamia saltin state -funktioita.



# a) Asenna kaksi virtuaalikonetta samaan verkkoon.
Tein tämän tehtävän seuraten Tero Karvisen kirjoittamaa ohjetta (katso lähde 1) ja käyttäen omaa henkilökohtaista kannettavaa tietokonettani. Tehtävä suoritettiin käyttäen Vagrant -ohjelmaa kahden identtisen virtuaalikoneen luomiseen.

Tehtävä alkoi kahden melkein identtisen virtuaalikoneen luomisella vagrantfileä muokaten. Loin kyseisen vagrant tiedoston sijaintiin C:\users\käyttäjä\palvelimet cmd komennolla vagrant init debian/bullseye64. 

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/3b5368c3-7493-47a0-8a95-a14c8164d58d)

Tämän jälkeen avasin vagrantfilen muistiolla ja muutin sen sisällön vastaavasti:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/9016badf-224c-4352-9862-9ab0c929e574)

Tällä muutoksella vagrant siis luo kaksi identtistä linux-konetta joilla on kuitenkin eri nimet, (t001, t002) sekä eri IP-osoitteet (192.168.88.101, 192.168.88.102). Koneiden luomisen jälkeen käynnistin ne cmd komennolla "vagrant up" ja pystyin aloittamaan niiden testaamisen.

Testaaminen tapahtui aluksi ottamalla ssh yhteys molempiin koneisiin. Tämä tapahtui vuorotellen komennoilla "vagrant ssh t001", ja "vagrant ssh t002".

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/19a5e509-f692-4d73-88c4-73f132c3259d)

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/6df3ab22-a923-46f8-9896-4cb8577f1d7f)

Tämän jälkeen testauksen viimeisenä vaiheena oli enää koneiden pingaaminen ristikkäin.

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/fc2b4543-31dc-442e-acc9-8aff979cbc51)

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/486ae418-c7e0-470e-826a-9e1f2e9f7101)

//Pro dippi hippi tippi: Linuxissa ping -komennon hyppyjen määrää rajoitetaan parametrillä "-c" + hyppyjen määrä numerona. //

Testauksen lopputuloksena se, että koneet ovat olemassa ja ne voivat löytää toisensa verkossa.



# b) Asenna saltin herra-orja -arkkitehtuuri toimimaan verkon yli.

Seuraavana oli salt-masterin ja salt-minionin asennus t001 ja t002 koneille. Tässä kohtaa sai valita kummasta koneesta tulee herra ja kummasta tulee orja. Koneesta 1 tuli herra ja koneesta 2 orja. Tehtävä tehtiin noudatten Teron toista ohjetta (Katso lähde 2).

Tehtävässä yksinkertaisesti asensin salt-masterin koneelle t001 komennolla "sudo apt-get install salt-master" ja salt-minionin koneelle t002 komennolla "sudo apt-get install salt-minion. Tämän jälkeen testasin asentumisen molemmilla koneilla komennolla salt-master --version ja salt-minion --version.

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/745bbe6a-e371-4ce0-b294-81944b0b9d0c)

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/785f1bc2-e65b-413e-8544-debec74f993f)

Tämän jälkeen piti saada t002 kone lähettämään tieto sen olemassaolosta salt-master koneelle t001. Tämä tapahtui muokkaamalla t002 koneen "minion" tiedostoa komennolla "sudoedit /etc/salt/minion" ja asettamalla kohtaan "Master" master-koneen ip-osoite:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/d104b1e4-8cc1-438b-aadc-32d87cf97384)

Tämän jälkeen käynnistin sekä master, että minion koneet uudelleen ja etenin viimeiseen osaan: Avainten varmennukseen

Avainten varmennus oli erittäin simppeliä, sillä se tehtiin ajamalla komento "sudo salt-key -A" master-koneella, jolloin saltti kysyi masterkoneelta haluaako tämä hyväksyä t002 koneen lähettämän avaimen. Painoin nappeja Y ja ENTER jolloin master-kone hyväksyi avaimen.

//Onnistuin kadottamaan kuvankaappauksen tapahtumasta//

Nyt Minion-kone oli linkitetty Master-koneeseen ja master-koneella pystyi ajamaan komentoja Minion-koneella.



# c) Aja shell-komento orjalla saltin master-slave yhteyden yli.

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/055041a0-8ec5-4dab-9cb2-40f907a0c36f)



# d) Aja useita idempotentteja (state.single) komentoja master-slave yhteyden yli.

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/8c60ae4c-6ac1-4df8-a067-544748886574)

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/e2d8443b-7874-4ed5-9ae8-3c1253566fbb)

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/453c2231-f106-4829-8d56-4b914acbdfd3)



# e) Kerää teknisiä tietoja orjista verkon yli (grains.item).

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/a0437588-345a-4612-873d-9597f923c42f)

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/e73c2d4c-a3b5-4565-883c-6d8b369ca787)

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/e2c9fa6a-a74a-4b15-b663-4912f8e94972)

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/d7483c26-1015-40a3-846c-449be00aed80)


// Jos ei tiedä/muista grains -moduulin nimeä niin komennolla: "sudo salt '*' grains.ls" saa listattua kaikki asennetut moduulit. //



# f) Tee infraa koodina kirjoittamalla /srv/salt/hello/init.sls.
Tässä tehtävässä oli tarkoituksena luoda yksi state-tiedosto joka pystytään ajamaan kaikilla salt-orjakoneilla. Tehtävä tehtiin noudatten Tero Karvisen ohjetta (katso lähde 3).

Ensimmäiseksi Master-koneelle pitää luoda tiedostosijainti johon state-tiedosto luodaan. Tämä tapahtui ajamalla master-koneella komento "sudo mkdir -p /srv/salt/ ja luomalla luotuun sijaintiin .sls tekstitiedosto komennolla "sudoedit /srv/salt/Hello.sls. Tekstitiedostoa muokattiin ohjeita noudattaen seuraavasti:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/53edfa9d-c96d-4c24-b5dc-72130f0e314d)

Tämän jälkeen luotiin itse hellotero.txt johon aikaisempi koodi viitta komennolla "sudoedit /srv/salt/hellotero.txt" ja sen sisältöön kirjoitettiin "see you at http://TeroKarvinen.com"

State-tiedoston ajaminen tapahtui komennolla sudo salt '*' state.apply hello:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/cb4cfffd-64ca-4fa0-8350-4e878413bd23)

Koodin onnistuminen testattiin etsimällä Minion-koneesta siihen juuri luotu tekstitiedosto:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/3988130c-9155-4713-875c-baa277b327cb)



# Lähteet
1. https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/
2. https://terokarvinen.com/2018/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/?fromSearch=salt%20quickstart%20salt%20stack%20master%20and%20slave%20on%20ubuntu%20linux
3. https://terokarvinen.com/2024/hello-salt-infra-as-code/




