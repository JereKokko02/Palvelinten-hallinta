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

''' Vagrant.configure("2") do |config|
	config.vm.synced_folder ".", "/vagrant", disabled: true
	config.vm.synced_folder "shared/", "/home/vagrant/shared", create: true
	config.vm.box = "debian/bullseye64"

	config.vm.define "t001" do |t001|
		t001.vm.hostname = "t001"
		t001.vm.network "private_network", ip: "192.168.88.101"
	end

	config.vm.define "t002", primary: true do |t002|
		t002.vm.hostname = "t002"
		t002.vm.network "private_network", ip: "192.168.88.102"
	end
end '''

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

Seuraavana oli salt-masterin ja salt-minionin asennus t001 ja t002 koneille. Tässä kohtaa sai valita kummasta koneesta tulee herra ja kummasta tulee orja. Koneesta 1 tuli herra ja koneesta 2 orja.


# c) Aja shell-komento orjalla saltin master-slave yhteyden yli.




