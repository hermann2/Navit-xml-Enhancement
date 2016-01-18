# Navit-xml-Enhancement
Extension to Navit.xml
created to display 1920x1080 5" (Galaxy S4 ANDROID). Other display see - table - Format.pdf 

XML compled includes choice of two routing masks Heard or Normal

Icons are in folder - src - enclosed. The empty folder in (routing mask) can be replaced/fill with this or own.

Installation:
Path in Device Memory --> Folder navit ; Add File: gui_internal.txt ;  Add Sub Folder: maske ;  poi ;  txt ; (Heard) 
Path in SDcard to Map --> Folder navit 

If the map is in the device memory then change in Navit.xml the Path under

mapset

	map type="textfile" active="yes" data="$NAVIT_USER_DATADIR/Your_Map_Name.bin"

