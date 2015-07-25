---
layout: post
categories: Apunts
title: Fanzines (Imposició de pàgines)
---

Aquest és el primer pas per a imprimir fanzines de manera KISS ([Keep It Simple Stupid](https://ca.wikipedia.org/wiki/Principi_KISS)).

El format del fanzine resultant és un llibret de pàgines doblegades per la meitat. Si el document té més de 40 pàgines (10 fulls), caldria fer grups de quaderns per després acabar-los unint en un sol volum, això no s'explica en aquest artícle.

Preparació bàsica document
--------------------------

Per a que s'imprimeixi el document correctament, cal que tingui un nombre de pàgines múltiple de 4. Doncs en una fulla hi cabran 4 pàgines, dos pàgines per cara.

Si el document és editable, només cal anar afegint pàgines en blanc fins que el document tingui un nombre de pàgines múltiple de 4.

Si el document és un pdf, la manera més senzilla que he trobat és amb [PDF-Shuffler](http://sourceforge.net/projects/pdfshuffler/), disponible als repositoris de debian amb el nom [pdfshuffler](https://packages.debian.org/jessie/pdfshuffler).

Per a quadrar el nombre de pàgines, primer cal un pdf d'[una pàgina en blanc](/assets/pàginaenblanc.pdf), aquesta és en A4, amb l'editor de text de libre office i exportant-ho a pdf es pot crear una de la mida que faci falta.

Llavors amb el PDF-Shuffler i la pàginaenblanc.pdf, es van afegint al document original tantes pàgines en blanc com faci falta per arribar a ser múltiple de 4.

Imposició del document
----------------------

Per aconseguir el document imposat s'explicaran dues opcions:

* Manualment.
    * Per comprendre millor què cal fer, per això és més elaborat.
* Amb el programa [bookbinder](http://www.quantumelephant.co.uk/bookbinder/bookbinder.html).
    * Molt ràpid i fàcil.

Manualment
----------

### Calcular l'ordre de les pàgines

Aquesta imatge mostra com quedaria la imposició d'un document de 8 pàgines:

{: .img-center}
![Imposició de 8 pàgines en A4](/assets/FanzinesKISS-01.png)

L'ordre de les pàgines respecte el document original hauria de ser:

{: .img-center}
8,1,2,7,6,3,4,5

Per saber l'ordre d'un document amb qualsevol nombre de pàgines (**sempre múltiples de 4**) hi ha una manera molt senzilla de trobar-ho, per exemple en un document de 16 pàgines.

1.S'escriu el número de pàgines en dues columnes en l'ordre indicat per les fletxes:

{: .img-center}
![Escriure número de pàgines](/assets/FanzinesKISS-03.png)

2.Començant des de l'última pàgina es passa per cada número fent aquest recorregut:

{: .img-center}
![recorregut per definir l'ordre](/assets/FanzinesKISS-04.png)

3.L'ordre final:

{: .img-center}
16,1,2,15,14,3,4,13,12,5,6,11,10,7,8,9

Per automatitzar el procés de treure l'ordre de les pàgines he fet un senzill programa que introduïnt el nombre de pàgines del document et diu l'ordre de les pàgines, el podeu trobar al [repositori imposition](https://github.com/duub/Imposition).

S'executa a través del terminal:

{% highlight sh %}
cd /ruta/al/directori/
python imposition.py
{% endhighlight %}

### Ordenar les pàgines per imprimir

Amb el PDF-Shuffler es pot ordenar manualment el document, movent les pàgines una a una i així tenim el document preparat i només cal configurar a l'imprimir que el volem imprimir a **doble cara** i que ha de **girar la fulla pel costat curt**.

L'inconvenient d'aquest mètode és que si són moltes pàgines és una feinada.

Per estalviar-te aquest pas, segons des de quin programa imprimeixis et permet indicar-li l'ordre de les pàgines, aquí un exemple per un document de 4 pàgines:

{: .img-center}
![Imposició de 8 pàgines en A4](/assets/FanzinesKISS-02.png)

Imprimint d'aquesta manera cal configurar els següents paràmetres:

* A doble cara girant pel costat curt.
* 2 pàgines per cara.
* Ordenat de pàgines d'esquerra a dreta.

Si ho vols imprimir amb una impresora que no permet la impressió a doble cara cal mirar com es poden imprimir totes les fulles d'una cara i després tornant a posar les fulles imprimir la segona cara.

Bookbinder
----------

### Baixar i executar programa

Al web de l'autor es troba l'enllaç per descarregar l'aplicació, es descomprimeix a la carpeta on es vulgui i si fent doble click sobre Bookbinder.jar cal executar des del terminal la següent comanda;

{% highlight sh %}
cd /ruta/al/directori/
java -jar bookbinder.jar
{% endhighlight %}

i llavors si tot va bé s'hauria d'obrir una nova finestra amb l'aplicació:

{:.img-center}
![Bookbinder](/assets/FanzinesKISS-05.png)

### Utilització del programa

Per a aconseguir un document on les pàgines estiguin imposades per a fer el llibret cal tenir en compte els següents punts:

* Primer de tot carregar el fitxer: *File -> Open input PDF*
* A "*Printer type*" si no tens impressora duplex (que imprimeix a doble cara) cal indicar *Single sided* llavors genera dos pdfs per a que s'imprimeixi el primer, tornar a posar els fulls a la impressora i imprimir el segon document sobre els fulls impressos.
* L'opció "*Alternate Page Rotation*" ajuda a girar les pàgines per a que a l'imprimir una cara no quedi al revés de l'altra. Aquesta opció jo la desmarco i després a l'imprimir indico que giri pel costat curt, així en el document en digital les  pàgines tenen totes la mateixa orientació.
* A "*Signature format*" cal triar Booklet, doncs és el tipus de fanzine que es doblega la fulla per la meitat.
* La resta d'opcions es deixen per defecte.

Llavors ja es pot apretar el botó "*Generate Document*" i a la carpeta on hi tenim el Bookbinder hi trobarem una nova carpeta amb el pdf imposat preparat per a ser imprés!
