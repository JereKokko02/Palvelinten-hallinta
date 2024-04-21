#a) Hello SLS! Tee Hei maailma -tila kirjoittamalla se tekstitiedostoon.

Tässä tehtävässä on tarkoitus luoda Salt-tilafunktio jolla saa tuotettua "Hei maailma!" viestin. Tämän tehtävän tarkoitus on siis varmistaa että osataan tehdä tilafunktioita saltissa.

Tein tämän tehtävän ensin luomalla 


#b) Top. Tee top.sls niin, että useita valitsemiasi tiloja ajetaan automaattisesti

Tässä tehtävässä loin aluksi uuden hakemiston /srv/salt/ jonne loin nanolla uuden top.sls tiedoston. Tähän tiedostoon kirjoitetaan useampia saltti tiloja joita haluan ajaa kerralla valituilla koneilla. Tein seuraavat konfiguraatiot /srv/salt/top.sls tiedostoon:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/a239f3d0-c427-4d5e-a212-7734df435bba)

Kyseisessä konffissa saltti siis lukee tuon top.sls tiedoston ja katsoo sen sisällöstä tarvittavat tehtävät. Tässä tapauksessa se siis katsoo mille minion koneille tuo top.sls ajateaan ja minkä tiedoston perusteella (testi1).

Seuraavaksi piti luodo tuo kyseinen tiedosto jota saltti alkaa etsimään. Tein sen vastaavanlaiseksi:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/9acf1f57-e1d6-4c3f-890b-7bcff09c5abd)

Ja näin saltti asensi valitut paketit minion koneelle kun ajettiin komento "sudo salt '*' state.apply"

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/33189bd5-b913-4ad9-bfdf-d303da4b16ab)


#c( 

Tein manuaalisen asennuksen ihan vain seuraamalla Ubuntu.comin ohjeita (lähde 4) ja korvasin /var/www/html -hakemiston index.html tiedoston haluamakseni:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/f9bbf7cd-d0a2-424e-98c2-fe5927e06243)

Indeksi -sivun vaihdon testasin host-os:n kautta kirjoittamalla virtuaalikoneen ip-osoitteen hakukenttään (edel.kuva).


TÄHÄN init sls apache2!!!!

init sls /srv/salt/init.sls
![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/27e1e76c-bc91-4364-aca3-088d35e8b2bc)


Init ajo
![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/ede99b3b-99b2-48a4-8bc2-9cb9027f8258)


+ miksi ei onnistunut


# Lähteet

4 https://ubuntu.com/tutorials/install-and-configure-apache#3-creating-your-own-website
