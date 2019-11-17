# Navit-xml-Enhancement
## Extension to Navit.xml ##

Created to 2560x1440 Galaxy S7 with navit-git 0.5.3+589c11d0  
Icons are in folder - src - enclosed. The empty folder in (routing mask) can be replaced/fill with this or own.  
### Installation:  
Path in Device Memory --> Folder navit; Add Sub Folder: maske; poi; txt; (Heard)  
Path in SDcard to Map --> Folder navit  
If the map is in the device memory then change in Navit.xml the Path under

	<mapset>
	map type="textfile" active="yes" data="$NAVIT_USER_DATADIR/Your_Map_Name.bin"
	..........
	</mapset>

![](https://github.com/hermann2/Navit-xml-Enhancement/blob/master/src/screencapture/003437_Navit.jpg)
![](https://github.com/hermann2/Navit-xml-Enhancement/blob/master/src/screencapture/090030_Navit.jpg)
![](https://github.com/hermann2/Navit-xml-Enhancement/blob/master/src/screencapture/091006_Navit.jpg)

### Display of individual *Point of Interrest:*  
(see /NAVIT_XML/2560x1440 XML Normal/Navit/**Navit.xml**)  
After own idea the POI as "universal layer" create, they can be used in all layouts.

	<layer name="wintersport">
	<itemgra item_types="piste_downhill_novice" order="16-">	<polyline color="#00A00040" width="40"/><icon src="$NAVIT_USER_DATADIR/poi/skinovice" w="64" h="64" x="32" y="32"/>	<circle text_size="36" color="#00A000"/><text text_size="36" color="#00A000"/></itemgra>
	<itemgra item_types="piste_downhill_easy" order="16-">		<polyline color="#0000FF40" width="40"/><icon src="$NAVIT_USER_DATADIR/poi/skieasy" w="64" h="64" x="32" y="-32"/>	<circle text_size="36" color="#0000FF"/><text text_size="36" color="#0000FF"/></itemgra>
	<itemgra item_types="piste_downhill_intermediate" order="16-">	<polyline color="#FF000040" width="40"/><icon src="$NAVIT_USER_DATADIR/poi/skimediate" w="64" h="64" x="32" y="32"/>	<circle text_size="36" color="#E00000"/><text text_size="36" color="#E00000"/></itemgra>
	<itemgra item_types="piste_downhill_advanced" order="16-">	<polyline color="#00000040" width="40"/><icon src="$NAVIT_USER_DATADIR/poi/skiadvanced" w="64" h="64" x="32" y="-32"/>	<circle text_size="36" color="#000000"/><text text_size="36" color="#000000"/></itemgra>
	<itemgra item_types="piste_downhill_expert" order="16-">	<polyline color="#FFAA0040" width="40"/><icon src="$NAVIT_USER_DATADIR/poi/skiexpert" w="64" h="64" x="32" y="32"/>	<circle text_size="36" color="#FFAA00"/><text text_size="36" color="#FFAA00"/></itemgra>
	<itemgra item_types="piste_downhill_freeride" order="16-">	<polyline color="#FFFF0060" width="40"/><icon src="$NAVIT_USER_DATADIR/poi/skifreeride" w="64" h="64" x="32" y="-32"/>	<circle text_size="36" color="#000000"/><text text_size="36" color="#000000"/></itemgra>
	<itemgra item_types="piste_nordic" order="16-">			<polyline color="#CCFFFF" width="18"/><polyline color="#FFFFFF" width="10"/><polyline color="#CCFFFF90" width="5"/>	<text text_size="28" color="#8888FF"/><icon src="$NAVIT_USER_DATADIR/poi/langlauf" w="64" h="64" x="32" y="32"/><circle text_size="32" color="#8888FF"/></itemgra>
	<itemgra item_types="piste_nordic" order="16-">			<polyline color="#CCFFFF" width="30"/><polyline color="#FFFFFF" width="16"/><polyline color="#CCFFFF90" width="8"/>	<text text_size="36" color="#8888FF"/><icon src="$NAVIT_USER_DATADIR/poi/langlauf" w="64" h="64" x="32" y="32"/><circle text_size="32" color="#8888FF"/></itemgra>
	<itemgra item_types="footway_and_piste_nordic" order="16-">	<polyline color="#CCFFFF" width="30"/><polyline color="#FFFFFF" width="16"/><polyline color="#CCFFFF90" width="8"/>	<text text_size="36" color="#8888FF"/><icon src="$NAVIT_USER_DATADIR/poi/walknordic" w="64" h="64" x="32" y="32"/><circle text_size="32" color="#8888FF"/></itemgra>
	<itemgra item_types="poi_skiing" order="16-">			<icon src="skiing" w="64" h="64" x="32" y="32"/><circle text_size="32" color="#1A2A3A"/></itemgra>
	<itemgra item_types="lift_chair" order="16-">			<polyline color="#003663" width="6"/><icon src="$NAVIT_USER_DATADIR/poi/chair" w="96" h="96" x="48" y="0"/>		<text text_size="38" color="#944C00" background_color="#944C00"/><circle text_size="38" color="#944C00"/></itemgra>
	.........
	</layer>  

In the respective **Layout**, the link to the "universal Layer" will be entered:

	<layer name="wintersport" 	ref="wintersport" active="0"/>
	<layer name="Android-POI-Icons-full" 	ref="Android-POI-Icons-full" active="0"/>
	<layer name="hikings" 		ref="hikings" active="0"/>
	<layer name="leisure" 		ref="leisure" active="0"/>
	<layer name="sport" 		ref="sport" active="0"/>
	............

any **OSD Button "[POI]"**

	<osd x="0" y="0" w="160" h="140" font_size="650" type="text" label="[POI]\n" command='gui.menu("#POI_Icons")' background_color="#FFFFFF00" align="0" text_color="#902080"/>

open the **GUI Menü "POI_Icons"**

![Image of GUI Menü "POI_Icons"](https://github.com/hermann2/Navit-xml-Enhancement/blob/master/src/screencapture/131342_Navit.jpg)

and allows the POI compilation or all POIs to be activated / deactivated.

	<a name='POI_Icons'><text>POI-Auswahl</text>
	<img cond='navit.layout.layer[@name=="wintersport"].active==0'		src='gui_stop'	onclick='navit.toggle_layer("wintersport"),refresh()'><text>Wintersport</text></img>
	<img cond='navit.layout.layer[@name=="wintersport"].active==1'		src='gui_active' onclick='navit.toggle_layer("wintersport"),refresh()'><text>Wintersport</text></img>
	<img cond='navit.layout.layer[@name=="Android-POI-Icons-full"].active==0' src='gui_stop' onclick='navit.toggle_layer("Android-POI-Icons-full"),refresh()'><text>Gebäude</text></img>
	<img cond='navit.layout.layer[@name=="Android-POI-Icons-full"].active==1' src='gui_active' onclick='navit.toggle_layer("Android-POI-Icons-full"),refresh()'><text>Gebäude</text></img>
	<img cond='navit.layout.layer[@name=="hikings"].active==0'		src='gui_stop'	onclick='navit.toggle_layer("hiking_way");navit.toggle_layer("hikings");refresh()'><text>Wanderung</text></img>
	<img cond='navit.layout.layer[@name=="hikings"].active==1'		src='gui_active' onclick='navit.toggle_layer("hiking_way");navit.toggle_layer("hikings");refresh()'><text>Wanderung</text></img>
	<img cond='navit.layout.layer[@name=="leisure"].active==0'		src='gui_stop'	onclick='navit.toggle_layer ("leisure"),refresh()'><text>Freizeit</text></img>
	<img cond='navit.layout.layer[@name=="leisure"].active==1'		src='gui_active' onclick='navit.toggle_layer("leisure"),refresh()'><text>Freizeit</text></img>
	........
	<img src='zoom_in'	onclick='menu("#poi_on");back_to_map()'><text>ALLE an</text></img>
	<img src='zoom_out'	onclick='menu("#poi_off");back_to_map()'><text>ALLE aus</text></img>
	<-- menu("#poi_on") <script> automatically sets everything on/off -->

All "<itemgra item_types =" can be served. Brings overview and speed while scrolling the map.

### At high zoom level, show a world map or /*: ###

Required is an image (map) of maximum dimension 4096x4096 (*src/maske/worldimage.png*).  
The folder "src / poi`_`my / worldimage_EBENE.xcf" contains the world map for free design.  
*worldimage.txt* (Create as UTF-8 and Line Delimiters to Unix LF) File with coordinates (icon_src="different image names" label="any text") possibly information such as:

	31.626 22.3372	type=poi_customb label="Abu Simbel Temples" icon_src="abusimbel"
	1.5 42.5 	type=poi_customc label="Andorra" icon_src="country_ad"
	24.0 82.0 	type=poi_customd label="A R T I C  O C E A N"
	<!-- what else should be shown. Various icons according to personal imagination.
	necessarily EMPTY LINE -->
	type=image label="$NAVIT_USER_DATADIR/maske/worldimage.png"
	-180.0 85.0511
	180.0 85.0511
	-180.0 -85.0511

Enter this file under `<mapset>` with the corresponding path.

    <mapset>
    ......
    <map type="textfile" enabled="yes" active="yes" data="$NAVIT_USER_DATADIR/txt/worldimage.txt"/>
    </mapset>

A world map for 3D requires many map sections and a lot of memory. Below is an automatic switching in the OSD to switch from *zoom&gt;64* to *2D and Orientation North*. The parameters for "*pitch*", "*orientation*" are saved. If "zoom&lt;128" the default setting will be reset (3D and Orientation 360 degrees).

	<osd x="-1" y="-1" w="1" h="1" type="cmd_interface" update_period="1" command='zoom&gt;64
	?(get_int_var("zoom_gt")==0 
	  ?(set_int_var("is_pitch",pitch),pitch=0,set_int_var("is_orientation",orientation),orientation=0,set_int_var("zoom_gt",1))
	  :"")
	:(get_int_var("zoom_gt")==1 
	  ?(pitch=get_int_var("is_pitch"),orientation=get_int_var("is_orientation"),set_int_var("zoom_gt",0))
	  :""))'/>

Enter the world map in a <layout name=" order="any".

	<layer name="world_image"> <itemgra item_types="image" order="0-11"> <image/> </itemgra> </layer>
	<!-- In the "worldimage.txt" included (poi_custom*) are also included in the layout, possibly as a separate layer.
		 %s is placeholder for different Icon names -->
	<layer name="world_poly">
	<itemgra item_types="poi_customb" order="0-">	<icon src="$NAVIT_USER_DATADIR/maske/%s" w="96" h="96"/><circle text_size="32" color="#990099"/></itemgra>
	<itemgra item_types="poi_customc" order="0-11">	<icon src="%s" w="192" h="192" x="0" y="288"/><circle text_size="75" color="" background_color="#B00000"/></itemgra>
	<itemgra item_types="poi_customd" order="0-11">	<circle text_size="50" color="#008CC8" background_color="#40CCFF"/></itemgra>
	</layer>

### Center map to the cursor ###
    timeout="86400"				| seconds to wait at scroll bevore the map jumps back to the active vehicle
    type="text" label="TEXT"
    \n					| new line
						| or
    type="button" src="$NAVIT_USER_DATADIR/center_Cursor.png"
    command=				| click the item, Instruction is executed
    follow=1				| wait one second before map is refreshed
    zoom=4					| a given zoom level (2,4,8,16....)
    set_center_cursor()			| center the map back to the vehicle
    enable_expression			| If the expression is true show this OSD Item
    follow&gt;1				| More than one second before the map is refreshed
    &amp;&amp;				| UND Operator
    vehicle.position_valid			| GPS works
    background_color			| any color BB=Tranparency
    align="4"				| Text align to the left
    text_color				| any color

Example for entry under **OSD**

	<osd x="0" y="-560" w="290" h="290" font_size="940" type="text" label="CENTER\nCURSOR" command="follow=1; zoom=4; set_center_cursor()" enable_expression="follow&gt;1&amp;&amp;vehicle.position_valid" background_color="#56FF00BB" align="4" text_color="#000000"/>
