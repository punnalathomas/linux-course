kolmas tehtävä:  
pitäisi katsoa uudelleen käynnistyksen yhteydessä käynnistyykö apache automaattisesti sudo systemctl is-enabled apache2  
documentRoot on se mistä apache tietää että siellä on se varsinainen kontentti  
sites-available kaikki  
sites-enable on ne mitkä on käytössä  
enable kansiossa olevat tiedostot ovat linkki available tiedostossa oleviin tietoihin  
kaikki omat sivut tehdään käyttäjän kotihakemistoon, eli ei tarvita sudo komentoa muokkaukseen  
sudo journalctl näyttää apache tason logit  


usean webbisivun ajaminen saman ip:n alla:  
/etc/hosts fileen täytyy käydä laittamassa webbisivu esim 127.0.0.1 site2.com  
näin saadaan kerrottua nimipalvelulle, että minkä ip:n takaa löytyy webbisivu kirjoitettuna selkokielisenä  

update: 6.9.2025  
# Tietokone ja käyttöjärjestelmä
**GPU:** Nvidia RTX 2070  
**Processor:** Intel Core i9-9900K 3.60 Ghz    
**RAM:** 16.0 GB  
**OS:**  Windows 11 Home  

# Hello Web Server

## Tiivistelmä
**6.9.25**  
**Aloitusaika**: 16:48  
**Lopetusaika**:   
  
Tämän harjoituksen tavoitteet löytyvät Tero Karvisen Linux Palvelimet 2025 alkusyksyn web sivulta kohdasta h3 Hello Web Server (Karvinen 2025).  

## Name-based Virtual Hosts

Apache tukee useaa domain-nimeä yhden IP-osoitteen alla (Karvinen 2018). Tämä tapa säästää IP-osoitteita, koska useita eri host-nimiä voidaan palvella saman osoitteen alla. Tämä on toteutettu sisällyttämällä HTTP-otsakkeeseen hostname. (Apache)  
Apache Web Server asennetaan antamalla komento `sudo apt-get -y install apache2`, voimme myös muokata default web sitea esimerkiksi antamalla seuraava komento `echo "<tähän voi kirjoittaa mitä haluaa sivulla näkyvän>"|sudo tee /var/www/html/index.html`. Saadaksemme uusi nimi-pohjainen virtuaalipalvelin toimintaan, on sille annettava määrityksiä. Luodaan aluksi uusi konfiguraatio tiedosto komennolla `sudoedit /etc/apache2/sites-available/pyora.example.com.conf` ja annetaan sille seuraavanlainen sisältö:
```
<VirtualHost *:80>
 ServerName pyora.example.com
 ServerAlias www.pyora.example.com
 DocumentRoot /home/xubuntu/publicsites/pyora.example.com
 <Directory /home/xubuntu/publicsites/pyora.example.com>
   Require all granted
 </Directory>
</VirtualHost>
```
Sivun osoitteeksi tulee siis pyora.example.com, jolla on myös www. alkuinen alias, eli vaihtoehtoinen nimi osoitteelle. DocumentRoot kertoo kansion, mistä sivuston tiedot löydetään. <Directory> antaa lukuoikeuden kaikille sivuston kansioon. (Karvinen 2018)  
Tämän jälkeen enabloidaan sivusto antamalla komento `sudo a2ensite pyora.example.com` ja uudelleen ladataan Apachen konfiguraatio tiedostot ilman palvelun uudelleen käynnistystä komennolla `sudo systemctl reload apache2` (Heinonen 2025).  
Tämän jälkeen voimme luoda uuden web-sivun normaalina käyttäjänä, käyttäjän kotihakemistoon, `mkdir -p /home/xubuntu/publicsites/pyora.example.com/` ja index.html tiedosto komennolla `echo pyora > /home/xubuntu/publicsites/pyora.example.com/index.html`. Web-sivu sisältäisi tällä hetkellä tiedon "pyora". Tämän jälkeen voimme testata sivua komentorivillä antamalla curl komennon `curl pyora.example.com`. Koska emme ole vielä vuokranneet nimeä palveluntarjoajalta, voimme simuloida nimipalvelua lokaalisti. Teemme sen muokkaamalla /etc/hosts tiedostoon IP-osoitteen joka vastaa pyora.example.com nimeä. (Karvinen 2018)  
On erittäin suositeltavaa määrittää Servername aina jokaiselle virtuaalipalvelimelle, muuten Apache joutuu käyttämään järjestelmän isäntänimeä (FQDN). Jos yksikään ServerName tai Alias ei vastaa pyyntöön, palvelin käyttää ensimmäistä konfiguraatiossa määritettyä virtuaalipalvelinta IP:lle ja portille. (Apache)  

