https://megamorf.gitlab.io/2019/08/27/safari-nsposixerrordomain-100-error-with-nginx-and-apache.html

https://serverfault.com/questions/937253/https-doesnt-work-with-safari

ALTER TABLE mhs__channel_partners_employers__products ADD uuid VARCHAR(255) NULL;
ALTER TABLE mhs__sales_partners__products ADD uuid VARCHAR(255) NULL;
ALTER TABLE mhs__channel_partners__products ADD uuid VARCHAR(255)  NULL;
ALTER TABLE mhs__principal__product ADD uuid VARCHAR(255)  NULL;
ALTER TABLE mhs__order_item ADD uuid VARCHAR(255)  NULL;
ALTER TABLE mhs__transaction ADD uuid VARCHAR(255)  NULL;
ALTER TABLE mhs__channel_partner ADD uuid VARCHAR(255)  NULL ;
ALTER TABLE mhs__claim__approver ADD uuid VARCHAR(255)  NULL ;
ALTER TABLE mhs__claim__benefit ADD uuid VARCHAR(255)  NULL ;
ALTER TABLE mhs__claim__type ADD uuid VARCHAR(255)  NULL ;
ALTER TABLE mhs__employer_benefit ADD uuid VARCHAR(255)  NULL ;
ALTER TABLE mhs__employer__employee ADD uuid VARCHAR(255)  NULL ;
ALTER TABLE mhs__employer ADD uuid VARCHAR(255) NULL ;
ALTER TABLE mhs__clinic ADD uuid VARCHAR(255)  NULL ;
ALTER TABLE mhs__principal ADD uuid VARCHAR(255)  NULL ;
ALTER TABLE mhs__sales_partner ADD uuid VARCHAR(255)  NULL ;



mhs__channel_partners_employers__products__voucher
"id"	"id_business_employer"	"id_channel_partner_employer"	"id_channel_partner_voucher_product"
"60"	"17"	"18"	"22"

DELETE FROM `magenta_wellness`.`mhs__channel_partners_employers__products` WHERE  `id`=61;




Workers:
- EventUpdateWorker

Quick Debug
file_put_contents('D:\\workspace\\magenta\\wellness\\legacy\\entity-manager.txt', 'changeSet '.json_encode($changeSet).PHP_EOL, FILE_APPEND);

Update sql

UPDATE `wellness_live`.`mhs__transaction` 
SET `non_panel`= '0' 
WHERE `instance_type` not like 'CLAIM_TRANSACTION';

UPDATE `wellness_live`.`mhs__transaction` 
SET `non_panel`= '1' 
WHERE `instance_type` like 'CLAIM_TRANSACTION';


UPDATE `wellness_live`.`mhs__transaction` 
SET `instance_type`= 'ITEM_CLAIM' 
WHERE `discr` like 'item_claim';

UPDATE `wellness_live`.`mhs__transaction` 
SET `instance_type`= 'EMPLOYEE_VISIT' 
WHERE `discr` like 'visit';

UPDATE `wellness_live`.`mhs__transaction` 
SET `instance_type`= 'CLAIM_TRANSACTION' 
WHERE `discr` like 'non_panel_claim';



health-services
============
- ChannelPartnerProduct is supposed to only be used for Voucher-based Products
- When adding a new RedemptionTransaction sub-type, adjust
    - ClinicTransactionAdmin 
    and 
    - TransactionRepository
- BusinessEmployeeVisit List can be found under:
    - Employer Login/Analytics/Product Consumption > (Action) View Visits    

