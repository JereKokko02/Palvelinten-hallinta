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
