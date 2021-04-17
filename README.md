# Custom Integration - Recommend Similar Products
Instructions for custom shop systems on how to use similar products recommendations API

## English

### 1. Compute related products using webshop products

Invoke this command to send catalogue products to the API:

```bash
curl --location --request POST 'https://shopware.visualsearch.at/store-api/v3/vis/status_cross' \
--header 'sw-access-key: TEST_KEY' \
--data-raw ''
```

This command starts the computation of related products a returns the result to the webshop.

### 2. Update existing related products in the webshop

The webshop needs create an endpoint, which can accept the computed related products.

```bash
curl --location --request POST 'https://shopware.visualsearch.at/store-api/v3/vis/status_cross' \
--header 'sw-access-key: TEST_KEY' \
--data-raw ''
```

## German


## Slovak / Czech

### Contact
E-Mail: office@visualsearch.at, Web: www.visualsearch.at, Mobile: +43 670 6017118

UID-Number: ATU74052259, Registration Number: FN 505045 p, Jurisdiction: Commercial court of Vienna, Austria

### License
[MIT](https://choosealicense.com/licenses/mit/)
