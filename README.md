# STUV

# Definition:
Needed to name this something, UV and ST coordinates (and to a degree MV) is our concern here and looking up urban dictionary the most upvoted definition for that sort of sums up to dumb blonde, so that seemed appropriate, so STUV: "expression used in computer graphics, image processing and computer vision to flag/tag data to avoid working in the wrong coordinates system so that stupid results are not produced when mapping the results of two bug-free perfectly accurate software.” 

If UV maps are to be used to exchange between applications, for example so important in rendering, then it appears the rendering sampling grid must be clearly specified.  How we do a simple sanity test for arbitrary app M to app N?

# TEST 1:
So a first simple test procedure we have been doing is to simply render a 1000x1000 pixel image putting a square aligned to the 4 corners of the render window (projection plane boundaries) in a 3D renderer context and simply put vertices color, position and uv at 0 and 1.0 (normalized) and expect all this is rendering the same ramp. Of course in non-square image ratio, position would be different (part of test 2).  In 3D renderer also for precaution comparing the RG_A output with the UV AOV (aux pass) as well. 1000x1000 in floating point allows us to look-up in image viewer the coordinates and pixel values which should match if 0,0 is bottom-left and if not a scale in Y of -100% is non-destructive.

So far, applying this to different renderers, we seemed to have 3 sampling grids in the wild (in pixel/raster coordinates),  testing 6 renders check at least one of each below): 

      1) 0 to Width=1.0,  
      2) 0 to Width-1.0, 
      3) 0.5 to Width – 0.5. 
      
We would like to name them but each word by itself is ambiguous.  So, we will use here the label UV (1.) to imply a scaling defined by the image width and height (U is function of Width, and V of Height) and the default UV ramp is inside the 0 to 1.0 “normalized” space and 0.5 is the center of frame. We can all agree that an Image lattice is 2. – and 3. Is label wise ambiguous. It obviously is related to mesh interpolation.  

Note from the point-of-view of a UV map, this is non-destructibly convertible using offset (add) and scale (mult):  Scaling 1. to 3. via scaling center,  offsetting 2. by 0.5 is 3.,   scaling 2. To 1. by mult…  We call here the enumerated type or simple arithmetic mapping, the base ST Mapping of the map. There are other elements of this definition (e.g. polar coordinates even) but in TEST 1 we just discuss sampling GRID.

We will add as we go (you can help us) scenes in different applications (and version) with a 32b float render (when an option).  Of course, the second part of this test is to see if one can bypass any color management process that transforms this data (including pre-multiplying a data pass).  Notes about that can be added in each test folder when relevant.

