Tunnin muistiinpanot:  


SSHN teko: ssh-keygen -> hyväksytään tallennus paikka -> ei passphrasee ja enter -> cd .ssh/ -> ls -> siellä on tiedosto -> catilla voi lukee, public ookoo näyttää salanen ei ikinä -> 
update: 6.9.2025  
# Tietokone ja käyttöjärjestelmä
**GPU:** Nvidia RTX 2070  
**Processor:** Intel Core i9-9900K 3.60 Ghz    
**RAM:** 16.0 GB  
**OS:**  Windows 11 Home  

# Hello World

## Tiivistelmä
**11.9.25**  
**Aloitusaika**:   
**Lopetusaika**:    
  
Tämän harjoituksen tavoitteet löytyvät Tero Karvisen Linux Palvelimet 2025 alkusyksyn web sivulta kohdasta h4 Maailma kuulee (Karvinen 2025). Olin tehnyt kaikki tarvittavat asennukset jo oppitunnin aikana. Avasin siis uuden serverin **UpCloudista**, jotta tässä raportissa olisi järkevä sisältö. Tämä raportti on kirjoitettu erityisesti itselleni voidakseni palata aiheen pariin, kun toimenpiteet eivät ole muistissa.  


## Pois pöytälaatikosta

**Pilvipalvelimen vuokraus ja asennus**:  
Pilvipalvelun vuokraamiseen on monia eri palveluntarjoajia. Jokainen, joka aikoo vuokrata tämänkaltaisen palvelun tuleekin harkita tarkkaan mihin käyttöön tarvitsee palvelua. Palvelua valittaessa on hyvä miettiä myös millaisella budjetilla haluaa tehdä toimintansa. Ilmaisia palveluita löytyy, mutta palvelun sisältö jää yleensä suppeaksi. (Lehto 2022)  

Pilvipalvelinta vuokrattaessa tarvitaan rekisteröityminen palveluun, sekä luotto- tai debitkortti maksuja varten. Rekisteröitymisen jälkeen voi käyttäjä aloittaa palvelimen asennuksen. Asennus on tehty yksinkertaiseksi ja käyttäjä pystyy vaikuttamaan esimerkiksi käytettävään käyttöjärjestelmään, tallenustilaan, palvelun sijaintiin, varmuuskopiointiin, sekä kirjautumis tapaan. (Lehto 2022)  

**Palvelin suojaan palomuurilla**:  
Yhteys palvelimeen tulee tehdä SSH-yhteyden avulla, joka on huomattavasti luotettavampi kuin TelNet-yhteys. Kun palvelimelle on päästy sisään ensimmäisen kerran tulee käyttäjän hakea päivitykset komennolla `sudo apt-get update`. Tämän jälkeen on hyvä asentaa palomuuri komennolla `sudo apt-get install ufw` ja tehdä "reikä" palomuuriin SSH-yhteydelle komennolla `sudo ufw allow 22/tcp`. Tämän jälkeen palomuuri voidaan laittaa päälle komennolla `sudo ufw enable`. (Lehto 2022)  

**Kotisivut palvelimelle**:  
Seuraavana vuorossa on käyttäjän lisääminen palvelimelle komennolla `sudo adduser [käyttäjä]`. Tämä antaa meidän käyttää palvelinta käyttäjänä, eikä roottina. Tämä lisää tietoturvaa, koska toimimme least privilidged periaatteella. Käyttäjä asetetaan sudo ryhmään, jolloin hän pystyy ajamaan komentoja sudolla.  (Lehto 2022)   

Käyttäjälle annetaan salasana, joka tulisi olla vaikea. Karvinen mainitsi tunnilla, että tähän salasanaan kohdistetaan todennäköisesti paljon bruteforce hyökkäystä, jolloin heikko salasana päästää hyökkääjän palvelimelle. (Karvinen 2025)  

Saadaksemme kotisivut toimimaan tulee asentaa Apache2-webbipalvelin, sekä avata palomuuriin portti 80 (http-yhteys). Apachen default-kotisivu on helppo muokata haluamakseen komennolla `echo Hello world! |sudo tee /var/www/html/index.html`. Kun käyttäjä haluaa tehdä oman kotisivun, olisi se paras tehdä käyttäjän omaan kotihakemistoon, jolloin sivua voidaan muokata ilman sudo-oikeutta. (Lehto 2022)  

**Palvelimen ohjelmien päivitys**:  
Palvelimen ohjelmien päivitykseen voidaan käyttää seuraavia komentoja:  
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
(Lehto 2022)  
Karvisen mukaan dist-upgradea ei tulisi keskeyttää, koska tämä saattaa hajottaa koneen.  

**First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS**:  
Vaikka Karvisen ohjeet ovat vuodelta 2017, ovat ne edelleen erittäin pätevät edellä mainittujen toimintojen tekemiseen. Karvinen (2017) mainitseekin root-käyttäjän sulkemisesta, tämä on hyvä tehdä tieturvallisista syistä. Kun root-käyttäjän kirjautuminen palvelimelle on suljettu, ei sitä voida käyttää haitallisiin tarkoituksiin. (Karvinen 2017)  

Edellä mainitujen toimintojen jälkeen, voidaan palvelinta alkaa käyttämään. Seuraava vaihe voisi olla Domain-nimen vuokraamisella, jolloin voidaan viitata esimerkiksi TeroKarvinen.comiin, eikä sen IP-osoitteeseen. (Karvinen 2017)  

## Tehtävät











## Lähteet

Karvinen, T. 2025. Linux Palvelimet 2025 alkusyksy. Luettavissa: https://terokarvinen.com/linux-palvelimet/. Luettu: 11.9.2025  

Karvinen, T. 2017. First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS. Luettavissa: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/. Luettu: 11.9.2025  

Lehto, S. 2022. Teoriasta käytäntöön pilvipalvelimen avulla (h4). Luettavissa: https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/. Luettu: 11.9.2025  