Report
============
- Total no of employees for Out-Patient Program: 1647
- Total Value till date for PLan A and Plan B: $4285.5
- Total number of voucher product sales and value (If possible, breakdown based on which package) if possible without the dummy purchases
990701
---
SELECT ee.name as eeName,m0_.id AS sclr_0, m1_.total  AS total , m8_.name AS name,
m1_.clinic_name as ClinicName
FROM mhs__employer__employee_visit m1_ 
INNER JOIN mhs__employer_benefit ben 
ON ben.id = m1_.id_benefit
INNER JOIN mhs__employer__employee ee
ON ben.id_business_employee = ee.id
INNER JOIN mhs__transaction m0_ 
ON m1_.id = m0_.id INNER JOIN mhs__employer_benefit m2_ 
ON m1_.id_benefit = m2_.id INNER JOIN mhs__channel_partners_employers__products__non_voucher m3_ 
ON m2_.id_employer_non_voucher_product = m3_.id 
LEFT JOIN mhs__channel_partners_employers__products m4_ 
ON m3_.id = m4_.id INNER JOIN mhs__channel_partners__products m5_ 
ON m4_.id_channel_partner_product = m5_.id LEFT JOIN mhs__channel_partners__products__voucher m6_ 
ON m5_.id = m6_.id LEFT JOIN mhs__channel_partners__products__non_voucher m7_ ON m5_.id = m7_.id 
INNER JOIN mhs__principal__product m8_ 
ON m5_.id_product = m8_.id 
LEFT JOIN mhs__principal__product__voucher m9_ 
ON m8_.id = m9_.id 
LEFT JOIN mhs__principal__product__non_voucher m10_ 
ON m8_.id = m10_.id WHERE m8_.id = 10
---
select  count(distinct od.id), sum(od.total) from `mhs__order` od
INNER JOIN `mhs__order__business` ob ON ob.id = od.id

INNER JOIN `mhs__employer` er ON er.id = ob.id_business_employer

INNER JOIN `mhs__employer_benefit` ben ON er.id = ben.id_business_employer

INNER JOIN `organisation__organisation` org ON org.id = er.id_organisation
INNER JOIN `mhs__channel_partners_employers` cpe ON cpe.id_employer = er.id 
INNER JOIN `mhs__channel_partners_employers__products__non_voucher` cpeNonVP 
ON cpeNonVP.`id` = ben.`id_employer_non_voucher_product`
INNER JOIN `mhs__channel_partners__products__non_voucher` cpNonVP 
ON cpNonVP.`id` = cpeNonVP.`id_channel_partner_non_voucher_product`
INNER JOIN `mhs__channel_partners__products` cpP ON cpP.id = cpNonVP.id
INNER JOIN `mhs__principal__product` pp ON pp.id = cpP.`id_product`
WHERE 
(org.reg_no LIKE '201537883C' OR org.reg_no LIKE '53279119C' OR
org.reg_no LIKE '201419954C' OR org.reg_no LIKE '53082953C' OR 
org.reg_no LIKE '201609963M' OR org.reg_no LIKE '201134148Z' OR
org.reg_no LIKE  'NUSS' OR org.reg_no LIKE '201330107Z' OR
org.reg_no LIKE '201228521G' OR org.reg_no LIKE '201313056G' OR
org.reg_no LIKE '20117104W' OR org.reg_no LIKE '200204215G' OR
org.reg_no LIKE 'T06FC6884E' OR org.reg_no LIKE  '199708037N' OR
org.reg_no LIKE  '201332280M' OR org.reg_no LIKE '200704603H-PTE-01' OR
org.reg_no LIKE  'C3-CN-HB' OR org.reg_no LIKE  '198801700E' OR org.reg_no LIKE  '2001-01-562H' OR
org.reg_no LIKE  '200711258W' OR org.reg_no LIKE  '200106490M' OR org.reg_no LIKE  'COM118' OR
org.reg_no LIKE  '201214425M' OR  org.reg_no LIKE  '201602017G' OR  org.reg_no LIKE  '200722413R' OR 
org.reg_no LIKE  '201018916C' OR  org.reg_no LIKE  '201715006N' OR  org.reg_no LIKE  '200710542G' OR 
org.reg_no LIKE  '201525600G' OR  org.reg_no LIKE  '201708746W' OR  org.reg_no LIKE  '200809585D' OR 
org.reg_no LIKE  '200919400N' OR  org.reg_no LIKE  '201632110Z' OR  org.reg_no LIKE  '201020358N(FL)' OR 
org.reg_no LIKE  '201220207M' OR  org.reg_no LIKE  '201319232H' OR  org.reg_no LIKE  '198601026G' OR 
org.reg_no LIKE  '200600721W' OR  org.reg_no LIKE  '201529324W' OR  org.reg_no LIKE  '199405327E' OR 
org.reg_no LIKE  '201623142W'

)


