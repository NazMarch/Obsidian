#flexbricks 

```ad-info
title: For creating new tabs in Control panel
collapse: open
During you create new items in control panel you must use database
for different operations and working your system

- pcontrolpaneltype - has info about <b>main</b> tabs in control
panel like: Workflows, Case etc.

- pControlPanel - has info about <b>subtabs</b> of control panel tabs
like: types of Workflows, Color class etc.

- dlookupquery - has info about queries for XML layouts
For example let's look at xml column below:

For lookupqueryid="8ff0a4fa-ac1d-dbeb-7be0-196ec2bb90c6"
there is a row in database ``dlookupquery`` with select query 
for table ``pActive``

Just select 

``select * from dlookupquery 
where id = '8ff0a4fa-ac1d-dbeb-7be0-196ec2bb90c6'``



```


##### example xml
```xml
<Column 

name="Active" column="1" order="003" alias="Active" pk="0" type="dropdownlist" datatype="query" 
enabled="1" visible="1" cellwidth="150px" gridorder="007" gridvisible="1" gridwidth="75"
autopostback="0" addnullfield="0" filterfield="" linkedcol="" cssclass="" maxlength=""
source="t" apidatatype="integer" dataformat="" defaultvalue="" readonly="0" 
filterfield2="" dateformat="" trackchange="1" aliascss="" filterfield3="" lock1="" lock2="" 
issystemrequired="1" skipdatatranslation="0" multiselectquery="" multiselectsavespx="" skiplabeltranslation="0"
expression="" isaudit="0" attributeaccessmask="-1" 
lookupqueryid="8ff0a4fa-ac1d-dbeb-7be0-196ec2bb90c6" extraattributes="">
</Column>

```
