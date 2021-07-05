# APEX-IR-Zip-Download
APEX processing plugin for downloading large APEX Interactive Reports as ZIP files.
In case you have to download very large reports from an APEX Instance that is 
running behind a web proxy server or in cases where you have to download reports 
with more rows than the technical limit allows you to use, you can use 
this plugin to successfully download these reports. 
File size up to 2 GB is supported for the compressed data. 
The Sample App can be installed in APEX 5 or higher.


Usage:
1. Install the plugin file process_type_plugin_com_strack-software_ir_zip_download.sql in your application.
2. add a Button to your Report region.
3. set the Button action to redirect and set the link to the current page with Request = 'ZIP_DOWNLOAD'
4. In the Rendering tab at pre-Rendering / Before Header you add a 'Process' of type 'plugin', choose the 'IR Zip Download' plugin.
    Set the Setting / Region Name to contain the title of the IR Region.
    Set Condition / Type to : REQUEST = Value, set Condition / Value to : ZIP_DOWNLOAD

The plugin performs the following steps:
1. Extract the query with APEX_IR.GET_REPORT
2. Bind the variables for filter conditions
3. Open cursor for query and load the rows
4. Convert to CSV. The parameters 'CSV Separator', 'CSV Enclosed By', and 'Filename' defined under Attributes / Download of the report region are recognized. The Enclosing character is only used, when a data value contains the 'CSV Separator', or newline character.
5. Convert to ZIP with APEX_ZIP.ADD_FILE. Up to 2GB of compressed data can be processed.
6. Start the download to the browser
