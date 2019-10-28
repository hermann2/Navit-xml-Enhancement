# Navit-xml-Enhancement
Extension to Navit.xml

Display 1920x1080 5" (Galaxy S4 ANDROID does not work anymore with own Navit.xml).

created to 2560x1440 Galaxy S7 Other display see - table - Format.pdf 

Icons are in folder - src - enclosed. The empty folder in (routing mask) can be replaced/fill with this or own.

Installation:
Path in Device Memory --> Folder navit ; Add File: gui_internal.txt ;  Add Sub Folder: maske ;  poi ;  txt ; (Heard) 
Path in SDcard to Map --> Folder navit 

If the map is in the device memory then change in Navit.xml the Path under

mapset

	map type="textfile" active="yes" data="$NAVIT_USER_DATADIR/Your_Map_Name.bin"

