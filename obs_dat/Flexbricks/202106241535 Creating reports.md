#flexbricks 

Documentation of the design: 

https://reportpublisher.yuniquecloud.com/v1/v8_Style_Guide/documentation.html


## Create Portrait version of Existing 'Style Cover with Comments' Report

```ad-example
title: useful tips
collapse: open
- You can check your deployed reports by path in browser: 
  http://localhost/reports/browse/ 
  
  Or use Report Server Configuration Manager
  
- When you create new .rdl file in datasets must be dataset `dsL10n`.
- Parameters for a .rdl file must be called as in the query which  generate query to report server.
- Views in database always starts with `rpx`
- Reports name must have eding of the name as `LLT` or `PLT` (landscape or portrait form)
- For usual plmOn reports in database name of the tables starts with `r` like `rreportitems`
- For BI reports name starts from `rbi`.

Important Files for setup reports and for adding new reports are here:
- for plmOn reports `C:\YuniquePLM_Development\Reports\plmOnReports\
SQL.Data\Report.Data.OOTB.sql.tmpl`
- for BI `C:\YuniquePLM_Development\Reports\YuniqueBI\
SQL.Data\Report.Data.OOTB.sql.tmpl`
```

```ad-example
title: useful tables
collapse: open
```sql

--for dropdowns in control panel
SELECT * FROM ptechpackcoverpage;
--for all reports
SELECT * FROM rreportitem;
--all types of reports as link for your report server
SELECT * FROM rreporttenantitem;
--all folders for reports that combine report
SELECT * FROM rreportfolders;
--IMPORTANT here you set rdl file for new report
SELECT * FROM rreportfiles;
--all path for report servers for enable users
SELECT * FROM sreportpath;
-- URL for servers that was installed
SELECT * FROM sreportserver; 

SELECT * FROM rreportfoldertypecoverpage
```


# Main part
Procedure of creating 
example YPLM-8584: 
Create Portrait version of Existing 'Style Cover with Comments' Report

- Go to `C:\YuniquePLM_Development\Reports\plmOnReports\
SQL.Data\Report.Data.OOTB.sql.tmpl` 
search in script the insert contains name 'Style Cover with Comments'.

- Take the identifier from the found row and make select: 

```sql
SELECT reportbodyfileid, reportheaderfileid, reportitemname, reportitemid 
FROM rreportitem WHERE 
reportitemid = 'ff8fb7de-eebd-41b9-b920-81ade6c00700';
```


- Look at reportbodyfileid, reportheaderfileid. Find them in the table:


### Finding names of executable .rdl files
```sql
SELECT * FROM rreportfiles 
WHERE id IN 
('9e2a47ce-f7f4-4af2-8abf-11419bd76b77',
 'a0ec0939-ecac-4b42-8f4a-8323ab0b9236');
```

Now you know the names of executable files. Let's go to Visual Studio and find them in solution explorer for project plmOnReports which is stored by path: `C:\YuniquePLM_Development\Reports\plmOnReports\*.sln`.

After you found file called `style_coversheet_wcomments_llt` make a copy and rename it as `style_coversheet_wcomments_plt`

You need to change page mode of the report to portrait. For this - call Right mouse click on free space and select `Report Properties` and select mode you need.

Actual sizes example for portrait form

![[page size.png]]

- After you select portrait mode - you need to correct size for all elements in designer

Elements like 'Modified by', 'Left image', 'Right image' you mustn't change

![[Example 1.png]]

- So now you need to change size for 'Comments', 'Cover page' placeholder,
<u>Style Comments</u> label and for label above

- If you don't have a window 'Properties' - you should call it by View->Properties Window (Ctr+W, P). Now you can set the actual size for selected element (look image below)
![[Set page size.png]]

- Let's make some calculations to know the size of each element


Width of portrait mode is 8.25in 
Size of 'Modified by' element must be 2.0in - Width, 0.25in - Height
- For 'Comments': 8.25 - 2.0 = 6.25in - Width, 0.25in - Height
- For 'Style Comments' set 8.25in - Width, 0.2in - Height
- For Cover page: 8.25 - 1.65(left picture) - 1.65(right picture) = 4.85in - Width
- For Label which contains grid: you can look example in Style_Coversheet_PLT
- For footer height must be 0.25in

Don't forget to check location of each element and ==Don't use mouse to move or replace elements==, it can makes wrong values of location.

Strongly recommended to check your finally values of size and location before finishing and look at other existing reports

- Now we need to correct SQL scripts to add your report before deploy

==Remember== You need correct only Report.Data.OOTB.sql.tmpl, otherwise your changes won't be applied

Go to `C:\YuniquePLM_Development\Reports\plmOnReports\SQL.Data\Report.Data.OOTB.sql.tmpl` 

There are inserts you need below.

### Table rreportfilestemp
```sql
-- here you set your executable .rdl, ID is unique
  insert into rreportfilestemp 
  (id, name, reportpathid) 
  values 
  ('9e2a47ce-f7f4-4af2-855f-11419bd76b77', 
  'style_coversheet_wcomments_plt', v_path_id); 
```

### Table rreportitemtemp
```sql
-- here you set value for Style-generate PDF list
-- you also connect your executable .rdl as a body and header as blank
insert into rreportitemtemp 
(reportitemid, desktopid, reportmapid, reportitemname, reportitemdescription, reportitemservertype, reportitemurl, reportitempkfield, reportitemsort, reportitemactive, reportitemsrmaccess, reportitemisworkflow, reportbodyfileid, reportheaderfileid) values ('ff8fb7de-eebd-41b9-b440-81ade6c00700', 8, '70000000-0000-0000-0000-000000000001', 'Style Cover with Comments Portrait', 'Style Cover', 'sql', '/reportredirect.aspx?rpid=##rpid##&sid=', 'styleid', '011', 1, 0, 0, '9e2a47ce-f7f4-4af2-855f-11419bd76b77', 'a0ec0939-ecac-4b42-8f4a-8323ab0b9236');
```


### Table techpackcoverpagetemp
```sql
  insert into techpackcoverpagetemp (customid, custom, customkey, customsort, active, cuser, cdate, muser, mdate, reportfileid) values ('f0000000-aaaa-bbbb-cccc-000000000008', 'Portrait Coverpage with Comments', null, 40, 1, 'System', now() at time zone 'utc', 'System', now() at time zone 'utc', '9e2a47ce-f7f4-4af2-855f-11419bd76b77');

```


### Table rreportfoldertypecoverpagetemp
```sql

--for dropdown in Controll panel->Tech Pack->Predefined Tech Pack 
  insert into rreportfoldertypecoverpagetemp (reportfoldertypeid, coverpageid) values ('00000000-0000-0000-0000-000000000001', 'f0000000-aaaa-bbbb-cccc-000000000008');

--for dropdown in Controll panel->Tech Pack->Predefined Sample Request Reports 
  insert into rreportfoldertypecoverpagetemp (reportfoldertypeid, coverpageid) values ('00000000-0000-0000-0000-000000000002', 'f0000000-aaaa-bbbb-cccc-000000000008');
  
```


For understanding ID-s like `00000000-0000-0000-0000-000000000002`
you can make a query to your database like:

```sql
SELECT * FROM rreportfoldertype;
```
