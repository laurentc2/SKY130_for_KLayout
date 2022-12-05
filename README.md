# SKY130_for_KLayout

## KLayout (version 0.27 or higher) technology files for Skywater SKY130

 * SKY130.lyt   : technology and connections description
 * SKY130.lyp   : layers color and shape description
 * SkyWater SKY130 Design Rules.odt : SKY130 Design Rules in LibreOffice Writer format (compatible Word)
 * SkyWater SKY130 Layers Reference.odt : SKY130 layers description in LibreOffice Writer format (compatible Word)
 * drc/drc_sky130.lydrc : DRC script
 * lvs/lvs_sky130.lylvs : LVS script  (coming soon, so far only for MOSfet)
 * def-lef/layermap.txt : layermap for the import_def.rb file : need to add in the config.mk file a line :
`export GDS_LAYER_MAP = ../../../../$(PLATFORM_DIR)/layermap.txt`

Within KLayout, create the technolgy SKY130 by the menu : **[Tools]-[Manage Technologies]**  
Then press + at the bottom left, you will add a new technology that you can call : _SKY130_

Then, you can copy the file **SKY130.lyp**, **SKY130.lyt** and the 2 directories **drc** and **lvs** of that repository in your directory :  
`$HOME/.klayout/tech/SKY130  (under Linux)`  
`#HOMEDATA#/klayout/tech/SKY130  (under Windows)`

Due to few **SKY130 GDS** cases found and tested, the DRC/LVS files have not been extensively tested and still probably have bugs for some cases.
It was tested on the GDS and spice netlists of the LIB_CASES directory.
The more we can publish **SKY130 GDS** files, the better those DRC/LVS files.
At that stage, the GDS needs another checks before tape-out.