SELECT COUNT(m0_.id) AS sclr_0, SUM(m1_.total) AS sclr_1 FROM mhs__employer__employee_visit m1_ INNER JOIN mhs__transaction m0_ ON m1_.id = m0_.id

select count(distinct ee.id) from `mhs__employer__employee` ee 
INNER JOIN `mhs__employer_benefit` ben ON ee.id = ben.id_business_employee
INNER JOIN `mhs__employer` er ON er.id = ben.id_business_employer
INNER JOIN `organisation__organisation` org ON org.id = er.id_organisation
INNER JOIN `mhs__channel_partners_employers` cpe ON cpe.id_employer = er.id 
INNER JOIN `mhs__channel_partners_employers__products__non_voucher` cpeNonVP 
ON cpeNonVP.`id` = ben.`id_employer_non_voucher_product`
INNER JOIN `mhs__channel_partners__products__non_voucher` cpNonVP 
ON cpNonVP.`id` = cpeNonVP.`id_channel_partner_non_voucher_product`
INNER JOIN `mhs__channel_partners__products` cpP ON cpP.id = cpNonVP.id
INNER JOIN `mhs__principal__product` pp ON pp.id = cpP.`id_product`
WHERE (pp.id = 10 OR pp.id = 27)
AND 
(org.reg_no LIKE '201537883C' OR org.reg_no LIKE '53279119C' OR
org.reg_no LIKE '201419954C' OR org.reg_no LIKE '53082953C' OR 
org.reg_no LIKE '201609963M' OR org.reg_no LIKE '201134148Z' OR
org.reg_no LIKE  'NUSS' OR org.reg_no LIKE '201330107Z' OR
org.reg_no LIKE '201228521G' OR org.reg_no LIKE '201313056G' OR
org.reg_no LIKE '20117104W' OR org.reg_no LIKE '200204215G' OR
org.reg_no LIKE 'T06FC6884E' OR org.reg_no LIKE  '199708037N' OR
org.reg_no LIKE  '201332280M' OR org.reg_no LIKE '200704603H-PTE-01' OR
org.reg_no LIKE  'C3-CN-HB' OR org.reg_no LIKE  '198801700E' OR org.reg_no LIKE  '2001-01-562H' OR
org.reg_no LIKE  '200711258W' OR org.reg_no LIKE  '200106490M' OR org.reg_no LIKE  'COM118' OR
org.reg_no LIKE  '201214425M' OR  org.reg_no LIKE  '201602017G' OR  org.reg_no LIKE  '200722413R' OR 
org.reg_no LIKE  '201018916C' OR  org.reg_no LIKE  '201715006N' OR  org.reg_no LIKE  '200710542G' OR 
org.reg_no LIKE  '201525600G' OR  org.reg_no LIKE  '201708746W' OR  org.reg_no LIKE  '200809585D' OR 
org.reg_no LIKE  '200919400N' OR  org.reg_no LIKE  '201632110Z' OR  org.reg_no LIKE  '201020358N(FL)' OR 
org.reg_no LIKE  '201220207M' OR  org.reg_no LIKE  '201319232H' OR  org.reg_no LIKE  '198601026G' OR 
org.reg_no LIKE  '200600721W' OR  org.reg_no LIKE  '201529324W' OR  org.reg_no LIKE  '199405327E' OR 
org.reg_no LIKE  '201623142W'

)


SonataAdmin
============
- Each layout has the following benefits:
    - iCheck.fronteed.com
    
Landing Page
============
- E-Slip: (Spotify)
    - Standard
    - Huttons

EMPLOYER VIEW
============
- Product Consumption: https://www.magenta-wellness.com/en/system/app/employer-businessemployer/25/product-consumption
The Order Based Products must have GST added to the final value.
    
INHERITED MISTAKES
============
- Unnecessary Relations
    - BusinessBenefit was unnecessarily linked with both BusinessEmployer and BusinessEmployee

Employee Import Action
============
- AppBundle\Service\EmployeeService.php::employeesImportAction is used 
    1) when employees are imported to a **Voucher** Product in Mass Order Listing and 
    2) when employees are imported **directly** to an Employer.
    
    - If **$cpeProduct** not empty and instanceOf ChannelPartnerEmployerVoucherProduct, it s always (1)
    - _TODO_: add the function to import to **NON-voucher** Product too.
