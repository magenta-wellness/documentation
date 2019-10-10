## Object Settings
### General Settings

- *product: ChannelPartnerEmployerNonVoucherProduct*

id | name | product | limitBase | currency | employer
------------ | ------------- | ------------- | ------------- | ------------- | -------------
1 | Linked Product | 815 | MONEY | SGD | 1


Logic Name | Object | Property/Method | Input | Output | Action
------------ | ------------- | ------------- | ------------- | ------------- | -------------
Rdmpt Form | ClaimType{1} | limitBase: string | MONEY | |
NonPanel Linked Product Setup | ClaimType{1} | product: ChannelPartnerEmployerNonVoucherProduct | 815 | |
NonPanel Linked Product Setup | ClaimType{1} | limitBase: string | MONEY | |

