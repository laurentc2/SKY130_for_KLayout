##  Redundant Via insertion for SKY130 technology

Redundant vias may lead to 10X-100X smaller failure rate that single vias.
So, it is an important step after the place&route layout generation.
Unfortunately the OpenROAD cannot handle double vias usage at the moment.
Here a KLayout procedure for insertion of double vias for the SKY130 process, thanks Matthias for you help.

**drc_insert_redundant_via_SKY130.lydrc** is written to avoid any DRC error. 

I tested it on the sky130hd_jpeg.gds.gz layout - an example provided with OpenROAD - included in this directory.
On sky130hd_jpeg and sky130hs_gcd, it did not generate any DRC error.

For its generation with OpenROAD, I have added some file in the platforms/sky130hd directory :
 * layermap.txt
 * sky130hd_lib.cdl   (to generate the layout netlist to check my flow)
 * config.mk   (I only added the 2 lines 135 and 136)

---

An other early improvement before the redundant vias insertion is to use the script **drc_route_lines_sky130.lydrc** ... to avoid the vias !

If a line between 2 Metal1 lines is routed in Metal2 although it can be in Metal1 (without short-circuit or DRC error), changing it to Metal1 avoids 2 vias and improves the robustness of the layout to the back-end metallization process. Same with 2 Metal2 lines that are connected in Metal1 or Metal3, if the interconnection in Metal1 or Metal3 is changed to Metal2, it removes 2 vias in the routing. Ideally, this improvement should be done within OpenROAD.

You can try the script on sky130hd_jpeg.gds.gz layout :yum:

The risk with that last improvement is that long Metal lines may generate antenna DRC errors - I did not notice it on my experiments. 

The advantage is that it avoids the resistance of the vias and decreases the RC of the wire and so increase the circuit speed. If you use both metals, it further decreases the RC of the wire and further increases the circuit speed.
