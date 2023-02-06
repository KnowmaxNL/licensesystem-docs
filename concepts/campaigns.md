---
titel: Campagnes
pernmalink: /concepts/campaigns
---

## Inleiding
Het Knowmax Licentiesysteem beschikt over een module **campagnes** voor de automatische uitgifte van licenties. Het kan dan bijvoorbeeld gaan om demonstratielicenties met een beperkte geldigheid. De beschikbaarheid van deze module is afhankelijk van de afgenomen opties van het Knowmax Licentiesysteem. Neem contact op met Knowmax voor meer informatie over de beschikbaarheid.

Voor een campagne gebruikt kan worden moet deze eerst worden aangemaakt in het onderdeel **Campagnes** onder **Systeemconfiguratie**. Er zijn verschillende opties voor de configuratie van een campagne. Zo is het soort uit te geven licentie in te stellen, maar ook de wanneer de uitgegeven licentie zal vervallen. Bijvoorbeeld na een vast aantal dagen of het aantal keren dat de licentie gebruikt is. Verder zijn er instellingen te maken over de te gebruiken emailsjablonen die gebruikt worden voor communicatie met de aanvrager van een licentie en de campagnebeheerder.

Om te voorkomen dat een geautomatiseerd systeem de campagnemodule misbruikt om in massa licenties voor een bepaalde campagne aan te maken, is het per campagne mogelijk een mensverificatie toe te voegen. De campagnemodule ondersteunt hiervoor de [Recaptcha](https://www.google.com/recaptcha/about/) dienst van Google. Deze geeft de gebruiker een puzzel om te bewijzen dat we met een echt mens te maken hebben. Voordeel van deze dienst is de eenvoudige toepassing en daarnaast helpt de gebruiker bij het oplossen van een puzzel met het digitaliseren van boeken. In de campagne-instellingen kunnen de private en publieke sluetel van de recaptcha dienst worden opgeslagen.

## Aanvraagformulier
De API ingangen van de campagnemodule ondersteunen standaard HTML formulieren voor het aanvragen van een licentie. Er kan een vanuit een HTML pagina een **application/x-www-form-urlencoded** formulier met een POST verzonden worden naar **Api/Campaign/RequestLicenseHtml**. Deze ingang geeft als resultaat altijd een HTML pagina. Voor AJAX scenario's kan gebruik gemaakt worden van de API ingang **Api/Campaign/RequestLicense**. Deze geeft **XML** of **JSON** terug met het resultaat van de aanvraag.

Verplichte velden in HTML aanvraagformulier

Parameter | Omschrijving
---|---
campaign | Label van campagne waarvoor licentie wordt aangevraagd.
name | Naam van aanvrager.
email| Emailadres van aanvrager.

Onderstaande HTML fragment geeft een HTML formulier met de minimaal verplichte velden voor de aanvraag van een licentie. Naaste de verplichte velden is het mogelijk eigen velden in het formulier op te nemen en mee te sturen voor de licentie-aanvraag. Al deze waarden worden opgeslagen en zijn achteraf bij de automatisch aangemaakte licentie te raadplegen.

``` HTML
        <form action="http://licentie.bris.nl/Api/Campaign/RequestLicenseHtml" method="post">
          <input type="hidden" name="campaign" value="label-van-campagne" />       
          <label>Naam: <input type="text" name="name" /></label>          
          <label>Email: <input type="email" name="email" /></label>         
          <div id="recaptcha_area"></div>
          
          <button type="submit">Verstuur</button>          
        </form> 
``` 

In het bovenstaande fragment is ook een **div** element met als **id** de waarde **recaptcha_area** opgenomen voor de eerder beschreven mensverificatie met behulp van Goolge Recaptcha. Onderstaande fragment toont de benodigde Javascript om het formulier aan te sluiten op de Recaptcha dienst. In dit voorbeeld gebruiken we ook jQuery. Voor meer mogelijkheden om de Recaptcha dienst te gebruiken verwijzen we naar de [documentatie](https://www.google.com/recaptcha/about/).

``` javascript
        <script src="http://ajax.googleapis.com/ajax/libs/jquery/2.0.2/jquery.min.js"></script>
        <script type="text/javascript" src="http://www.google.com/recaptcha/api/js/recaptcha_ajax.js"></script>
        <script>
          $(function () {
            Recaptcha.create("publieke-recaptcha-sleutel", "recaptcha_area", {
              theme: "blackglass"
            });
          });
        </script>         
```

Voor iedere campagne is een voorbeeldformulier met de verplichte velden op te vragen. Gebruik daarvoor onderstaande adres en vervang {campagne} voor het label van de campagne.
```
http://licentie.bris.nl/Campaign/Subscribe/{campagne}
```

## Na de licentie-uitgifte
Na een succesvolle automatische licentie-uitgifte is de licentie zoals alle andere licenties te bekijken in Knowmax Licentiebeheer. Automatisch uitgegeven licenties hebben een extra tabblad Campagne. Op dit tabblad is te zien met welke **campagne** de licentie is uitgegeven en welke gegevens de gebruiker in het aanvraagformulier heeft ingevuld.

Op het scherm met alle licenties kan met de filteropties een selectie gemaakt worden van alle licenties die in het kader van een bepaalde campagne zijn uitgegeven.

Indien in het Knowmax Licentiesysteem ook de module Knowmax MagmaStats beschikbaar is, kunnen via de MagmaStats log ook de mislukte aanvragen bekeken worden.