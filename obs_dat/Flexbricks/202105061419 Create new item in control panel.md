#flexbricks 

```ad-success
title: 1. Create control panel type
collapse: open

```sql
select * from public.pcontrolpaneltype;
--
INSERT INTO public.pcontrolpaneltype(
controlpaneltypeid,
controlpaneltypename, controlpaneltypedescription,
cuser,
cdate,
muser, 
mdate, 
active, 
sort, 
legacyid,
eav, 
vsmvisible)

VALUES(
'91299a75-34b8-4271-8e30-63bded48adfa',
'Boots',
'Boots',
'Admin 1',
'2021-04-29 11:45:25.354',
'Admin 1',
'2021-04-29 11:47:54.684',
1,
NULL,
NULL,
NULL,
0);


```


```ad-success
title: 2. Create control panel
collapse: open
```sql

INSERT INTO public.pcontrolpanel
(controlpanelid, controlpanelname, controlpaneldescription,
controlpanelorder, controlpanelidschema, controlpanelschema, 
controlpanelsearchschema, controlpaneltablename, controlpanelurl, 
controlpaneleditschema, spxlogicinsert, spxlogicupdate, 
controlpaneltypeid, controlpanelrepid, isdatavalidation,
sort, legacyid, controlpanelsortschema, controlpanelsortfield, eav)
VALUES(614, 'Boot Type', 'Boot type', 614, NULL, 
'Control_pBootType_Default.xml',
'Control_pBootType_Search.xml', 
'pboottype', 
'Control_Boots_BootType_List.aspx?CPID=614', 
'Control_pBootType_Edit.xml', NULL, NULL, 
'91299a75-34b8-4271-8e30-63bded48adfa', 
'8f652f47-40f8-4b09-ab06-aa1d453bb2d4', 
0, 0, NULL, NULL, 'SortOrder', NULL);


```