## Tehtävät

Tehtävien tekeminen aloitetaan normaalisti avaamalla virtuaalikone, kirjautumalla sisään ja avaamalla Terminal-sovellus. Apachen weppipalvelin oli asennettu oppitunnilla, joten asennusta ei käydä tässä raportissa sen enempää läpi. Raporttia varten testaan kuitenkin onko Apache statuksen komennolla `sudo systemctl status apache2`, kuten voimme huomata Apache2 on päällä ja enabloitu. Voimme huomata lokiviesteistä varoituksen: Sep 06 15:55:05 debian apachectl[1073]: AH00558: apache2: Could not reliably determine the server's fully qualified domain na>, eli ServerNamea ei ole asetettu. En lähde korjaamaan asiaa tässä kohtaa. (Heinonen 2025)    

![kuva48](./Pictures/kuva48.png)  

Seuraavaksi testasin että weppipalvelin vastaa localhost-osoitteesta. Annoin komennon `curl localhost` ja komentoriville ilmestyi html muodossa oleva esimerkkisivusto. (Karvinen 2018)  

![kuva49](./Pictures/kuva49.png)  

Seuraavaksi oli tarkoitus etsiä ja analysoida lokeista rivit, jotka syntyvät kun omalta palvelimelta ladataan sivu. Heinosen ohjeista löysin komennon `sudo tail -f /var/log/apache2/access.log`. Komennon jälkeen loki-tekstit ilmestyivät komentoriville, käytin näppäimmistön ENTER näppäintä hyödyksi, jotta sain hieman tyhjää tilaa aikaisempien lokitekstien ja uuden kohta ilmestyvän tekstin väliin. Tämän jälkeen avasin uuden Terminal sovelluksen ja kirjoitin komennon `curl localhost`. Komennon jälkeen huomasin että alkuperäiseen lokitekstiin ilmestyi uusi log entry. (Heinonen 2025)  

![kuva50](./Pictures/kuva50.png)  

## lokin analyysi
Analyysiin on käytetty hyödyksi David Girvinin (2025) blogi-tekstiä "Understanding the Apache access log: how to view, locate, and analyze".  
::1 - - [06/Sep/2025:17:07:16 +0300] "GET / HTTP/1.1" 200 10981 "-" "curl/8.14.1"  

1. ::1 = IP-osoite joka teki pyynnön, eli tässä tilanteessa se on loopback-osoite, joka tarkoittaa pyynnön tulleen itseltään
2. [06/Sep/2025:17:07:16 +0300] = päivämäärä ja aika kun pyyntö tehtiin
3. GET = pyynnön metodi, eli resurssi haetaan
4. HTTP/1.1 = HTTP-protokollan versio. Tässä tilanteessa 1.1
5. 200 = HTTP status code. Tässä tilanteessa onnistunut vastaus (MDN 2025)
6. 10981 = palvelimen palauttaman vastauksen koko
7. "-" = mistä sivulta käyttäjä tuli. Tässä kohtaa ei ole mitään, koska pyyntö tuli curlilla
8. curl/8.14.1 = pyyntö tehtiin curl-työkalulla, jonka versio on 8.14.1



## Lähteet

Apache. Name-based Virtual Host Support. Luettavissa: https://httpd.apache.org/docs/2.4/vhosts/name-based.html. Luettu: 6.9.2025  

Girvin, D. 2025. Understanding the Apache access log: how to view, locate, and analyze. Sumo logic. Luettavissa: https://www.sumologic.com/blog/apache-access-log. Luettu: 6.9.2025  

Karvinen, T. 2025. Linux-palvelimet. Luettavissa: https://terokarvinen.com/linux-palvelimet/. Luettu: 6.9.2025  

Karvinen, T. 2018. Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address. Luettavissa: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/. Luettu: 6.9.2025  

MDN. 2025. HTTP response status codes. Luettavissa: https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status. Luettu: 6.9.2025  

Heinonen, J. 2025. linux-03092025.md. Luettavissa: https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-03092025.md. Luettu: 6.9.2025  








