#flexbricks 
# Access to partner tabs
## Usage: For hiding buttons

First Go to:
As a plmOn user (admin) go to Partner folder and select partner view.
Select any partner and also select any left tab. In the top you'll see a dropdown
"Shared:" (None, View, Edit). Select view or edit.

Enter to the system as a partner and use the same way
```ad-quote
title: List of pages and Share type to them
collapse: open
```sql

SELECT tp.TradePartnerTemplatePageID, tp.TradePartnerTemplatePageName, 
tp.TradePartnerTemplatePageURL, ti.TradePartnerTemplateItemID,
COALESCE(tis.partneraccesstype, 0) AS PartnerAccessToPage 
FROM uTradePartnerTemplateItem ti 
INNER JOIN uTradePartnerTemplateItemShare tis 
ON tis.TradePartnerTemplateItemId = ti.TradePartnerTemplateItemId 
INNER JOIN uTradePartnerTemplatePage tp 
ON ti.TradePartnerTemplatePageID = tp.TradePartnerTemplatePageID 
WHERE ti.TradePartnerTemplateID = '4090fa5e-2d43-4ce2-8195-c9d453aa2976' 
AND tis.PartnerAccessType IS NOT NULL 
AND tis.PartnerAccessType<>'0' 
AND TradePartnerId = 'ac303323-5ffd-4208-8057-521aa3340abe'
ORDER BY ti.Sort


-- OR

SELECT (COALESCE(partneraccesstype, 0) > 1) AS AccessToPage
FROM utradepartnertemplateitemshare
WHERE tradepartnerid = 'ac303323-5ffd-4208-8057-521aa3340abe'
AND tradepartnertemplateitemid = '1106bb78-67ed-4237-87b9-73250e42e713';

--SEE AlSO

SELECT * FROM vwx_uTradePartnerRelationshipType_SEL 
WHERE TradePartnerID = 'ac303323-5ffd-4208-8057-521aa3340abe' 
AND TradePartnerAllowRelationship = 1 

select spx_TradePartner_Agent_AccessType_SELECT(
'4090fa5e-2d43-4ce2-8195-c9d453aa2976',
'ac303323-5ffd-4208-8057-521aa3340abe');
```