```ad-success
title: Create new layout
collapse: open
```xml
	<Table layoutname ="Control _pBootType _Default" name="pBootType" formcolumns="1" formsql="select * from pboottype" gridreadsql="select * from pboottype" gridsql="select * from pboottype" apisql="select * from pboottype" muisections="Misc Details" useradgrid="1" pagesize="10" gridheight="400" viewmode="ByRow" autosizeinreadmode="0" allowcolumnreordering="0" allowgrouping="0" allowsorting="1" allowmulticolumnsorting="0" frozencolumncount="1" allowkeyboardsupport="0" allowpaging="0" allowfiltering="0" allowscrolling="0" allowrowdraggingreadmode="0" allowrowdraggingeditmode="0" allowrowselect="1" allowmultirowselect="0" addcheckboxrowselectcolumnreadmode="0" addcheckboxrowselectcolumneditmode="0" apiwhereclause="" apiorderby="" datakeyfield="" sortorder="" repeatcolumns="" showalias="" border="" columnheight="" gridwidth="" table="" selectsql="" repeatdirection="" codecolumn="" idcolumn="" spacecolumn="" tablewidthmode="" itemstylecssclasseditmode="" alternatingitemstylecssclasseditmode="" imagesize="" lockfieldname="" locksql="" apicreatewhereclause="" formdisplay="" spreadsheetfilename_update="" height="" orderby="" isconfigurable="1" allowexpressions="0" expressionsreadonly="0" extraattributes="">
	<Column name="BootTypeID" column="1" order="000" alias="Type ID" pk="1" type="label" datatype="guid" enabled="0" visible="0" cellwidth="150px" gridorder="000" gridvisible="0" gridwidth="100" autopostback="0" addnullfield="1" filterfield="" linkedcol="" cssclass="" maxlength="" source="t" apidatatype="uniqueidentifier" dataformat="" defaultvalue="" readonly="0" filterfield2="" dateformat="" trackchange="1" aliascss="" filterfield3="" lock1="" lock2="" issystemrequired="1" skipdatatranslation="0" multiselectquery="" multiselectsavespx="" skiplabeltranslation="0" expression="" isaudit="0" attributeaccessmask="-1" lookupqueryid="" extraattributes="" />
  </Column>
  <Column name="BootTypeName" column="1" order="000" alias="Boot Type Name" pk="0" type="textbox" datatype="string" enabled="1" visible="1" cellwidth="150px" gridorder="001" gridvisible="1" gridwidth="200" autopostback="0" addnullfield="1" filterfield="" linkedcol="" cssclass="" maxlength="200" source="t" apidatatype="string" dataformat="" defaultvalue="" readonly="0" filterfield2="" dateformat="" trackchange="1" aliascss="" filterfield3="" lock1="" lock2="" issystemrequired="1" skipdatatranslation="0" multiselectquery="" multiselectsavespx="" skiplabeltranslation="0" expression="" isaudit="0" attributeaccessmask="-1" lookupqueryid="" extraattributes="">  
    <Validator class="Required" type="" minimum="2" maximum="50" text="Boot Type Name length between 2 - 50" dataformat="" validationexpression="" seqno="1" />
	</Column>
	
	<Column name="BootTypeKey" column="1" order="001" alias="Boot Type Key" pk="0" type="textbox" datatype="string" enabled="1" visible="1" cellwidth="150px" gridorder="002" gridvisible="1" gridwidth="75" autopostback="0" addnullfield="1" filterfield="" linkedcol="" cssclass="" maxlength="10" source="t" apidatatype="string" dataformat="" defaultvalue="" readonly="0" filterfield2="" dateformat="" trackchange="1" aliascss="" filterfield3="" lock1="" lock2="" issystemrequired="1" skipdatatranslation="0" multiselectquery="" multiselectsavespx="" skiplabeltranslation="0" expression="" isaudit="0" attributeaccessmask="-1" lookupqueryid="" extraattributes="">
  <Validator class="Required" type="" minimum="2" maximum="10" text="Boot Type Key length between 2 - 10" dataformat="" validationexpression="" seqno="1" />
  </Column>
  
  <Column name="BootTypeDesc" column="1" order="002" alias="Boot Type Description" pk="0" type="textbox" datatype="string" enabled="1" visible="1" cellwidth="150px" gridorder="003" gridvisible="1" gridwidth="75" autopostback="0" addnullfield="1" filterfield="" linkedcol="" cssclass="" maxlength="100" source="t" apidatatype="string" dataformat="" defaultvalue="" readonly="0" filterfield2="" dateformat="" trackchange="1" aliascss="" filterfield3="" lock1="" lock2="" issystemrequired="1" skipdatatranslation="0" multiselectquery="" multiselectsavespx="" skiplabeltranslation="0" expression="" isaudit="0" attributeaccessmask="-1" lookupqueryid="" extraattributes="">  
  <Validator class="Length" type="" minimum="2" maximum="100" text="Boot Type Key length between 2 - 100" dataformat="" validationexpression="" seqno="1" />
  </Column>
  
  <Column name="Active" column="1" order="003" alias="Active" pk="0" type="dropdownlist" datatype="query" enabled="1" visible="1" cellwidth="150px" gridorder="007" gridvisible="1" gridwidth="75" autopostback="0" addnullfield="0" filterfield="" linkedcol="" cssclass="" maxlength="" source="t" apidatatype="integer" dataformat="" defaultvalue="" readonly="0" filterfield2="" dateformat="" trackchange="1" aliascss="" filterfield3="" lock1="" lock2="" issystemrequired="1" skipdatatranslation="0" multiselectquery="" multiselectsavespx="" skiplabeltranslation="0" expression="" isaudit="0" attributeaccessmask="-1" lookupqueryid="8ff0a4fa-ac1d-dbeb-7be0-196ec2bb90c6" extraattributes="">
  <Validator class="dropdown" type="" minimum="" maximum="" text="Required" dataformat="" validationexpression="" seqno="1" />
  </Column>
  
  <Column name="MUser" column="1" order="004" alias="Modified By" pk="0" type="label" datatype="string" enabled="0" visible="1" cellwidth="150px" gridorder="005" gridvisible="1" gridwidth="75" autopostback="0" addnullfield="1" filterfield="" linkedcol="" cssclass="" maxlength="" source="t" apidatatype="string" dataformat="" defaultvalue="" readonly="0" filterfield2="" dateformat="" trackchange="1" aliascss="" filterfield3="" lock1="" lock2="" issystemrequired="1" skipdatatranslation="0" multiselectquery="" multiselectsavespx="" skiplabeltranslation="0" expression="" isaudit="1" attributeaccessmask="-1" lookupqueryid="" extraattributes="" />  
  </Column>
  <Column name="CUser" column="2" order="005" alias="Created By" pk="0" type="label" datatype="string" enabled="0" visible="1" cellwidth="150px" gridorder="004" gridvisible="1" gridwidth="75" autopostback="0" addnullfield="1" filterfield="" linkedcol="" cssclass="" maxlength="" source="t" apidatatype="string" dataformat="" defaultvalue="" readonly="0" filterfield2="" dateformat="" trackchange="1" aliascss="" filterfield3="" lock1="" lock2="" issystemrequired="1" skipdatatranslation="0" multiselectquery="" multiselectsavespx="" skiplabeltranslation="0" expression="" isaudit="1" attributeaccessmask="-1" lookupqueryid="" extraattributes="" />  
  </Column>
  
  <Column name="CDate" column="2" order="006" alias="Created Date" pk="0" type="label" datatype="datetime" enabled="0" visible="1" cellwidth="150px" gridorder="005" gridvisible="1" gridwidth="75" autopostback="0" addnullfield="1" filterfield="" linkedcol="" cssclass="" maxlength="" source="t" apidatatype="datetime" dataformat="" defaultvalue="" readonly="0" filterfield2="" dateformat="" trackchange="0" aliascss="" filterfield3="" lock1="" lock2="" issystemrequired="1" skipdatatranslation="0" multiselectquery="" multiselectsavespx="" skiplabeltranslation="0" expression="" isaudit="1" attributeaccessmask="-1" lookupqueryid="" extraattributes="" />  
  </Column>
  
  <Column name="MDate" column="2" order="007" alias="Modified Date" pk="0" type="label" datatype="datetime" enabled="0" visible="1" cellwidth="150px" gridorder="006" gridvisible="1" gridwidth="75" autopostback="0" addnullfield="1" filterfield="" linkedcol="" cssclass="" maxlength="" source="t" apidatatype="datetime" dataformat="" defaultvalue="" readonly="0" filterfield2="" dateformat="" trackchange="0" aliascss="" filterfield3="" lock1="" lock2="" issystemrequired="1" skipdatatranslation="0" multiselectquery="" multiselectsavespx="" skiplabeltranslation="0" expression="" isaudit="1" attributeaccessmask="-1" lookupqueryid="" extraattributes="" />
  </Column>
 </Table>
```

```ad-success
title: Create new web forms
collapse: open

In vs for current solution create web forms
```

