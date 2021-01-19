# APEX-IR-Zip-Download
plugin for downloading of large APEX Interactive Reports as ZIP files.
In case you have to download very large reports from an APEX Instance that is running behind a web proxy server or in cases where you have to download reports with more rows than the technical limit allows you to use, you can use the plugin to successfully download these reports. The Sample App can be installed in APEX 5 or higher.


Usage:
1. Install the plugin file process_type_plugin_com_strack-software_ir_zip_download.sql in your application.
2. add a Button to your Report region.
3. set the Button action to redirect and set the link to the current page with Request = 'ZIP_DOWNLOAD'
4. In the Rendering tab at pre-Rendering / Before Header add a 'Process' of type 'plugin', choose the 'IR Zip Download' plugin.
    Set the Setting / Region Name to contain the title of the IR Region.
    Set Condition / Type to REQUEST = Value, set Condition / Value to ZIP_DOWNLOAD

The plugin performs the following steps:
1. extract the query with APEX_IR.GET_REPORT
2. bind the variables
3. Open cursor for query
4. convert to csv.
5. Convert to zip with APEX_ZIP.ADD_FIle
6. start the download to the browser
