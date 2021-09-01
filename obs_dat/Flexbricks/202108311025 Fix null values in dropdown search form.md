#flexbricks 

```ad-info
title: FormHandler.vb
collapse: open
```dotnet

//FormHandler.vb
//It gets finished data for dropdowns. Search in FormHandler:
Dim dtTable As DataTable = GetDropDownListData(dtrRow) //and go there
//Find:
ReplaceIDsInLookupQuery() //- get values from layout lookupID

```

```ad-info
title: Useful request to get info:
collapse: open
```sql

//take id from the layout for dropdown and check:
select * from
dlookupquery d where id  ='d81726ca-332a-f057-fcd8-a379ab242c05';

//Check lookupqueryid for 
//'8b5ad40a-1ef5-a81e-8c96-9215fe5fa339' - lookup id for culumn
// from layout

select dl.id as SLQID,dl.query,schild."name", smain.layoutname 
from suilayoutfield schild 
join dlookupquery dl on dl.id = schild.lookupqueryid 
join suilayout smain on smain.layoutid = schild.layoutid 
	and dl.id != '8b5ad40a-1ef5-a81e-8c96-9215fe5fa339' 
	and schild."name" = 'StyleType' 
--and smain.layoutname = 'Download_TechPack_Search_SRMUSER';

-- And you can find other new id and placement of usage
```

See also
[[202109011156 Layout UPDATE]]