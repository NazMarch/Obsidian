#flexbricks 

Documentation of the design: 

https://reportpublisher.yuniquecloud.com/v1/v8_Style_Guide/documentation.html


## Create Portrait version of Existing 'Style Cover with Comments' Report

You can check your deployed reports by path in browser: 
http://localhost/reports/browse/

Or use Report Server Configuration Manager

When you create new .rdl file in datasets must be dataset `dsL10n`.

Parameters must be declared or named the same as in the query.

Views in database always starts with `rpx`

Reports name must have the part `LLT` or `PLT` that means landscape or portrait form.

To change size of form of report use Right Click of the mouse on the designer form and select `report properties` where you can set special form and size.

For usual reports in database names of the tables starts with `r` like `rreportitems`
For BI reports names starts from `rbi`.

Important Files for setup reports and for adding new reports are here:
- for usual reports `C:\YuniquePLM_Development\Reports\plmOnReports\SQL.Data\Report.Data.OOTB.sql`
- for BI `C:\YuniquePLM_Development\Reports\YuniqueBI\SQL.Data\Report.Data.OOTB.sql`

Open Style, then select reports, need to add new item in dropdown for a portrait report.

```ad-example
title: important tables
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

