# x) Lue ja tiivistä (lähde 1)

- Windows package manager: mikä se on?
- Saltin oma package manager josta saltti pystyy asentamaan haluttuja ohjelmia windows-minionille.
- Käytännössä samanlainen repository kuin linuxin apt -varasto.
- Ohjeet package managerin käyttöön ja asennukseen / päivittämiseen.
- ohjeet miten winrepo yhdistetään masteriin tai minioniin githubista.
- komentoja winrepon käyttöön.


# a) dsdsdsds


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








d

2 ![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/cb459189-b4d4-4818-8fdb-43f3687cd8c4)

1 ![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/2aae8d9f-c3a1-4264-a9a0-d51030558f6e)
































Lähteet

1. https://docs.saltproject.io/en/latest/topics/windows/windows-package-manager.html
