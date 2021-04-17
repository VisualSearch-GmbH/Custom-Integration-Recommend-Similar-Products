# Custom Integration - Recommend Similar Products
Instructions for custom shop systems on how to use our similar product recommendations API

## Languages

[English](README.md#English)

[German](README.md#German)

[Slovak](README.md#Slovak)

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

To send this request, you need a valid API key. Contact please office@visualsearch.at to obtain your API key. System key is an optional variable, which is used to access the webshop.

If the request is accepted, then you should receive this message:

```bash
{
    "code": 200,
    "message": "API processing started key API_TEST_KEY"
}
```
If the request is not accepted, then you should receive a message with code 500.

### 2. Update related products in the webshop

To use the computed related products, the webshop needs to create an endpoint, which can accept them. Using this endpoint, we update the related products.

An example of updating product with ID = 8e56cc01ee064d7dbaf7a4356895da9f using this endpoint is presented here:

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

## German

### 1. Compute related products using webshop products

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

To send this request, you need a valid API key. Contact please office@visualsearch.at to obtain your API key. System key is an optional variable, which is used to access the webshop.

### 2. Update existing related products in the webshop

To use the computed related products, the webshop needs to create and endpoint, which can accept them. Using this endpoint, we update the related products.

An example of updating product with ID = 8e56cc01ee064d7dbaf7a4356895da9f using this endpoint is presented here:

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

## Slovak

### 1. Vypocitaj podobne produkty z katalogu webshopu

Na vypocitanie podobnych produktov pomocou naseho API nam potrebujete poslat tento request:

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
Ako mozete vidiet tu, potrebujeme ID produktov, ich mena, kategorie a url obrazkov.

Na zaslanie tohto requestu je potrebny platny API kluc. Kontaktujte prosim office@visualsearch.at na obrzanie platneho API kluca. Systemovy kluc je potrebny len v pripade, ze si ho webshop vyzaduje.

V pripade uspechu by sme mali obdrzat tuto spravu:

```bash
{
    "code": 200,
    "message": "API processing started key API_TEST_KEY"
}
```
V pripade neuspechu by sme mali obdrzat spravu s kodom 500.

### 2. Aktualizovanie podobnych produktov vo webshope

Vypocitane podobne produkty pouzijeme na updatovanie webshopu. Na tento ucel potrebujeme aby webshop disponoval endpointom, ktory dokaze aktualizovat podobne produkty. Pouzijeme tento endpoint a pomocou neho aktualizujeme podobne produkty.

Na tomto priklade je uvedene ako sa da pomocou endpointu webshopu aktualizovat produkt s ID = 8e56cc01ee064d7dbaf7a4356895da9f:

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
