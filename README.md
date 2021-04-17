# Custom Integration - Recommend Similar Products
Instructions for custom shop systems on how to use our similar product recommendations API

## Languages

[English](README.md#English)

[Deutsch](README.md#Deutsch)

[Slovensky](README.md#Slovensky)

## English

### 1. Compute related products using webshop's catalogue

To compute related products using our API you need to send the following request:

```bash
curl --location --request POST 'https://api.visualsearch.wien/similar_compute' \
--header 'Vis-API-KEY: API_TEST_KEY' \
--header 'Vis-SYSTEM-KEY: SYSTEM_KEY' \
--header 'Vis-SYSTEM-HOSTS: domain.com' \
--header 'Vis-SYSTEM-TYPE: custom' \
--header 'Content-Type: application/json' \
--data-raw '{"products": 
  [
    ["002ee82ce2754dd786c56a68bde02eb0", "Aerodynamic Plastic Proflex", ["135f57af59ec49cf953db9e9f1dbfeeb", "4f8938e279a4485fac26dc973151594b", "803a938a305f464dae2778e9d43abcc3"], "http://visrecommendsimilarproducts-ajwwh.testenv.shopware.in/shop/public/media/a3/3e/75/1617786384/b6a7105d66d8ef6bf38a7bccfdf57746.jpg"],
    ["0fc5589aa7d9430fa431d96193b4b8d1", "Small Concrete Virtual Horseshoes", ["135f57af59ec49cf953db9e9f1dbfeeb", "4f8938e279a4485fac26dc973151594b", "803a938a305f464dae2778e9d43abcc3"], "http://visrecommendsimilarproducts-ajwwh.testenv.shopware.in/shop/public/media/78/72/89/1617786383/63b0317865f07190263723a09ce64ed9.jpg"],
    ["264ef0475b20404b96487795987b5473", "Lightweight Wool G2-Tambi\u00e9n", ["135f57af59ec49cf953db9e9f1dbfeeb", "4f8938e279a4485fac26dc973151594b", "803a938a305f464dae2778e9d43abcc3"], "http://visrecommendsimilarproducts-ajwwh.testenv.shopware.in/shop/public/media/2e/67/ba/1617786381/3e412a097a9db2766d811dd33c080267.jpg"]
  ]
}'
```
As you can see here, we need product IDs, names, categories and image urls.

To send this request, you need a valid API key. Contact please office@visualsearch.at to obtain your API key. System key is an optional variable, which is used to access the webshop. The computation of related products vary according to the size of the catalogue. For 1.000 products it should take about 5 minutes.

If the request is accepted, then you should receive this message:

```bash
{
    "code": 200,
    "message": "API processing started key API_TEST_KEY"
}
```
If the request is not accepted, then you should receive a message with code 500.

### 2. Update related products in the webshop

#### Alternative #1 Update using Json file

After you send the computation request, please wait according to the size of your catalogue. For 1.000 products about 5 min, for 10.000 products about 1 hour, etc. 

To use the latest computed related products, you can download the results from a provided url link e.g. https://api.visualsearch.wien/similar_compute/API_TEST_KEY.json. Here is an example of the content of a Json result file, where product with ID = 11dc680240b04f469ccba354cbf0b967 has these 2 related products:

```bash
{
  "products": 
    {"11dc680240b04f469ccba354cbf0b967": ["05dc680240b04f469ccba354cbf0b967", "2a88d9b59d474c7e869d8071649be43c"]}
}
```

#### Alternative #2 Update using webshop API

If you choose this alternative, then you do not need to wait for the results. Our API will automatically upload results to your webshop. 

To use the computed related products, the webshop needs to create an endpoint, which can accept them. Using this endpoint, we update the related products. We will use the previously provided System key.

An example of updating product with ID = 8e56cc01ee064d7dbaf7a4356895da9f with 10 related products using this endpoint is presented here:

```bash
curl --location --request POST 'https://YOUR_WEBSHOP.com/api/update_cross_selling' \
--header 'Vis-SYSTEM-KEY: SYSTEM_KEY' \
--header 'Content-Type: application/json' \
--data-raw '{
  "products": 
  {
    "8e56cc01ee064d7dbaf7a4356895da9f": ["91004537ddb74ac89ef6b1f8853887c9", "8dcc68a7e9f44e6fa4429ce412adc80d", "f48fdd472c5d4b8d992da9a16faea29d",        "2171fe56f5614493838f7716795eb628", "0fce9c7e0c9549778cdf79cd5fd9cf5e", "354992a049af4e69a1b4a8ed27786a63", "427650c5390b4201af6ae8319a26f3fc", "56a332dafd254f8ba39d5fecc2661963", "232135a954f54852b0b9d3ebd97b8bc5", "3347bb11f3a44838bfcc7b4e80cc5474"]
    }
}'
```

## Deutsch

### 1. Ähnliche Produkte aus dem Katalog des Webshops berechnen

Um ähnliche Produkte mit unserer API zu berechnen, müssen Sie die folgende Anfrage senden:

```bash
curl --location --request POST 'https://api.visualsearch.wien/similar_compute' \
--header 'Vis-API-KEY: API_TEST_KEY' \
--header 'Vis-SYSTEM-KEY: SYSTEM_KEY' \
--header 'Vis-SYSTEM-HOSTS: domain.com' \
--header 'Vis-SYSTEM-TYPE: custom' \
--header 'Content-Type: application/json' \
--data-raw '{"products": 
  [
    ["002ee82ce2754dd786c56a68bde02eb0", "Aerodynamic Plastic Proflex", ["135f57af59ec49cf953db9e9f1dbfeeb", "4f8938e279a4485fac26dc973151594b", "803a938a305f464dae2778e9d43abcc3"], "http://visrecommendsimilarproducts-ajwwh.testenv.shopware.in/shop/public/media/a3/3e/75/1617786384/b6a7105d66d8ef6bf38a7bccfdf57746.jpg"],
    ["0fc5589aa7d9430fa431d96193b4b8d1", "Small Concrete Virtual Horseshoes", ["135f57af59ec49cf953db9e9f1dbfeeb", "4f8938e279a4485fac26dc973151594b", "803a938a305f464dae2778e9d43abcc3"], "http://visrecommendsimilarproducts-ajwwh.testenv.shopware.in/shop/public/media/78/72/89/1617786383/63b0317865f07190263723a09ce64ed9.jpg"],
    ["264ef0475b20404b96487795987b5473", "Lightweight Wool G2-Tambi\u00e9n", ["135f57af59ec49cf953db9e9f1dbfeeb", "4f8938e279a4485fac26dc973151594b", "803a938a305f464dae2778e9d43abcc3"], "http://visrecommendsimilarproducts-ajwwh.testenv.shopware.in/shop/public/media/2e/67/ba/1617786381/3e412a097a9db2766d811dd33c080267.jpg"]
  ]
}'
```
Wie Sie hier sehen können, benötigen wir Produkt-IDs, Namen, Kategorien und Bild-URLs.

Um diese Anfrage zu senden, benötigen Sie einen gültigen API-Schlüssel. Kontaktieren Sie bitte office@visualsearch.at, um Ihren API-Schlüssel zu erhalten. Der Systemschlüssel ist eine optionale Variable, die für den Zugriff auf den Webshop verwendet wird. Die Berechnung der ähnlichen Produkte variiert je nach Größe des Katalogs. Für 1.000 Produkte sollte es etwa 5 Minuten dauern.

Wenn die Anfrage akzeptiert wird, sollten Sie diese Meldung erhalten:

```bash
{
    "code": 200,
    "message": "API processing started key API_TEST_KEY"
}
```
Wenn die Anfrage nicht akzeptiert wird, sollten Sie eine Meldung mit Code 500 erhalten.

### 2. Ähnliche Produkte im Webshop aktualisieren

#### Alternative #1 Update mit Hilfe einer Json-Datei

Nachdem Sie die Berechnungsanfrage gesendet haben, warten Sie bitte entsprechend der Größe Ihres Katalogs. Für 1.000 Produkte ca. 5 min, für 10.000 Produkte ca. 1 Stunde, usw. 

Um die neuesten berechneten verwandten Produkte zu verwenden, können Sie die Ergebnisse von einem bereitgestellten URL-Link herunterladen, z. B. https://api.visualsearch.wien/similar_compute/API_TEST_KEY.json. Hier ist ein Beispiel des Inhalts einer Json-Ergebnisdatei, in der das Produkt mit der ID = 11dc680240b04f469ccba354cbf0b967 diese 2 ähnlichen Produkte hat:

```bash
{
  "products": 
    {"11dc680240b04f469ccba354cbf0b967": ["05dc680240b04f469ccba354cbf0b967", "2a88d9b59d474c7e869d8071649be43c"]}
}
```

#### Alternative #2 Update über Webshop-API

Wenn Sie sich für diese Alternative entscheiden, dann müssen Sie nicht auf die Ergebnisse warten. Unsere API wird die Ergebnisse automatisch in Ihren Webshop hochladen. 

Um die berechneten verwandten Produkte zu verwenden, muss der Webshop einen Endpoint erstellen, der diese akzeptieren kann. Über diesen Endpoint aktualisieren wir die verwandten Produkte. Wir werden den zuvor bereitgestellten Systemschlüssel verwenden.

Ein Beispiel für die Aktualisierung eines Produkts mit der ID = 8e56cc01ee064d7dbaf7a4356895da9f mit 10 zugehörigen Produkten unter Verwendung dieses Endpoints wird hier dargestellt:

```bash
curl --location --request POST 'https://YOUR_WEBSHOP.com/api/update_cross_selling' \
--header 'Vis-SYSTEM-KEY: SYSTEM_KEY' \
--header 'Content-Type: application/json' \
--data-raw '{
  "products": 
  {
    "8e56cc01ee064d7dbaf7a4356895da9f": ["91004537ddb74ac89ef6b1f8853887c9", "8dcc68a7e9f44e6fa4429ce412adc80d", "f48fdd472c5d4b8d992da9a16faea29d",        "2171fe56f5614493838f7716795eb628", "0fce9c7e0c9549778cdf79cd5fd9cf5e", "354992a049af4e69a1b4a8ed27786a63", "427650c5390b4201af6ae8319a26f3fc", "56a332dafd254f8ba39d5fecc2661963", "232135a954f54852b0b9d3ebd97b8bc5", "3347bb11f3a44838bfcc7b4e80cc5474"]
    }
}'
```

## Slovensky

### 1. Výpočet podobných produktov pomocou katalógu webového obchodu

Ak chcete vypočítať podobné produkty pomocou nášho API rozhrania, musíte odoslať nasledujúcu požiadavku:

```bash
curl --location --request POST 'https://api.visualsearch.wien/similar_compute' \
--header 'Vis-API-KEY: API_TEST_KEY' \
--header 'Vis-SYSTEM-KEY: SYSTEM_KEY' \
--header 'Vis-SYSTEM-HOSTS: domain.com' \
--header 'Vis-SYSTEM-TYPE: custom' \
--header 'Content-Type: application/json' \
--data-raw '{"products": 
  [
    ["002ee82ce2754dd786c56a68bde02eb0", "Aerodynamic Plastic Proflex", ["135f57af59ec49cf953db9e9f1dbfeeb", "4f8938e279a4485fac26dc973151594b", "803a938a305f464dae2778e9d43abcc3"], "http://visrecommendsimilarproducts-ajwwh.testenv.shopware.in/shop/public/media/a3/3e/75/1617786384/b6a7105d66d8ef6bf38a7bccfdf57746.jpg"],
    ["0fc5589aa7d9430fa431d96193b4b8d1", "Small Concrete Virtual Horseshoes", ["135f57af59ec49cf953db9e9f1dbfeeb", "4f8938e279a4485fac26dc973151594b", "803a938a305f464dae2778e9d43abcc3"], "http://visrecommendsimilarproducts-ajwwh.testenv.shopware.in/shop/public/media/78/72/89/1617786383/63b0317865f07190263723a09ce64ed9.jpg"],
    ["264ef0475b20404b96487795987b5473", "Lightweight Wool G2-Tambi\u00e9n", ["135f57af59ec49cf953db9e9f1dbfeeb", "4f8938e279a4485fac26dc973151594b", "803a938a305f464dae2778e9d43abcc3"], "http://visrecommendsimilarproducts-ajwwh.testenv.shopware.in/shop/public/media/2e/67/ba/1617786381/3e412a097a9db2766d811dd33c080267.jpg"]
  ]
}'
```
Ako vidíte, potrebujeme produktové ID, názvy, kategórie a URL adresy obrázkov.

Na odoslanie tejto požiadavky potrebujete platný API kľúč. Kontaktujte prosím office@visualsearch.at a získajte svoj kľúč API. Systémový kľúč je nepovinná premenná, ktorá sa používa na prístup k webovému obchodu. Výpočet podobných produktov sa líši podľa veľkosti katalógu. V prípade 1 000 produktov by to malo trvať približne 5 minút.

Ak je žiadosť prijatá, mala by sa zobraziť táto správa:

```bash
{
    "code": 200,
    "message": "API processing started key API_TEST_KEY"
}
```
Ak žiadosť nebude prijatá, mala by sa zobraziť správa s kódom 500.

### 2. Aktualizácia podobných produktov v internetovom obchode

#### Alternatíva 1. Aktualizácia pomocou súboru Json

Po odoslaní žiadosti o výpočet počkajte podľa veľkosti vášho katalógu. Pre 1 000 produktov približne 5 minút, pre 10 000 produktov približne 1 hodinu atď. 

Ak chcete používať najnovšie vypočítané súvisiace produkty, môžete si výsledky stiahnuť z poskytnutého url odkazu, napr. https://api.visualsearch.wien/similar_compute/API_TEST_KEY.json. Tu je príklad obsahu súboru s výsledkami Json, kde výrobok s ID = 11dc680240b04f469ccba354cbf0b967 má tieto 2 súvisiace výrobky:

```bash
{
  "products": 
    {"11dc680240b04f469ccba354cbf0b967": ["05dc680240b04f469ccba354cbf0b967", "2a88d9b59d474c7e869d8071649be43c"]}
}
```

#### Alternatíva 2. Aktualizácia pomocou webového obchodu API

Ak si vyberiete túto alternatívu, nemusíte čakať na výsledky. Naše rozhranie API automaticky nahrá výsledky do vášho internetového obchodu. 

Ak chcete používať vypočítané súvisiace produkty, webový obchod musí vytvoriť endpoint, ktorý ich dokáže prijať. Pomocou tohto endpointu aktualizujeme súvisiace produkty. Použijeme predtým zadaný systémový kľúč.

Tu je uvedený príklad aktualizácie produktu s ID = 8e56cc01ee064d7dbaf7a4356895da9f s 10 podobnými produktmi pomocou tohto koncového bodu:

```bash
curl --location --request POST 'https://YOUR_WEBSHOP.com/api/update_cross_selling' \
--header 'Vis-SYSTEM-KEY: SYSTEM_KEY' \
--header 'Content-Type: application/json' \
--data-raw '{
  "products": 
  {
    "8e56cc01ee064d7dbaf7a4356895da9f": ["91004537ddb74ac89ef6b1f8853887c9", "8dcc68a7e9f44e6fa4429ce412adc80d", "f48fdd472c5d4b8d992da9a16faea29d",        "2171fe56f5614493838f7716795eb628", "0fce9c7e0c9549778cdf79cd5fd9cf5e", "354992a049af4e69a1b4a8ed27786a63", "427650c5390b4201af6ae8319a26f3fc", "56a332dafd254f8ba39d5fecc2661963", "232135a954f54852b0b9d3ebd97b8bc5", "3347bb11f3a44838bfcc7b4e80cc5474"]
    }
}'
```

### Contact
E-Mail: office@visualsearch.at, Web: www.visualsearch.at, Mobile: +43 670 6017118

UID-Number: ATU74052259, Registration Number: FN 505045 p, Jurisdiction: Commercial court of Vienna, Austria

### License
[MIT](https://choosealicense.com/licenses/mit/)
