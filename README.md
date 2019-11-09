# Navit-xml-Enhancement
## Extension to Navit.xml ##


Created to 2560x1440 Galaxy S7

Icons are in folder - src - enclosed. The empty folder in (routing mask) can be replaced/fill with this or own.

Installation:
Path in Device Memory --> Folder navit ; Add File: gui_internal.txt ;  Add Sub Folder: maske ;  poi ;  txt ; (Heard) 
Path in SDcard to Map --> Folder navit 

If the map is in the device memory then change in Navit.xml the Path under

mapset

	map type="textfile" active="yes" data="$NAVIT_USER_DATADIR/Your_Map_Name.bin"

