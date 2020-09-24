# README:

Plugin for uploading data into a APEX_COLLECTION. Then edit and save the collection data without programming pl/sql code.

**Purpose**: Upload CSV data via copy and paste or via file upload.
The optional first line of the input (file) and the currency symbols will be removed from the input.
The plugin process copies the data into new rows in the named apex collection. 
The character columns C001 - C050 of the apex collection will contain the data in the the corresponding rows and columns from the input.

Now you can access and update forms and interactive grids that are based on an APEX_COLLECTION without additional PL/SQL code.
## Usage in IG:
Create an IG Region based on a SQL Query :
	select COLLECTION_NAME,
		   SEQ_ID,
		   C001,
		   C002,
		   C003,...
	from V_APEX_COLLECTIONS
	where COLLECTION_NAME = 'IMPORTED_DATA'
	
When the Region is created change some attributes:
1. Column 'COLLECTION_NAME'
	Type : Hidden
	Query Only 	: No 
	Primary Key : No 
	Default 
		Type : Static
		Static Value : IMPORTED_DATA
		
2. Column 'SEQ_ID' 
	Query Only : Yes,
	Primary Key : Yes 
	
3. Process  - Save Interactive Grid Data
	Prevent Lost Updates : No,  
	Lock Row : No,  
	Return Primary Key(s) after Insert : No 

This sample application demonstrates the usage of the plugin and the view v_apex_collections in an updatable interactive grid.
No pl/sql code is required to perform the DML operations.

----------
## Installation 

The package upload_to_collection_plugin has to be installed in the application schema. 
execute the file upload_to_collection_plsql_code.sql and v_apex_collections.sql to install the required database objects.
You can add the file to the installation script of you application.

A demo of the plugin can be found here: 
https://apex.oracle.com/pls/apex/f?p=103003:LOGIN_DESKTOP
