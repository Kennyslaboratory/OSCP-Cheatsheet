# The Best OSCP Cheatsheet... Ever...
Footprinting, Reconocise, and Enumeration is the key to passing the OSCP.  

## Start Here
//Create Spreadsheet
spreadsheetObj = SpreadsheetNew('Names');
//Add Header Row
SpreadSheetAddRow(spreadsheetObj,'ID,Name');
//Add Data
SpreadSheetAddRow(spreadsheetObj,'1,Simon');
SpreadSheetAddRow(spreadsheetObj,'2,Carl');
//Format Header
SpreadsheetformatRow(spreadsheetobj,{bold=true,alignment='center'},1);
//Add Sheet
SpreadSheetcreateSheet(spreadsheetobj,'Towns');
//Switch to Names Sheet
SpreadsheetSetActiveSheet(spreadsheetobj,'Towns');
//Add Header Row
SpreadSheetAddRow(spreadsheetObj,'ID,Town');
//Add Data
SpreadSheetAddRow(spreadsheetObj,'1,Detroit');
SpreadSheetAddRow(spreadsheetObj,'2,Sheffield');
//Format Header
SpreadsheetformatRow(spreadsheetobj,{bold=true,alignment='center'},1);
//Write File
Spreadsheetwrite(spreadsheetobj,expandpath('myData.xls'),true);
