![Alt text](https://raw.githubusercontent.com/jimakker/Sare-aplikazioak-Node.js-rekin-eta-web-irekia/master/irudiak/goiburua.png)

#EVENT LOOP

![Irudia](https://github.com/jimakker/Sare-aplikazioak-Node.js-rekin-eta-web-irekia/raw/master/irudiak/tradizionala_vs_nodejs.png)
Irudiaren sortzailea: <http://www.toptal.com/nodejs/why-the-hell-would-i-use-node-js>


```
 8 GB RAM
-------------  = 4000 konexio gehienez (beste gauza batzuk kontuan hartu gabe)
 2 MB/thread
```

* PUZ (CPU) erabilera intentsiboak haria/thread ito dezake, bezero guztientzako

* Gertakizun begiztan eszepzioa gertatzen bada aplikazioa itxiko da (*exception bubbling*)

* Hori ekiditeko, eszepzioa bota (*throw*) ordez callback parametro bezala itzultzen da

* Aplikazioa berriro martxan jartzeko erremintak badaude: pm2, forever...