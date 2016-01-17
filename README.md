# Navit-xml-Enhancement
Extension to Navit.xml
created to display 1920x1080 5" (Galaxy S4 ANDROID). Other display see - table - Format.pdf 

XML compled includes choice of two routing masks Heard or Normal

Icons are in folder - src - enclosed. The empty folder in (routing mask) can be replaced/fill with this or own.

Installation:
Path in Device Memory --> navit; Add: gui_internal.txt; Add Sub Folder: maske; poi; txt; (Heard) 
Path in SDcard to Map --> navit; 

If the map is in the device memory then change in Navit.xml the Path under
<mapset>
	<map type="binfile" active="yes" data="/sdcard/navit/Your_Map_Name.bin" />

