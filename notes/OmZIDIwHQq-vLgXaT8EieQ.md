# SunUp Shopline API
### How my flatten function works
input
```
nested_json = {
    "key1": "value1",
    "key2": {
        "subkey1": "subvalue1",
        "subkey2": "subvalue2"
    },
    "key3": [10, 20, 30]
}

flattened = flatten_json(nested_json)
print(flattened)
```
output

```
{
    "key1": "value1",
    "key2.subkey1": "subvalue1",
    "key2.subkey2": "subvalue2",
    "key3.0": 10,
    "key3.1": 20,
    "key3.2": 30
}
```
will clean up index in later processing

## Profiles
```
'subscriptions':
[{'platform': 'sms', 'is_active': False},
    {'platform': 'email', 'is_active': True}]
```
into 
```
'subcription.platform.sms.is_active':False
'subcription.platform.email.is_active':False
```
since every 'subcription.platform.sms.is_active'for all profile is False, whole column is removed in the end output

## Orders
```
 'subtotal_items': [{'id': '64b76991bd5ffa00158265ae',
     'item_type': 'Product',
     'item_data': {'cart_item_id': '462942304',
      'promotion_id': None,
      'parent_item_ids': [],
      'triggering_item_id': '',
      'order_promotion_items': {},
      'is_exclude_promotion': False,
      'is_exclude_user_credit': False,
      'is_exclude_member_point': False,
      'has_exclude_promotion_tag': False,
      'custom_discounted_amount': {'cents': 0,
       'currency_symbol': 'NT$',
       'currency_iso': 'TWD',
       'label': '',
       'dollars': 0.0},
      'custom_discounted_amount_items': [],
      'user_credit_ratio_amount': {'cents': 50,
       'currency_symbol': 'NT$',
       'currency_iso': 'TWD',
       'label': 'NT$50',
       'dollars': 50.0}},
     'item_id': '60750607753c5f001a15e705',
     'item_variation_id': '',
}}]
```
We explode subtotal_items, and merge the 'item_id' of subtotal_items with the id of every order and create a new key 
new_key_name='orderID/productID'


also we concat every promotion_item["id"]

'discounted_amount' is mostly 0 in the datas, weird

shopline api for promotion items
https://open-api.docs.shoplineapp.com/docs/order-promotion_items


## Products
don't know why so few product, not sure if its SunUp's problem


Explode by Variations
new_key_name='id/variationsID'

'categories_all_info' =  {category_id}/{zh_hant_value}*{priority_value}
should contain most needed category infos





