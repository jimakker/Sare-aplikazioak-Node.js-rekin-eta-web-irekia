![Alt text](https://raw.githubusercontent.com/jimakker/Sare-aplikazioak-Node.js-rekin-eta-web-irekia/master/irudiak/goiburua.png)

#NPM

* Pakete kudeatzailea

* Github-en dauden moduluen katxe bat da (besteak beste)

* `package.json` izeneko fitxategi baten bidez konfiguratzen da

* bertan moduluaren mendekotasunak definitzen dira.  Garapenerako mendekotasunak baita ere.

* `npm install --save` eginda npm berak eguneratzen du package.json

* `package.json` fitxategia duen karpeta batean `npm install` eginda mendekotasun guztiak instalatuko ditu

* Mendekotasunak proiektuaren erroan bertan "instalatzen" dira, `node_modules` izeneko karpeta batean. 

* Modulu hauek erraz aztertu eta modifikatu ahal izatea abantaila handia da

* Garatzerakoan ez dira modulu hauek git-en gordetzen, `.gitignore` erabiltzen da hauek baztertzeko

* Produkzioan komenigarria izaten da moduluen kontrol zehatzagoa. 

* `npm shrinkwrap` komandoak momentuan erabiltzen ari diren moduluen bertsioak "izoztuko" ditu, zer instalatuko den zehazki jakiteko

* git-en gordetzea onena.

* npm erregistro pribatuak