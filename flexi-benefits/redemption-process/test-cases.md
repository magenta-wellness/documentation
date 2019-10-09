# Table of Contents
1. [Case #001](#c001)
2. Case #002

# <a name="c001"></a>C001
## Object Settings
### ClaimType
- *product: ChannelPartnerEmployerNonVoucherProduct*

id | name | product | limitBase | currency | employer
------------ | ------------- | ------------- | ------------- | ------------- | -------------
1 | Linked Product | 815 | MONEY | SGD | 1


Logic Name | Object | Property/Method | Input | Output | Action
------------ | ------------- | ------------- | ------------- | ------------- | -------------
Rdmpt Form | ClaimType{1} | limitBase: string | MONEY | |
NonPanel Linked Product Setup | ClaimType{1} | product: ChannelPartnerEmployerNonVoucherProduct | 815 | |
NonPanel Linked Product Setup | ClaimType{1} | limitBase: string | MONEY | |

