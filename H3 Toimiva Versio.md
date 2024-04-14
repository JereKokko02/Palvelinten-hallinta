# x)
- Chacon and Straub 2014:
  - Gitin manuaali
  - 1.3 osuudessa taas gitin toiminta, sen erot muista versiontallennus ohjelmista
  - 1.3 osuudessa käytännössä kerrotaan pähkinänkuoressa gitin toiminta havannoivilla kuvilla sekä niiden kuvauksilla.
 
- git add . && git commit; git pull && git push
  - git add: Oman ymmärrykseni mukaan tämä komento on ns "valmisteleva" tekijä ennen varsinaista lähetysvaihetta. Elikkä git add siis lisää haluttavat muutokset lähetysvalmiuteen.
  - && git commit: Tämä komento tallentaa aikaisemmat tiedostot. Tämä on siis vähän sama kuin virtual boxissa snapshotit.
  - git pull: Hakee muutokset repositorystä nykyiseen sessioon.
  - %% git push: En ymmärrä.
 
# a) 

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/7574c624-360f-47d3-9fa7-c94e0c3db12e)

# b) 
Aluksi täytyy luoda uusi ssh-avain linuxin puolella komennolla "ssh-keygen" jonka jälkeen kopioida sen tuottama julkinen avain githubiin:
![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/ba199654-727e-437d-98d1-7933c2ff5765)
![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/122bcc66-67e6-4b0d-a488-1d428d95ddf3)

Tämän jälkeen repon voi kloonata linuxin puolella hakemalla ensin repon oman ssh-avaimen ja ajamalla komennon "git clone + ssh-avain" 




