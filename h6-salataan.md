muistiinpanot:  
set group id = g+s  
1. asennetaan certbot opettajan komennolla
2. reikä 443/tcp
3. sudo certbot --apache --domains thomaspunnala.com,www.thomaspunnala.com
4. enter skip
5. yes
6. alidomaineille omat ajot
7. sisennykset kuntoon .conf tiedostoista
8. 


update: 28.9.2025  

# Lokaali tietokone ja käyttöjärjestelmä
**GPU:** Nvidia RTX 2070  
**Processor:** Intel Core i9-9900K 3.60 Ghz    
**RAM:** 16.0 GB  
**OS:**  Windows 11 Home  

# Virtuaali palvelin
**Template:** Debian GNU/Linux 13 (Trixie)  
**CPU:** 1 core  
**RAM:** 1 GB  
**Storage:** 10 GB  
**Service provider:** UpCloud  

# Salataan

## Tiivistelmä
**28.9.25**  
**Aloitusaika**:    
**Lopetusaika**:      

Tämän harjoituksen tavoitteet löytyvät Tero Karvisen Linux Palvelimet 2025 alkusyksyn web sivulta kohdasta h6 Salataampa (Karvinen 2025).

## Lets Encrypt
Voidaksemme hankkia automaattisesti selaimen luottamia varmenteita tarvitsee meidän esimerkiksi ajaa ACME-asiakasohjelmaa verkkopalvelimella. Yksinkertaisimmillaan ACME-asiakas todistaa varmentajalle (certificate authority), että verkkotunnusta hallitsee asiakkaan verkkopalvelin. (Lets Encrypt 2025)  

Lets Encrypt tunnistaa ACME-asiakasohjelman sen julkisenavaimen perusteella. Ensimmäisellä yhteydenotolla luodaan avainpari ja todistetaan Lets Encryptin CA:lle, että asiakas hallitsee kyseistä verkkotunnusta. Käytännössä asiakas kysyy kuinka voin todistaa olevani kuka sanon ja Lets Encrypt antaa haasteita joista asiakkaan tulee selvitä. Kun tarkistukset onnistuvat, asiakas saa oikeuden hallita varmenteita kyseiselle verkkotunnukselle. (Lets Encrypt 2025)  

Asiakkaan valtuutuksen jälkeen asiakas voi pyytää, uusia ja peruuttaa varmenteita. (Lets Encrypt 2025)  

## The Apache Software Foundation
Tässä tehtävässä käytämme Certbottia tekemään salaukseen liittyvät asetukset. Apache tarvitsee kuitenkin vähintään seuraavan SSL-asetusten osion:  
```
LoadModule ssl_module modules/mod_ssl.so
Listen 443
<VirtualHost *:443>
    ServerName www.example.com
    SSLEngine on
    SSLCertificateFile "/path/to/www.example.com.cert"
    SSLCertificateKeyFile "/path/to/www.example.com.key"
</VirtualHost>
```
Tällä aktivoidaan SSL:n kuuntelemaan porttia 443 ja määritetään sertifikaatin ja avaimen tieodostot. (Apache 2025)  

## Tehtävät

### TLS-sertifikaatti
Tämän osion lähteenä on käytetty Karvisen (2025) oppitunnin ohjeistusta. Alotin tehtävän tekemisen käynnistämällä lokaalin linux koneen, tämän jälkeen otin yhteyden SSH:lla pilvessä olevaan palvelimeeni.  

Aluksi käynnistin uudelleen apachen komennolla `sudo systemctl restart apache2` ja tarkistin että verkkosivu toimii. Avasin thomaspunnala.com sivun ja totesin että toimii hyvin.  

Seuraavaksi avataan tulimuuriin reikä HTTPS-yhteydelle. Annetaan komento `sudo ufw allow 443/tcp` ja tarkistetaan komennolla `sudo ufw status verbose`, että asetus toimii.  

![kuva101](./Pictures/kuva101.png)  





## Lähteet
Apache. 2025. SSL/TLS Strong Encryption: How-To. Luettavissa: https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample. Luettu: 28.9.2025  

Karvinen, T. 2025. Linux Palvelimet 2025 alkusyksy. Luettavissa: https://terokarvinen.com/linux-palvelimet/#h6-salataampa. Luettu: 28.9.2025  
Lets Encrypt. 2025. How It Works. luettavissa: https://letsencrypt.org/how-it-works/. Luettu: 28.9.2025  


