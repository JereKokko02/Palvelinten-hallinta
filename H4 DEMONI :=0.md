#x) 

Karvinen 2023: Salt Vagrant - automatically provision one master and two slaves (Katso lähde 1)

- Infraa koodina
- mikä on top.sls ja mitä statet ovat yleensäkin
- vagrantin tuhoaminen
- esimerkkejä eri saltti tiloista (top.sls init.sls)


Salt contributors: Salt overview (katso lähde 2)

- Yaml-kielen käyttöohjeet
- listojen ja directoryjen teko yaml-kielellä


Karvinen 2018: Pkg-File-Service – Control Daemons with Salt – Change SSH Server Port (katso lähde 3)

- ssh-tilafunktio saltille
- Kyseisellä tilafunktiolla muutetaan ssh serverin käyttämää porttia
- Ohjeet aina tilafunktion luomisesta sen sisältöön
- lopussa ohjeet testaukseen








#a) Hello SLS! Tee Hei maailma -tila kirjoittamalla se tekstitiedostoon

Tätä en saanut toimimaan vaikka yritin, sillä saan ajettua vaikka mitä muita tiloja, mutta en saa ajettua tilaa jolla minion-kone printtaa hello world tekstin. Otan mielelläni ohjeet vastaan jos arvioija on tämän hiffannut!


#b) Top. Tee top.sls niin, että useita valitsemiasi tiloja ajetaan automaattisesti

Tässä tehtävässä loin aluksi uuden hakemiston /srv/salt/ jonne loin nanolla uuden top.sls tiedoston. Tähän tiedostoon kirjoitetaan useampia saltti-tiloja joita haluan ajaa kerralla valituilla koneilla. Tein seuraavat konfiguraatiot /srv/salt/top.sls tiedostoon:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/a239f3d0-c427-4d5e-a212-7734df435bba)

Kyseisessä konffissa saltti siis lukee tuon top.sls tiedoston ja katsoo sen sisällöstä tarvittavat tehtävät. Tässä tapauksessa se siis katsoo mille minion koneille tuo top.sls ajateaan ja minkä tiedoston perusteella (testi1).

Seuraavaksi piti luodo tuo kyseinen tiedosto jota saltti alkaa etsimään. Loin sen samaan hakemistoon vastaavanlaiseksi:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/9acf1f57-e1d6-4c3f-890b-7bcff09c5abd)

Ja näin saltti asensi valitut paketit minion koneelle kun ajettiin komento "sudo salt '*' state.apply"

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/33189bd5-b913-4ad9-bfdf-d303da4b16ab)


#c) 

Tein manuaalisen asennuksen ihan vain seuraamalla Ubuntu.comin ohjeita (katso lähde 4) ja korvasin /var/www/html -hakemiston index.html tiedoston haluamakseni:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/f9bbf7cd-d0a2-424e-98c2-fe5927e06243)

Indeksi -sivun vaihdon testasin host-os:n kautta kirjoittamalla virtuaalikoneen ip-osoitteen hakukenttään (edel.kuva) jolloin apache:n defaultti sivu korvaantui omalla sivullani.


En saanut tehtyä apachen automaattista asennusta siten, että saltti-tilafunktio myös vaihtaisi index.html tiedoston. Tein siis tässä kohtaa vain tilafunktion joka asentaa apachen minion-koneelle. 

Aluksi loin master-koneelle uuden tilafunktion kohteeseen /srv/salt/init.sls johon kirjoitin vastaavat komennot:
![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/27e1e76c-bc91-4364-aca3-088d35e8b2bc)

Tämän jälkeen ajoin kyseisen tilan aivan normaalisti komennolla "sudo salt '*' state.apply init":

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/ede99b3b-99b2-48a4-8bc2-9cb9027f8258)

Saltti asensi apachen onnostuneesti minion-koneelle.


#d) SSHouto. Lisää uusi portti, jossa SSHd kuuntelee.

Tein tämän tehtävän noudatten Tero Karvisen ohjetta (katso lähde 3).

Aluksi loin uuden sshd.sls tilafunktion kohteeseen /srv/salt/ ja kirjoitin sinne vastaavat tiedot:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/bd2750b4-5a68-40ba-bff2-d747079d9664)

Tämän jälkeen loin samaan sijaintiin tiedoston sshd_config johon aikaisempi tila viittaa ja tein vastaavat muutokset:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/d5ab5af8-722b-4004-921a-de34cfb294e5)

Tämän jälkeen ajoin tilan komennolla "sudo salt '*' state.apply sshd"

Koko litania ei millään mahdu järkevästi githubiin mutta käytännössä tästä kuvankaappauksesta näkyy että tilan ajo onnistui:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/20913923-8ea0-4930-a96c-16030ba73312)

Ssh:lla saa nyt otettua yhteyden minioniin:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/f2ee75e1-542a-4220-9c48-fcc65e982cb3)









# Lähteet
1. https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file
2. https://docs.saltproject.io/salt/user-guide/en/latest/topics/overview.html#rules-of-yaml
3. https://terokarvinen.com/2018/04/03/pkg-file-service-control-daemons-with-salt-change-ssh-server-port/?fromSearch=karvinen%20salt%20ssh
4. https://ubuntu.com/tutorials/install-and-configure-apache#3-creating-your-own-website
