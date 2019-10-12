## Object Settings
### Functional Statements
1. Panel Claim => Panel Product
1. NonPanel Claim 
    1. NonPanel Product (unlinked) => If a NonPanel ClaimType is not linked to a Panel CPE Product, it is called Flexi Benefit
    1. Panel Product (linked) => a NonPanel ClaimType could be linked to a Panel CPE Product.
1. Medical Certificates could be enabled for either NonPanel or Panel with Voucher-based or NonVoucher-based
1. This is different from Medical Report which is only for Voucher-based Products
1. MC Submissions do not need approving, only Flexi Claim Transactions do *linked/unlinked*.

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

