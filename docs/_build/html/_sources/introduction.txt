============
Introduction
============

:Author:    Ramon Bartl
:Date:      2012-08-24



Plone Installation unter unter MS Windows Server 2008
=====================================================
- Plone 4.2 herunterladen
  https://launchpad.net/plone/4.2/4.2/+download/setup-plone42-4.2.0-5363-win32.exe

- starten und Anweisungen folgen.

- Nach der Installation mit dem Browser auf http://localhost:8080 und eine Plonesite anlegen.




Installation eines Plone Addon-Pakets (egg) unter MS Windows Server 2008
========================================================================

Vorbereitung
------------
- VIM-Editor herunterladen und installieren, da die plone-configfiles im MS notepad nicht richtig dargestellt werden
  http://www.heise.de/download/ab771657a2942a22c7a05e63a7f63fe1-1345797418-2218455.html

- Paket suchen
  http://pypi.python.org/pypi?:action=search&term=plone&submit=search
  In der Sektion "Installation" steht meist der egg-Name des Pakets z.B. "Products.PloneFormGen"


Installation
------------

- Im Windows-Explorer Rechtsklick auf c:\Plone42\buildout.cfg -> "edit with VIM" auswählen
  
  egg-Namen der gewünschten Addon-Pakete in der Sektion [eggs] unten anfügen...

  >>> 
    collective.js.jqueryui
    Products.PloneFormGen

  
  Aktuelle Versionen für diese Pakete "festnageln" in der Sektion [versions]

  >>>
    collective.js.jqueryui = 1.8.16.8
    Products.PloneFormGen = 1.7.2


  ...speichern


- Start -> Rechtsklick auf "Eingabeaufforderung" -> Als Administrator ausführen

  >>>
  set http_proxy=http://proxy.YOURDOMAIN.de:8080
  set https_proxy=http://proxy.YOURDOMAIN.de:8080
  cd c:\Plone42
  bin\buildout.exe
  net stop "Plone 4.2"
  net start "Plone 4.2"


- Im Browser auf http://localhost:8080/Plone
- Anmelden als admin
- Rechts oben im Benutzer-Menu auf "Konfiguration"
- Den Punkt "Erweiterungen" klicken
- Häkchen setzen bei den kürzlich hinzugefügten Paketen und den Button "aktivieren" klicken

Fertig!


.. vim: set ft=rst tw=75 nocin nosi ai spell sw=4 ts=4 expandtab:
