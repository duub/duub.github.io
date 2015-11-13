---
layout: post
categories: Apunts
title: Actualitzar lloc web
---

Aquest lloc web funciona amb jekyll i per poder publicar nous artícles cal fer alguns passos.

* Afegir/Modificar els nous artícles.
* Executar jekyll:

```
  $ bundle exec jekyll build
```

* Després del pas anterior amb la configuració que ting s'hauria de copiar els fitxers del site resultant a la carpeta on hi ha el repo del site, sinó és així, cal copiar els fitxers generats.
* A la carpeta del repo del site commitejar els canvis:

```
  $ git status
  $ git add ...
  $ git commit -m "lelele"
  $ git push origin master
```

* Desplegar el repo al servidor web:

```
  $ ssh user@server 'deploy duub.org.git'
```

i ja s'hauria de tenir el site actualitzat!
