I expect everyone to know how to handle pbo's and getting scripts on your server so i wont explain this.

Installation:

-Database
	-import the _sql\sneak_customs.sql into your database
	-add the content of _sql\sneak_exile.ini at the end of your exile.ini (@ExileServer\extDB\sql_custom_v2\exile.ini)

-Serverside
	-compile as pbo and add to your server in: @ExileServer\addons

-mpmissions
	-add the mpmissions folder to your server
	-open the config.cpp and add 

ExileClient_gui_vehicleCustomsDialog_event_onPurchaseButtonClick = "overrides\ExileClient_gui_vehicleCustomsDialog_event_onPurchaseButtonClick.sqf";

		ExileClient_gui_vehicleCustomsDialog_event_onSkinListBoxSelectionChanged = "overrides\ExileClient_gui_vehicleCustomsDialog_event_onSkinListBoxSelectionChanged.sqf";

		ExileClient_gui_vehicleCustomsDialog_event_onVehicleDropDownSelectionChanged = "overrides\ExileClient_gui_vehicleCustomsDialog_event_onVehicleDropDownSelectionChanged.sqf";

		ExileClient_gui_vehicleCustomsDialog_show = "overrides\ExileClient_gui_vehicleCustomsDialog_show.sqf";

		ExileClient_gui_vehicleCustomsDialog_updateVehicle = "overrides\ExileClient_gui_vehicleCustomsDialog_updateVehicle.sqf";

	in class CfgCustomCode
	note: if you want to open the menu with a different key, this is the place to go.
	also add #include "addons\sneak_customs\SneakCustoms_config.cpp" at the top of your config.cpp

	-add 
		class SneakCustoms_change_skin {allowedTargets = 2;};
	to CfgRemoteExec -> CfgFunctions
	(description.ext)

-Battleye
	-im still working this out you can try everything when battleye is off, pls contact me
	if you have expierince with Battleye! (sneakcustoms@gmail.com)

Questions, bugreports or suggestions to:
sneakcustoms@gmail.com

How to use:
Just go to the standard vehicle customs trader and have fun!

How this works:
Everytime you change a skin the script will look up if its an custom skin or an exile standard.
When its standard it will just update the texture and the skinclass in the database.
When you apply a new custom skin it will add an entry to the sneak_customs database.
On server start the fn_Sneak_postInit.sqf will compare every spawned vehicle with my custom
database and update the skin to make custom skins persistent. When you revert back to a standard skin the entry in the custom databse will be deleted and value is stored in the standard database.