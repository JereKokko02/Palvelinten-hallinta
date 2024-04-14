# x)
- Chacon and Straub 2014: https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F
  - Gitin manuaali
  - 1.3 osuudessa taas gitin toiminta, sen erot muista versiontallennus ohjelmista
  - 1.3 osuudessa käytännössä kerrotaan pähkinänkuoressa gitin toiminta havannoivilla kuvilla sekä niiden kuvauksilla.
 
- git add . && git commit; git pull && git push
  - git add: Oman ymmärrykseni mukaan tämä komento on ns "valmisteleva" tekijä ennen varsinaista lähetysvaihetta. Elikkä git add siis lisää haluttavat muutokset lähetysvalmiuteen.
  - && git commit: Tämä komento tallentaa aikaisemmat tiedostot. Tämä on siis vähän sama kuin virtual boxissa snapshotit.
  - git pull: Hakee muutokset repositorystä nykyiseen sessioon.
  - %% git push: Vie muutokset remote repositoryyn.

    Käytin tässä havainnollistavaa kuvaa (lähde 1)
 
- Varaston terokarvinen historia: https://github.com/terokarvinen/suolax/
  - Käyttäjän Tero Karvinen Suolax repo ja sen sisältö
  - mm salt -komentoja sekä valmiita salt stateja



 
# a) 

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/7574c624-360f-47d3-9fa7-c94e0c3db12e)

# b) 
Aluksi täytyy luoda uusi ssh-avain linuxin puolella komennolla "ssh-keygen" jonka jälkeen kopioida sen tuottama julkinen avain githubiin:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/ba199654-727e-437d-98d1-7933c2ff5765)

Äsken tuotettu avain liitettynä Githubiin (Summer-avain).

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/122bcc66-67e6-4b0d-a488-1d428d95ddf3)

Tämän jälkeen repon voi kloonata linuxin puolella hakemalla ensin repon oman ssh-avaimen ja ajamalla komennon "git clone + ssh-avain" 

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/8048806b-cae4-4278-a583-3ea0318fdaff)


![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/c29a44eb-ec16-4de1-9fa2-39c1e14dfa26)

Sisällön voi sitten tarkistaa siirtymällä repoon ja ajamalla ls komennon:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/a714a97c-4141-4c45-b793-b4c43fa5b5a7)

Itse muutoksen tekeminen komennolla "git add . && git commit; git pull && git push" :

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/c6511fc3-7c9e-4fd5-affd-3f558358091a)

Muutos näkyykin sitten oikeassa repossa:

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/bc38f0ce-1034-4d18-a40b-62f9030b7799)

# c)
 Voi ei! Olen mennyt luomaan väärän tiedoston summer repoon ja vielä lähettänyt sen eteenpäin. Nyt menetän miljoonaideani ja salaisen sivubisnekseni nimeämättömän afrikkalaisen valtion kanssa. Voinko tehdä mitään tämän estämiseksi?
 
 ![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/eba1522e-6aca-4198-9471-bfe318f27dfc)

 ![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/70e4ce12-25f2-4cbc-b6eb-fdc35c919049)

Mutta hahaa! Muistinkin että olin ladannut aikaisemman version jo githubiin ja voin palata siihen komennolla "git reset --hard" joka tuhoaa nykyiset muutokset. Nyt minun ei tarvitse huolehtia miljoonaideastani eikä perua afrikan lentoa!

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/4f2a8a15-df22-4583-8c71-f83d450681ef)

# d) 

Git log komennolla saa vastaavat tiedot: 

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/751c74e4-c44d-4049-88c5-e950b56edd0c)

jossa:

date tarkoittaa sitä, milloin muutokset on puskettu läpi (commit)
author tarkoittaa muutoksen tekijää
commit on taas ajettujen muutosten tieto muutettuna siten, että github ymmärtää sen??

# e) 

Tässä tehtävässä minulla oli ongelmana se, että olin tehnyt git tehtävät salt-master koneella, eli en pystynyt ajamaan --local komentoja. Pystyin kuitenkin ajamaan summer reposta komentoja minionille vaikka sitä ei tehtävässä haetukkaan.

![image](https://github.com/JereKokko02/Palvelinten-hallinta/assets/165003744/a31b8e57-1377-4a1b-845e-226ecb9ed809)


 

# Lähteet
1. https://www.google.com/url?sa=i&url=https%3A%2F%2Fmedium.com%2F%40nmpegetis%2Fgit-how-to-start-code-changes-commit-and-push-changes-when-working-in-a-team-dbc6da3cd34c&psig=AOvVaw0s6trlTsSLETob41KZhVjK&ust=1713211629944000&source=images&cd=vfe&opi=89978449&ved=0CBIQjRxqFwoTCNDu4-LAwoUDFQAAAAAdAAAAABAE
   









