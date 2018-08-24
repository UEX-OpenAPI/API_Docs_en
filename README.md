# UEX OpenAPI document

## General Rules

**"_api key_" and "_secret_" are not passwords and are generated in the UEX "[My API](https://www.uex.com/my_open_api.html)".**


**Base url：https:// open-api.uex.com**

**Signature**  
The request parameters need to be ordered by dictionary, and then to be joined as string in the form of keyvalue，finally, sign=MD5(string+secretKey).  
Note：If there is any NULL in the request parameters, then it isn’t be included in the signature string during joining.


For example：  
```python
def sign (data, apikey, secret):
    data = copy.deepcopy(data)
    data['time'] = int(time.time())
    data['api_key'] = apikey
    keys = list(data.keys())
    keys.sort()
    part = []
    for key in keys:
        val = data[key]
        if val is None:
            continue
        part.append(str(key) + str(val))
    text = ''.join(part)
    text = (text + secret).encode('utf-8')
    data['sign'] = hashlib.md5(text).hexdigest()
    return data 
```

<br>

## POST the request parameters submitted data with form format

**content-type:application/x-www-form-urlencoded**

<br>

## Document Contents

[Home](https://github.com/UEX-OpenAPI/API_Docs_en/wik)

[/open/api/all_order -Get all delegation](https://github.com/UEX-OpenAPI/API_Docs_en/wiki/Get-all-delegation)

[/open/api/all_trade -Get all transaction record](https://github.com/UEX-OpenAPI/API_Docs_en/wiki/Get-all-transaction-record)

[/open/api/cancel_order -Cancel delegation order](https://github.com/UEX-OpenAPI/API_Docs_en/wiki/Cancel-delegation-order)

[/open/api/common/symbols -Query all transaction pairs and accuracy supported by the system](https://github.com/UEX-OpenAPI/API_Docs_en/wiki/Query-all-transaction-pairs-and-accuracy-supported-by-system)

[/open/api/create_order -Create order](https://github.com/UEX-OpenAPI/API_Docs_en/wiki/Create-order)

[/open/api/get_records -Get K-line data](https://github.com/UEX-OpenAPI/API_Docs_en/wiki/Get-K-line-data)

[/open/api/get_ticker -Get current quotations](https://github.com/UEX-OpenAPI/API_Docs_en/wiki/Get-current-Quotations)

[/open/api/get_trades -Get transaction record of quotations](https://github.com/UEX-OpenAPI/API_Docs_en/wiki/Get-transaction-record-of-quotations)

[/open/api/market_dept -Query orders depth](https://github.com/UEX-OpenAPI/API_Docs_en/wiki/Query-orders-depth)

[/open/api/market -Get the latest transaction price of each currency pair ](https://github.com/UEX-OpenAPI/API_Docs_en/wiki/Get-the-latest-transaction-price-of-each-currency-pair)

[/open/api/new_order -Get current delegation](https://github.com/UEX-OpenAPI/API_Docs_en/wiki/Get-current-delegations)

[/open/api/order_info -Get order details ](https://github.com/UEX-OpenAPI/API_Docs_en/wiki/Get-order-details)

[/open/api/user/account -Asset balance](https://github.com/UEX-OpenAPI/API_Docs_en/wiki/Asset-balance)

<br>

