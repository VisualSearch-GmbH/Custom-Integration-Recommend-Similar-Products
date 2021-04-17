# Custom Integration - Recommend Similar Products
Instructions for custom shop systems on how to use similar products recommendations API

## English

### 1. Compute related products using webshop products

To compute related products using our API you need to invoke this command:

```bash
curl --location --request POST 'https://shopware.visualsearch.at/store-api/v3/vis/status_cross' \
--header 'sw-access-key: TEST_KEY' \
--data-raw ''
```

To use this command, you need a valid API key. Contact please office@visualsearch.at to obtain your API key.

### 2. Update existing related products in the webshop

To use the computed related products, the webshop needs to create and endpoint, which can accept them. Using this endpoint, we update the related products.

An example of using this endpoint is presented here:

```bash
curl --location --request POST 'https://YOUR_WEBSHOP.com/api/update_cross_selling' \
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
