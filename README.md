## Languages

[Deutsch](README.md#Deutsch)

## Deutsch

# Benutzerdefinierte Integration - Ähnliche Produkte empfehlen
Anleitung für kundenspezifische Shopsysteme zur Verwendung unserer API für ähnliche Produktempfehlungen

### 1. Produktdaten aus dem Katalog übermitteln

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
    ["002ee82ce2754dd786c56a68bde02eb0", "Aerodynamic Plastic Proflex", ["135f57af59ec49cf953db9e9f1dbfeeb", "4f8938e279a4485fac26dc973151594b", "803a938a305f464dae2778e9d43abcc3"], ["Schuhe", "Handtaschen", "Neu"], "http://visrecommendsimilarproducts-ajwwh.testenv.shopware.in/shop/public/media/a3/3e/75/1617786384/b6a7105d66d8ef6bf38a7bccfdf57746.jpg"],
    ["0fc5589aa7d9430fa431d96193b4b8d1", "Small Concrete Virtual Horseshoes", ["135f57af59ec49cf953db9e9f1dbfeeb", "4f8938e279a4485fac26dc973151594b", "803a938a305f464dae2778e9d43abcc3"], ["Schuhe", "Handtaschen", "Neu"], "http://visrecommendsimilarproducts-ajwwh.testenv.shopware.in/shop/public/media/78/72/89/1617786383/63b0317865f07190263723a09ce64ed9.jpg"],
    ["264ef0475b20404b96487795987b5473", "Lightweight Wool G2-Tambi\u00e9n", ["135f57af59ec49cf953db9e9f1dbfeeb", "4f8938e279a4485fac26dc973151594b", "803a938a305f464dae2778e9d43abcc3"], ["Schuhe", "Handtaschen", "Neu"], "http://visrecommendsimilarproducts-ajwwh.testenv.shopware.in/shop/public/media/2e/67/ba/1617786381/3e412a097a9db2766d811dd33c080267.jpg"]
  ]
}'
```
Sie haben die Möglichkeit, die Produkte oder Kategorien auszuwählen, für die Sie Empfehlungen berechnen möchten. Wie Sie hier sehen können, benötigen wir Produkt-IDs, Namen, Kategorien-IDs, Kategorien-Namen und Bild-URLs. Es ist auch möglich, die Anzahl der berechneten Empfehlungen mit einem zusätzlichen Parameter anzugeben.

Um diese Anfrage zu senden, benötigen Sie einen gültigen API-Schlüssel. Kontaktieren Sie bitte office@visualsearch.at, um Ihren API-Schlüssel zu erhalten. Der Systemschlüssel ist eine optionale Variable, die für den Zugriff auf den Webshop verwendet wird. Die Berechnungszeit ähnlicher Produkte variiert je nach Größe des Katalogs. Für 1.000 Produkte sollte es etwa 5 Minuten dauern. Für Kunden mit großem Katalog können wir die Berechnung von 1.000 Produkten auf wenige Sekunden beschleunigen.

Wenn die Anfrage akzeptiert wird, sollten Sie diese Meldung erhalten:

```bash
{
    "code": 200,
    "message": "API processing started key API_TEST_KEY"
}
```
Wenn die Anfrage nicht akzeptiert wird, sollten Sie eine Meldung mit Code 500 erhalten.

### 2. Abrufen von berechneten Produktempfehlungen

#### Alternative #1 Produktempfehlungen mit Befehl abrufen

Sie können die Ergebnisse mit diesem Befehl abfragen

```bash
{
curl --location --request POST 'https://api.visualsearch.wien/similar_results' --header 'Vis-API-KEY: API_TEST_KEY'
}
```

Die Ergebnisse haben dieses Format
```bash
{ "products": {"00025beea86041d5891b989e59d7f8b8": ["8ba5f4bc5ddd4a75bfe55238e9308385","0dda22aa515843e282691970711a9a16","ca97b9a85c3b4d1a99ef9258b255f555"],... }}
```

Das bedeutet, dass das Produkt "00025beea86041d5891b989e59d7f8b8" z.B. drei ähnliche Produkte hat. Ihre IDs sind in dem Array zu finden.

#### Alternative #2 Update über Webshop-API

Wenn Sie sich für diese Alternative entscheiden, dann müssen Sie nicht auf die Ergebnisse warten. Unsere API wird die Ergebnisse automatisch in Ihren Webshop hochladen. 

Falls Sie Shopware verwenden und nur bestimmte Produkte oder Kategorien aktualisieren möchten, können Sie trotzdem unser Plugin verwenden. Sie müssen die automatischen Updates deaktivieren und Ihre Produkte manuell auf unseren Server hochladen, wie im vorherigen Kapitel beschrieben wurde.

Wenn Sie die Aktualisierung manuell auslösen, schickt unser Server die berechneten Empfehlungen über diesen Endpunkt zurück in Ihren Webshop. Ein Beispiel für die Aktualisierung eines Produkts mit der ID = 7dec5b61d24f4b1bbfd061fe5d2265cc mit 5 zugehörigen Produkten unter Verwendung dieses Endpoints wird hier dargestellt:

```bash
curl --location --request POST 'https://shopware.visualsearch.at/api/v3/vis/sim/update_cross' \
--header 'Authorization: Bearer XYZ123' \
--header 'Content-Type: application/json' \
--data-raw '{"products":
{
  "7dec5b61d24f4b1bbfd061fe5d2265cc":["a32fd2f7fa6c4ed4971630e443855f99", "91f639a5a9cd4cd699eb7d926703b98b", "e817bd859d2a4401ab69499abc86d801", "8ba5f4bc5ddd4a75bfe55238e9308385", "9988e0f6e23f47e1aafaab2c9317dd78"]
}
}'
```

### Contact
E-Mail: office@visualsearch.at, Web: www.visualsearch.at, Mobile: +43 670 6017118

UID-Number: ATU74052259, Registration Number: FN 505045 p, Jurisdiction: Commercial court of Vienna, Austria

### License
[MIT](https://choosealicense.com/licenses/mit/)
