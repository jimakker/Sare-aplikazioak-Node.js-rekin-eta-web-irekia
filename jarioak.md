![Alt text](https://raw.githubusercontent.com/jimakker/Sare-aplikazioak-Node.js-rekin-eta-web-irekia/master/irudiak/goiburua.png)

#STREAM-ak
<http://maxogden.com/node-streams.html>

<https://github.com/substack/stream-handbook>


* Erreminta boteretsua

* BASH pipes

* Node 0.10-ean sartu zituzten Streams2 

* Node 0.12 Streams3!

* Bezeroan erabili litezke (<https://github.com/substack/shoe> + <https://github.com/dominictarr/mux-demux>)

* Jario bat EventEmitter bat da

* Erremintak: <https://www.npmjs.com/package/through>, <https://github.com/maxogden/concat-stream>, ...


###Modu normala:
```
var http = require('http');
var fs = require('fs');

var server = http.createServer(function (req, res) {
    fs.readFile(__dirname + '/data.txt', function (err, data) {
        res.end(data);
    });
});
server.listen(8000);
```
Fitxategi osoa katxeatu behar lehenengo... Eskaera bakoitzeko!



###Jarioak erabiliz:
```
var http = require('http');
var fs = require('fs');

var server = http.createServer(function (req, res) {
    var stream = fs.createReadStream(__dirname + '/data.txt');
    stream.pipe(res);
});
server.listen(8000);
```
* Zatika (chunk), berehala
* Bezeroak ez badu eskatzen ez da katxeatu (buffer)


###Konprimatuz:
```
var http = require('http');
var fs = require('fs');
var oppressor = require('oppressor');

var server = http.createServer(function (req, res) {
    var stream = fs.createReadStream(__dirname + '/data.txt');
    stream.pipe(oppressor(req)).pipe(res);
});
server.listen(8000);
```
Substack-ek LEGO piezak direla dio



##OINARRIAK

###pipe

```
src.pipe(dst);
        
a.pipe(b).pipe(c).pipe(d);
 
// Hau aurrekoaren berbera da 
a.pipe(b);
b.pipe(c);
c.pipe(d);        
```
    

###Irakurgarriak (Readable)
    
```
var Readable = require('stream').Readable;

var rs = new Readable;
rs.push('beep ');
rs.push('boop\n');
rs.push(null); // amaitzeko

rs.pipe(process.stdout);
```

`._read` funtzioa sortu ezkero, "on demand" da

```
var Readable = require('stream').Readable;
var rs = Readable();

var c = 97;
rs._read = function () {
    rs.push(String.fromCharCode(c++));
    if (c > 'z'.charCodeAt(0)) rs.push(null);
};

rs.pipe(process.stdout);
```

###Idazgarriak (Writable)
    
```
var Writable = require('stream').Writable;
var ws = Writable();
ws._write = function (chunk, enc, next) {
    console.dir(chunk);
    next(); // next(err)
};

process.stdin.pipe(ws);
```

* `Writable({ decodeStrings: false })`
* `Writable({ objectMode: true })`

###Transform

###Duplex