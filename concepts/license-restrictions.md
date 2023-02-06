---
title: Licentie-restricties
permalink: /concepts/license-restrictions
---

## Inleiding
Het Knowmax Licentiesysteem ondersteunt naast de identiteitscontrole op bijvoorbeeld gebruikersnaam en wachtwoord ook andere voorwaarden waaraan moet worden voldaan om toegang te krijgen. Deze extra controles noemen we licentie-restricties.

## Gelijktijdig gebruik
In de licentie kan het aantal plaatsen worden ingesteld dat tegelijkertijd gebruikt mag worden. Deze zogenaamde multi-user restrictie zorgt ervoor dat een gebruiker die toegang probeert te krijgen op een licentie waarvan het maximum aantal gelijktijdige plaatsen is bereikt, wordt geweigerd. Pas als een andere gebruiker uitlogt zal er weer een plek beschikbaar komen.

Bovenstaande multi-user restrictie kan voor de hele licentie gelden, maar kan ook per [licentieonderdeel](/concepts/license-components) worden ingesteld.

## Geldigheid
Aan de licentie kan een vervaldatum gekoppeld worden. Na deze datum zal toegang met deze licentie door het licentiesysteem worden geweigerd.
Een bijzonder variant van een vervallen geldigheid is de zogenaamde "verval op toegangsteller". Als deze variant is ingesteld zal de licentie na een aantal keren gebruikt te zijn vervallen. Deze teller kan opgehoogd worden door het aantal pogingen om toegang te vekrijgen tot de licentie of tot een [licentieonderdeel](/concepts/license-components). Als het ingestelde maximum is bereikt zal toegang worden geweigerd. Deze geldigheidsrestrictie wordt veel voor demonstratie- of proefopstellingen gebruikt.

## Versie beperkingen
Een applicatie kan meerdere versies ondersteunen. Door een versiebeperking in te stellen kan de licentiebeheerder de toegang afdwingen vanaf een bepaalde versie en tot een bepaalde versie van de applicatie.

## Toegangsregels
Met behulp van toegangsregels kan naast de inloggegevens gecontroleerd worden vanaf welke locatie de gebruiker toegang probeert te krijgen. Dit kan door één of meerdere IP-v4 adressen in te stellen of IP-v4 ranges op te geven. Alleen vanaf deze IP-adressen zal toegang worden verleend.

Een licentie-restrictie kan ook via een zogenaamde HTTP-referer worden ingesteld. Een gebruiker moet dan vanaf een bepaalde URL komen om toegang te krijgen.

Als derde variant kan de licentie-toegang middels een zogenaamde MD5-hashkey worden bepaald. Met behulp van een secret key wordt aan de kant van de zender (bijvoorbeeld een externe website) een MD5-key berekend. In het Knowmax Licentiesysteem kan de secret key worden ingevuld waardoor het licentiesysteem in staat is om dezelfde MD5-hash te berekenen en op basis daarvan wel of geen toegang te verlenen.

Het is ook mogelijk om toegangsregels in te stellen voor gebruik in combinatie met KennisId. Een KennisId profiel kan gebruikt worden als waarde voor een toegangsregel.

## Toegangsregel t.b.v. licentieherkenning
Toegangsregels kunnen exclusief gebruikt worden. Daarmee wordt bedoeld dat de licentietoegang pas wordt verleend als aan de voorwaarde uit de toegangsregel(s) wordt voldaan. In plaats van exclusief kunnen ze ook als herkenning worden gebruikt. ALs een gebruiker vanaf een bepaald IP-adres toegang probeert te krijgen zal automatisch de juiste licentie erbij gezocht worden als aan de licentie een automatische herkenning wordt gebruikt. Een combinatie van exclusieve en herkennings toegangsregel wordt ook ondersteund.
