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




