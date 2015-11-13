---
layout: post
categories: Apunts
title: Apunts SVG
---

El format SVG serveix per crear gràfics vectorials i tot i que no és dels formats més coneguts té algunes característiques que el fan bastant interessant.

Com per exemple que al renderitzr les imatges a través d'un llenguatge permet escalar la imatge sense perdre qualitat i si la imatge és poc complexa, també fa que sigui no ocupi gaire espai en disc.

Una de les coses per les que ho volia utilitzar era per fer les imatges del post anterior ([Fanzines]({%post_url 2015-07-20-Fanzines-KISS%}))

El problema que m'he trobat és que no aconseguia que renderitzés bé el text, doncs no agafava bé la tipografia.

He estant cercant i fent diverses proves i just abans d'escriure aquest artícle, només havia aconseguit que es renderitzés correctament el text amb tipografia que jo volia si inseria el codi directament allà on volia que es mostrés de la pàgina.

Aquí els dos resultats que havia aconseguit, la primera inserint el codi directament a la pàgina i la segona inserint la imatge amb a través de l'etiqueta *img*:

<svg width="500px" height="150px" viewBox="0 0 501 152"
     xmlns="http://www.w3.org/2000/svg" version="1.1">
     <defs>
       <style type="text/css">
         <![CDATA[
         @font-face {
             font-family: 'GNUtypewriter';
             src: url('/assets/gtw.otf');
             font-weight: normal;
             font-style: normal;
         }
         ]]>
      </style>
     </defs>
      <desc>Exemple de text</desc>
      <text x="20" y="50"
            font-family="GNUtypewriter" font-size="30" fill="blue" >
        Voldria escriure amb la
      </text>
      <text x="20" y="110"
            font-family="GNUtypewriter" font-size="30" fill="blue" >
        tipografia GNUtypewriter
      </text>
      <!-- Show outline of canvas using 'rect' element -->
      <rect x="1" y="1" width="500px" height="150px"
            fill="none" stroke="blue" stroke-width="2" />
</svg>

<img src="/assets/test.svg" />

Com es pot veure només es mostra la tipografia correcte en el primer cas.

Curiosament en el segon resultat el text no és seleccionable, això és el que m'ha fet pensar que potser un svg no s'inseria així o si més no es podia inserir d'alguna altra manera.

Així que una última cerca m'ha portat a trobar una altra manera de com inserir un SVG i aquest si que renderitza correctament la tipografia:

<object data="/assets/test.svg" type="image/svg+xml"></object>

El codi és el següent:

{% highlight html %}

<object data="/assets/fitxer.svg" type="image/svg+xml">
  <img src="/assets/fitxer-nosvg.png" />
</object>

{% endhighlight %}

Així el tag que cal utilitzar és el de *object*, de forma opcional, si es vol mostrar una altra imatge pel cas en el que el navegador no obri SVG es pot afegir dins de *object* un tag *img* amb una imatge en un altre format.

Tot i així aquesta solució té detalls que estaria bé polir:

* Si s'afegeix la imatge alternativa (fallback) si el navegador pot carregar l'svg, carregarà igualment l'altra imatge, pel que no serà del tot eficient.
* Un altre problema que he trobat és que, com a mínim fins la versió 4.4.4 d'android el renderitzat tampóc no és correcte, el text queda desplaçat del lloc on hauria d'estar. A partir de la versió 5 ja queda resolt.
* Per a que la imatge reaccioni segons els canvis de pantalla i sigui *responsive* caldrà fer algunes modificacions al codi.

Per a que agafés la tipografia s'ha hagut d'afegir aquest codi just després del tag *svg*:

{% highlight html%}
   <style
      type="text/css"
      id="style3">
        @font-face {
            font-family: 'GNUtypewriter';
            src:
                local('GNUTypewriter'),
                url('/assets/gtw.otf');
            font-weight: normal;
            font-style: normal;
        }
 </style>

 {% endhighlight %}
