# Navit-xml-Enhancement
## Extension to Navit.xml ##

Created to 2560x1440 Galaxy S7

Icons are in folder - src - enclosed. The empty folder in (routing mask) can be replaced/fill with this or own.

### Installation: ###

Path in Device Memory --> Folder navit; Add Sub Folder: maske; poi; txt; (Heard)

Path in SDcard to Map --> Folder navit

If the map is in the device memory then change in Navit.xml the Path under

	<mapset>
	map type="textfile" active="yes" data="$NAVIT_USER_DATADIR/Your_Map_Name.bin"
	..........
	</mapset>
#### Display of individual *Point of Interrest:* ####
(see /NAVIT_XML/2560x1440 XML Normal/Navit/**Navit.xml**)

After own idea the POI as "universal layer" create, they can be used in all layouts.

	<layer name="wintersport">
	<itemgra item_types="piste_downhill_novice" order="16-">		<polyline color="#00A00040" width="40"/><icon src="$NAVIT_USER_DATADIR/poi/skinovice" w="64" h="64" x="32" y="32"/>		<circle text_size="36" color="#00A000"/><text text_size="36" color="#00A000"/></itemgra>
	<itemgra item_types="piste_downhill_easy" order="16-">			<polyline color="#0000FF40" width="40"/><icon src="$NAVIT_USER_DATADIR/poi/skieasy" w="64" h="64" x="32" y="-32"/>		<circle text_size="36" color="#0000FF"/><text text_size="36" color="#0000FF"/></itemgra>
	<itemgra item_types="piste_downhill_intermediate" order="16-">	<polyline color="#FF000040" width="40"/><icon src="$NAVIT_USER_DATADIR/poi/skimediate" w="64" h="64" x="32" y="32"/>	<circle text_size="36" color="#E00000"/><text text_size="36" color="#E00000"/></itemgra>
	<itemgra item_types="piste_downhill_advanced" order="16-">		<polyline color="#00000040" width="40"/><icon src="$NAVIT_USER_DATADIR/poi/skiadvanced" w="64" h="64" x="32" y="-32"/>	<circle text_size="36" color="#000000"/><text text_size="36" color="#000000"/></itemgra>
	<itemgra item_types="piste_downhill_expert" order="16-">		<polyline color="#FFAA0040" width="40"/><icon src="$NAVIT_USER_DATADIR/poi/skiexpert" w="64" h="64" x="32" y="32"/>		<circle text_size="36" color="#FFAA00"/><text text_size="36" color="#FFAA00"/></itemgra>
	<itemgra item_types="piste_downhill_freeride" order="16-">		<polyline color="#FFFF0060" width="40"/><icon src="$NAVIT_USER_DATADIR/poi/skifreeride" w="64" h="64" x="32" y="-32"/>	<circle text_size="36" color="#000000"/><text text_size="36" color="#000000"/></itemgra>
	<itemgra item_types="piste_nordic" order="16-">					<polyline color="#CCFFFF" width="18"/><polyline color="#FFFFFF" width="10"/><polyline color="#CCFFFF90" width="5"/>	<text text_size="28" color="#8888FF"/><icon src="$NAVIT_USER_DATADIR/poi/langlauf" w="64" h="64" x="32" y="32"/><circle text_size="32" color="#8888FF"/></itemgra>
	<itemgra item_types="piste_nordic" order="16-">					<polyline color="#CCFFFF" width="30"/><polyline color="#FFFFFF" width="16"/><polyline color="#CCFFFF90" width="8"/>	<text text_size="36" color="#8888FF"/><icon src="$NAVIT_USER_DATADIR/poi/langlauf" w="64" h="64" x="32" y="32"/><circle text_size="32" color="#8888FF"/></itemgra>
	<itemgra item_types="footway_and_piste_nordic" order="16-">		<polyline color="#CCFFFF" width="30"/><polyline color="#FFFFFF" width="16"/><polyline color="#CCFFFF90" width="8"/>	<text text_size="36" color="#8888FF"/><icon src="$NAVIT_USER_DATADIR/poi/walknordic" w="64" h="64" x="32" y="32"/><circle text_size="32" color="#8888FF"/></itemgra>
	<itemgra item_types="poi_skiing" order="16-">					<icon src="skiing" w="64" h="64" x="32" y="32"/><circle text_size="32" color="#1A2A3A"/></itemgra>
	<itemgra item_types="lift_chair" order="16-">					<polyline color="#003663" width="6"/><icon src="$NAVIT_USER_DATADIR/poi/chair" w="96" h="96" x="48" y="0"/>			<text text_size="38" color="#944C00" background_color="#944C00"/><circle text_size="38" color="#944C00"/></itemgra>
	.........
	</layer>

In the respective **Layout**, the link to the "universal Layer" will be entered:

	<layer name="wintersport" 				ref="wintersport" active="0"/>
	<layer name="Android-POI-Icons-full" 	ref="Android-POI-Icons-full" active="0"/>
	<layer name="hikings" 					ref="hikings" active="0"/>
	<layer name="leisure" 					ref="leisure" active="0"/>
	<layer name="sport" 					ref="sport" active="0"/>
	............

any **OSD Button "[POI]"**

	<osd x="0" y="0" w="160" h="140"	font_size="650"		type="text" label="[POI]\n" command='gui.menu("#POI_Icons")' background_color="#FFFFFF00" align="0" text_color="#902080"/>

open the **GUI Menü "POI_Icons"**

![Image of GUI Menü "POI_Icons"](https://hermann2.github.com/Navit-xml-Enhancement/src/screencapture/131342_Navit.jpg)

and allows the POI compilation or all POIs to be activated / deactivated.

	<a name='POI_Icons'><text>POI-Auswahl</text>
	<img cond='navit.layout.layer[@name=="wintersport"].active==0'				src='gui_stop'		onclick='navit.toggle_layer("wintersport"),refresh()'><text>Wintersport</text></img>
	<img cond='navit.layout.layer[@name=="wintersport"].active==1'				src='gui_active' onclick='navit.toggle_layer("wintersport"),refresh()'><text>Wintersport</text></img>
	<img cond='navit.layout.layer[@name=="Android-POI-Icons-full"].active==0' 	src='gui_stop' onclick='navit.toggle_layer("Android-POI-Icons-full"),refresh()'><text>Gebäude</text></img>
	<img cond='navit.layout.layer[@name=="Android-POI-Icons-full"].active==1' 	src='gui_active' onclick='navit.toggle_layer("Android-POI-Icons-full"),refresh()'><text>Gebäude</text></img>
	<img cond='navit.layout.layer[@name=="hikings"].active==0'					src='gui_stop'	onclick='navit.toggle_layer("hiking_way");navit.toggle_layer("hikings");refresh()'><text>Wanderung</text></img>
	<img cond='navit.layout.layer[@name=="hikings"].active==1'					src='gui_active' onclick='navit.toggle_layer("hiking_way");navit.toggle_layer("hikings");refresh()'><text>Wanderung</text></img>
	<img cond='navit.layout.layer[@name=="leisure"].active==0'					src='gui_stop'	onclick='navit.toggle_layer ("leisure"),refresh()'><text>Freizeit</text></img>
	<img cond='navit.layout.layer[@name=="leisure"].active==1'					src='gui_active' onclick='navit.toggle_layer("leisure"),refresh()'><text>Freizeit</text></img>
	........
	<img src='zoom_in'	onclick='menu("#poi_on");back_to_map()'><text>ALLE an</text></img>
	<img src='zoom_out'	onclick='menu("#poi_off");back_to_map()'><text>ALLE aus</text></img>
	<-- menu("#poi_on") <script> automatically sets everything on/off -->

All "<itemgra item_types =" can be served. Brings overview and speed while scrolling the map.			