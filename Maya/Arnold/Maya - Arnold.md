# Maya - Arnold

ReferencePlane_STUV_Direct_place2dTexure_Arnold.mb

Render UV Plane using:
* Maya 2020
* Arnold: MtoA 4.0.0, Arnold Core 6.0.0.0

Images:
* .EXR 32 Bits, no compression
* Rendering settings:
	* Default, AA = 3
	* Preferences/Color Management: Enabled (default)
* AOVs:
	* Beauty
	* UV (Result is identical to the Beauty render)
		* aiUtility shader. Color Mode: UV Coords. Shade Mode: Flat
		* IMPORTANT: Set Render Settings > AOV > UV filter to either "closest" or "gaussian" 1x1
			* Default filter Gaussian 2x2 generates non full alpha pixels in the edges of the UV AOV render

Result Type: (3)- Mesh (0.5 to Width-0.5)
