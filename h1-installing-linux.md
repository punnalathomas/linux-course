vinkit: mikä debianfile sivulta?debian live 13.00 xfce.iso
virtual box extencion packkia ei välttis tarvita
domain name ihan sama
salasanat ei tarvi rootille
guided - use entire disk
all files in one partition
-1 /n
-2
-3
# otsikko
## otsikko 2
adada
### otsikko 3
sources list examples ?
bookworm sanat -> trixie
tämä on ensimmäinen rivi.  
tämä on toinen rivi.
# Tietokone ja käyttöjärjestelmä
**GPU:** Nvidia RTX 2070  
**Processor:** Intel Core i9-9900K 3.60 Ghz    
**RAM:** 16.0 GB  
**OS:**  Windows 11 Home  

# Raportin kirjoittaminen
Raporttien tarkoituksena on kertoa täsmällisesti mitä on tehnyt. Raportin täsmällisyyteen tulee kiinnittää erityistä huomioita, koska tarkoituksena on, että kuka tahansa muu pystyy toistamaan tehdyt toimenpiteet seuraamalla raporttia. Raporttin tekeminen on tärkeää myös tekijälle. Tämän raportin tekijä voi itse palata myöhemmin raportin pariin ja toistaa vaikeat ja tarkkuutta vaativat toimenpiteet nopeasti, omia muistiinpanojaan seuraten. (Karvinen, T. 2006)  
Hyvän raportin tulee myös olla helppolukuinen. Se tuo tekijästä ammattimaisen ja luotettavan kuvan. Raportointiin kuuluu myös täsmällisyys. Komennot juuri sellaisina kuin ne on tehty. Raporttiin on myös hyvä sisällyttää käytetty aika, päivämäärä ja kellonaika, jolloin voidaan esimerkiksi todeta onko jokin virhetilanne johtunut laajemmasta ongelmasta, johon raportintekijä ei ole voinut itse vaikuttaa.  
Raportti siis tulee tehdä huolellisesti ja täsmällisesti. On tärkeää sisällyttää kaikki onnistumiset ja epäonnistumiset, jolloin mahdollisien virheiden selvittäminen on helpompaa. Työhön on myös hyvä sisällyttää paljon kuvakaappauksia tekemisestään, koska kuva voi havainnollistaa tekovaiheen selkeämmin. Muista myös viitata lähteisiin. (Karvinen 2006)  
# Linuxin asennus virtuaalikoneeseen
## Tiivistelmä
**Aloitusaika**: 16:33  
**Lopetusaika**: 
## Kuvien lisääminen Markdowniin
Tutustuin aluksi Tero Karvisen tekemään ohjeeseen, joka löytyi repositorysta nimeltä **dreamhugmonkey**. Avasin README.md tiedoston ja tutkin **Preview**-, sekä **Code**-näkymää. Sain hyvän käsityksen, kuinka kuvan saa lisättyä tekstin sekaan Markdownissa (Karvinen, dreamhugmonkey). Tutkin myös Johanna Heinosen ohjetta: How to Install Linux to Virtualbox? Huomasin, että Heinonen oli laittanut kaikki kuvat **Pictures**-kansion alle, joten halusin käyttää samaa menetelmää (Heinonen 2025). Nopealla googlettamisella löysin kuinka lisätään kansio omaan repositoryyn.  
1. Avaa haluttu repository
2. Create new file
3. Kirjoita kansion nimi
4. Nimen perään lisää merkki "/"
5. Tämän jälkeen voit lisätä haluttuja tiedostoja kansioon  
(SethClydesdale 2019)  
Markdowniin kuva saadaan upotettua seuraavanlaisesti:
```
![Description](filename). 
```
Tämä on testikuva:  
![Screenshot of my own repository](./Pictures/testikuva.png)
## Virtualboxin asennus
Aloitin Virtualboxin asentamisen avaamalla Heinosen ohjeet ja avaamalla [download Virtualbox sivun](https://www.virtualbox.org/wiki/Downloads) Latasin sivulta VirtualBox 7.2.0 platform packages: Windows host version. Tässä kohtaa siirryin Karvisen(2021) install debian on virtual box ohjeisiin ja käytin niitä hyödyksi Virtual machinen asennukseen. 
1. Avasin ladatun Oracle VirtualBox 7.2.0 installerin
2. Valitsin kovalevyn jossa oli vähintää 30GB vapaata tilaa.
3. Asennusohjelma varoitti nettiyhteyden katkeamisesta, joten pidin huolta, että kaikki tarvittavat tiedostot on tallennettu ennen jatkamista eteenpäin.


## Lähteet
Karvinen, T. 2006. Raportin kirjoittaminen. Luettavissa: https://terokarvinen.com/2006/raportin-kirjoittaminen-4/. Luettu: 24.8.2025  
Karvinen, T. 2025. Linux Palvelimet 2025 alkusyksy: läksyt. Luettavissa: https://terokarvinen.com/linux-palvelimet/. luettu: 24.8.2025 
Karvinen, T. 2023. dreamhugmonkey. Luettavissa: https://github.com/terokarvinen/dreamhugmonkey. Luettu 24.8.2025  
Karvinen, T. 2021. install debian on virtual box. Luettavissa: https://terokarvinen.com/2021/install-debian-on-virtualbox/. Luettu 24.8.2025
Heinonen, J. 2025. Johanna-test-repo. linux-20082025.md. luettavissa: https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-20082025.md. Luettu: 24.8.2025  
SethClydesdale 2019. Luettavissa: https://github.com/orgs/community/discussions/22534. Luettu: 24.8.2025  
Markdown Guide. Basic Syntax. Luettavissa: https://www.markdownguide.org/basic-syntax/. Luettu: 24.8.2025
