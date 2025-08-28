Tunnin 2 vinkit:  
man man = manuaali
komento --help = komennon avut  
kaks kertaa tabulator niin näkee mitä mahdollisia komentoja on  
tree = näyttää linuxin hakemistorakenteen  
etc on tärkeä hakemisto, löytyy paljon configuraatiofileja. etc vaatii ROOT oikeudet eli täytyy käyttää sudo komentoa.  
huom linuxissa jos poistat tai ylikirjoitat jotain, niin se on sitten tehty, eli ei ole palautusta niinkun Windowsissa. Eli tee mitä tiedät tekeväsi.  
.. menee pykälän eteenpäin hakemistossa  
cd = pääsee takas kotihakemistoon  
Editorit esim: nano, micro, 
uuden tiedoston luonti: nano uusi.txt  
touch testihakemisto/alihakemisto/(filename) = uusi tiedosto absoluuttista polkua käyttämällä  


update: 28.8.2025  
# Tietokone ja käyttöjärjestelmä
**GPU:** Nvidia RTX 2070  
**Processor:** Intel Core i9-9900K 3.60 Ghz    
**RAM:** 16.0 GB  
**OS:**  Windows 11 Home  

# Komentorivin käyttö

## Tiivistelmä
**28.8.25**  
**Aloitusaika**: 16:26  
**Lopetusaika**: 20:00   
 
Tämän harjoituksen tavoitteet löytyvät Tero Karvisen Linux Palvelimet 2025 alkusyksyn web sivulta kohdasta h2 Komentaja pingviini (Karvinen 2025).  

## Komennot  
Komentorivi on tosiaan kestänyt aikaa erittäin hyvin. Sitä käytettiin ennen Linuxin, Windowsin ja internetin aikaa ja sitä käytetään edelleen (Karvinen 2025). Komentorivi harjaantuneissa käsissä on erittäin nopeaa verrattuna esimerkiksi graafiseen käyttöliittymään. Komentorivi on myös kevyt raudalle, se ei vaadi suurta määrää tehoa pyöriäkseen. Tästä johtuen se on suosittu esimerkiksi servereiden käyttöön. Komentorivin avulla vaikeidenkin tehtävien tekeminen onnistuu muutamalla komennolla ja se on erittäin automaatio ystävällinen. (Walkme 2025)  

Tässä listattuna Linuxin komentorivin peruskomentoja (huom. $-merkki on normaali käyttäjäprompti ja sitä ei tarvitse kirjoittaa mukaan):  
`$ pwd` Näyttää tämän hetkisen työhakemiston  
`$ ls` Listaa tiedostot tämän hetkisessä hakemistossa  
`$ cd Desktop/` cd:n avulla voidaan liikkua hakemistossa, esim. mainittu komento siirtäisi käyttäjän työpöydän directoryyn  
`$ cd ..` tuplapisteellä voidaan siirtyä hakemistossa yhdenpykälän ylöspäin hakemistohierarkiassa  
Koin itse, että nämä komennot yhdistettynä `$ tree` -komentoon (näyttää hakemiston puumaisena rakenteena) ovat hyvä tapa opetella siirtymään hakemistossa. `$ tree` luo visuaalisen kartan, joka helpottaa navigointia ja rakenteen hahmottamista.  
`$ less` Tämä komento avaa tulosteen tai teksitiedoston helpommin selattavassa muodossa. Käyttäjä pystyy liikkumaan esimerkiksi helposti ylös ja alas lukiessaan tulostetta. `$ less` komennon jälkeen voimme käyttää `?` -merkkiä ja hakea jotain tiettyä patternia tekstistä. Kun haluamme poistua tästä lukutilasta painamme näppäimmistöllä `q` -merkkiä.  
Helpoin tapa palauttaa itseni kotihakemistoon oli komennolla `$ cd`, tätä voidaan käyttää hyödyksi tilanteessa, jossa käyttäjä eksyy hakemistoon ja haluaa aloittaa alusta.  
En luettele kaikkia opeteltuja peruskomentoja, mutta saadaksenne käsityksen mihin kaikkeen komentoriviä voi käyttää aion luetella muutaman esimerkin.  
Tiedostojen käsittely. Voimme luoda ja muokata tiedostoja editoreilla, kuten nano ja pico. Jos tiedostoa ei ole vielä olemassa, se luodaan editorin avauksen yhteydessä.  
SSH eli secure shell etäyhteys. Voidaan avata suojattu etäyhteys vaikkapa serveriin.  
Historian tarkasteluun.  
Tämänhetkinen suosikki ominaisuuteni on `tree`n lisäksi `Tab`:n eli tabulaattorin käyttö. Kun alkaa kirjoittamaan komentoa, tabulaattori näyttää mahdolliset vaihtoehdot kirjoitettujen kirjaimien perusteella. Jos vaihtoehtoja on vain yksi, kaksoispainallus täydentää komennon automaattisesti loppuun. Tämä on erityisen hyödyllinen, kun kirjoitetaan tiedostojen nimiä, sillä näin vältetään mahdolliset kirjoitusvirheet.  
Admin komennot. Kun halutaan antaa komentoja jotka vaikuttavat koko järjestelmään, täytyy antaa `$ sudo` -komento. Tämä etuliite antaa rajoittamattomat oikeudet. Tätä voidaan hyödyntää esimerkiksi ohjelmistojen asentamiseen ja poistamiseen. (Karvinen 2020) Heinosen mukaan jos joudutaan antamaan `sudo` -komento, tulisi miettiä tarkkaan mitä on tekemässä. Linux tekee juuri niinkuin sitä käsketään ja esimerkiksi poistettujen tiedostojen palautus muuttuu mahdottomaksi (27.8. Linux-palvelimet oppitunti).  


## Lähteet
Karvinen, T. 2025. Linux Palvelimet 2025 alkusyksy. Luettavissa: https://terokarvinen.com/linux-palvelimet/. Luettu: 28.8.2025  
WalkMeTeam. 2025. Graphical user interface (GUI) vs command line interface (CLI). Blogi-kirjoitus. Luettavissa: https://www.walkme.com/blog/graphical-user-interface-vs-command-line-interface/. Luettu: 28.8.2025
