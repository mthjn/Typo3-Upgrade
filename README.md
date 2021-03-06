# Typo3 Upgrade Hitchhiker's Guide

Notes based on [TYPO3camp presentation](https://jweiland.net/typo3/vortraege/typo3camp-berlin-2014.html)
  
---
  
#### Anmerkungen

* Niemals auf dem live Servers, immer auf Kopie
* Backup machen + testen:
  Backup Struktur
  Backup Datenbank
  Neu installieren und ansehen, diese Kopie liegen lassen

#### Workflow:

* Kopie erstellen
* Kopie aufräumen 
* Dateistruktur kopieren
* Neue leere Datenbank, collation utf8_general_ci
* Commandline DB Duplikat:
     
     ```mysqldump --opt -u user1 -p password1 olddb | mysql -u user2 -p pass2 newdb```
     
* Dev Kopie fertigstellen, DNS und so.
* localconf.php anpassen: neue Datenbank
* TypoScript: baseURL anpassen

Kopie:

* Inaktive Extensionen löschen

! Extension "Additional Reports" für mehr Infos

* Obsolete Extensionen entfernen
* Install Tool aufrufen - Database Analyzer
* Tabellen leeren (aber nicht entfernen)
	  
	cache_  
	cachingframework_  
	cf_  
	sys_log, sys_stat,   
	tx_realurl_errorlog...  
	index_...  
  
Backend:  

* "Check for extension updates"
* Extensionen aktualisieren

 ! Dep Errors - PHP Versionen, Extension dep, Namespacing
 ! Backup Datenbank
 ! Die gleiche PHP Version wie in Produktion usw.

*  DB Check - Manage Reference Index - Update reference cache
 ! tt_news Tabellen

Error Logs:

* Error reports einschalten


Smooth migration:

* Erweiterung extbase / smoothmigration extension
* Benötigt BE User _cli_smoothmigration
* Berichte zur Migration

Symlink anktualisieren

* typo3_src -> typo3_src-7.4.1

Install Tool aufrufen - als Check

* Upgrade Wizard
* Errors, incompatible Erweiterungen...
* Was inkompatibel ist muss entfernt werden
* Database analyzer

Noch:

* Clear all cache
* TSConfig: options.clearCache.system = 1

Erweiterungen aktualisieren

TypoScript anpassen

Testen!
