# x) Lue ja tiivistä (lähde 1)

- Windows package manager: mikä se on?
- Saltin oma package manager josta saltti pystyy asentamaan haluttuja ohjelmia windows-minionille.
- Käytännössä samanlainen repository kuin linuxin apt -varasto.
- Ohjeet package managerin käyttöön ja asennukseen / päivittämiseen.
- ohjeet miten winrepo yhdistetään masteriin tai minioniin githubista.
- komentoja winrepon käyttöön.


# a) //Tällä hetkellä windowsin kanssa ongelmaa, jos saan ratkaistua ongelman päivitän tämän viestin ennen tiistaita 7.5//





# b) Benchmark

## 1. https://github.com/arnisoph/salt-modules

Tämä on yksityisen henkilön luoma github sivu, jossa hän on luonut muutaman salt-moduulin joita hänen mukaansa voi käyttää esimerkiksi tavallisessa työelämässä.

- Tarkoitus: 
Hakee tietoa salt-minionin järjestelmän ajasta sekä tallennustilan käytöstä.

- Lisenssi:
Apache 2.0, eli työtä saa muokata, jakaa, käyttää ja käyttää osana muita töitä ilman että näissä tuotoksissa käytetään myös Apache 2.0 lisenssiä.

- Tekijä ja vuosi:
Arnold Bechtoldt, viimeisin muokkaus: Dec 18, 2015 

- Riippuvuudet:
Saltti pitää olla asennettuna masterille ja minionille. Myös saltin versio saattaa vaikuttaa toimivuuteen.



## 2. https://perfecto25.medium.com/using-saltstack-for-emergency-sudoers-access-tempsudo-d5417e528e4d + github koodit https://gist.github.com/perfecto25/f7a682cb5dca17bdd9c0bd5aa6394bd1

Tämä on yhden nimeättömän yrityksen työntekijän luoma ja käyttämä salt-moduuli joka mahdollistaa sudo-oikeuksien antamisen tietyille käyttäjille. Kyseinen yritys käyttää tätä varsinkin sellaisissa tapauksissa joissa yrityksen normaali järjestelmäasiantuntija ei ole paikalla tai on lomalla ja yrityksellä on tarvetta päästä muokkaamaan palvelinten tiloja tai tarvitsevat sudo-oikeudet hätätapauksien vuoksi.

- Tarkoitus:
  Antaa valikoiduille käyttäjille sudo-oikeudet, tallentaa niiden käytöstä lokitiedot, sekä antaa lokitapahtumista sähköposti-ilmoitukset halutuille henkilöille.

- Lisenssi:
  Valitettavasti moduulin verkkosivuilla tai githubissa ei lue tietoa lisenssistä. Sivustolla tekijä kuitenkin antaa lukijoiden käyttää koodia hyväkseen.

- Tekijä ja vuosi
  Mike R, 8.11.2018
  
- Riippuvuudet:
  Ainakin ohje on tehty linux-ympäristössä, eli riippuvuutena on linux kondeiden käyttö, sekä saltin asennus näille koneille.


## 3. https://tuomasvalkamo.com/how-to-create-your-own-salt-module/ + github https://github.com/tuomasvalkamo/starter-module

Tämä on yhden aikaisemman kurssin opiskelijan tekemä oman moduulin lopputyö.

- Tarkoitus:
  Asentaa muutamia aloitusohjelmia minionille. mm openssh, netcat, micro jne. Samalla tässä on ohjeet ensimmäisen salt-moduulin luomiseen.

- Lisenssi: 
GNU General Public License v3.0. Työtä saa jakaa ja käyttää kunhan sitä ei muokkaa itse.

- Tekijä ja vuosi:
Tuomas Valkamo, 13.12.2022

- Riippuvuudet:
Linux-ympäristö, tehty vagrantilla.








# c)

- Testasin moduulin nr.3 toimivuutta seuraamalla sen github repositoryn "readME" ohjetta. Valitsin tämän moduulin siksi, että se vaikutti minusta kiinnostavalta ja simppeliltä. Aloittamalla simppelillä moduulilla saan myös itse ymmärrettyä sen toimintaa paremmin. Valintaan vaikutti myös sen kotisivujen kattavuus, sille sivujen ohje on hyvin kattava ja sitä oli helppo seurata.


Testaaminen oli simppeliä, sillä ajoin komennon: "git clone https://github.com/tuomasvalkamo/starter-module" sijaintiin /srv/salt.

Tämän jälkeen ajoin moduulin paikallisesti komennolla "sudo salt-call --local state.apply starter-module". Kuten seuraavasta kuvasta voi huomata, vain moduulin ensimmäinen "pkg.installed ufw" ajettiin osittain. Koko moduuli ei siis toiminut ainakaan omalla virtuaalikoneellani.

 ![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/cb459189-b4d4-4818-8fdb-43f3687cd8c4)


Ratkaisu tähän olikin aika simppeli. Kun saltti jäi jumiin tuohon ufw kohtaan niin kirjoitin vahingossa komennon "exit" ilman moduulin ajon pysäytystä. Tämä jostain syystä sai jatkettua moduulin suoritusta ja se ajoi itsensä loppuun saakka:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/101ddc86-abab-4d2c-b0ad-9a27aa190192)

Moduuli siis toimii ja se asentaa halutut ohjelmat/paketit.

Mielestäni tämä moduuli on todella hyvä ensimmäinen moduuli, sillä siitä on hyötyä käyttäjälle. Moduuli nimittäin voidaan ajaa uudelle virtuaalikone minionille joka nopeuttaa aina sen konfigurointia. Tässä moduulissa on myös tehty askelta vaikeampaa, eli muutettu ufw asetuksia ja saatu ne toimimaan kaikilla koneilla joissa tila voidaan ajaa.


# d) Viisi omaa ideaa modulille: //päivitetty 7.5 tunnilla//

1. Moduli joka asentaa haluttuja paketteja uudelle koneelle.
2. Moduli joka palauttaa tietoja masterille minion koneesta (esim ip, os, valmistaja jne).
3. Moduli joka luo jotakin uutta ja muokkaa sitä (esim apachen konfigurointi ja sille verkkosivun luonti).
4. Moduli joka poistaa kaikkien minionien avaimet.
5. Moduli joka tuhoaa kaikki minion-koneet ja poistaa ne.
6. Moduli joka muuttaa ufw -asetuksia minion koneissa
## --------------------KOMMENTIT---------------------------------
3. Esimerkiksi apachen verkkosivun luominen jokaiseen minion koneeseen, sen oletussivun korvaaminen sekä sen lisäksi siihen jonkin muun toiminnon lisääminen, esimerkiksi sen suojaaminen. -- pkg.installed, file.managed

6. Moduuli voi esimerkiksi ajaa komennon -- rm-rf mutta siitä pitää lukea enemmän, sillä siihen liittyy joitakin sääntöjä eri linux distroissa (debian tässä tapauksessa)

2. Tämän lisäksi voi etsiä jotain muuta kuten mac-osoitteen ja käyttäjien määrän.
























Lähteet

1. https://docs.saltproject.io/en/latest/topics/windows/windows-package-manager.html
