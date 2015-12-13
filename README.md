# routingnoxim
Routing Noxim
Adaptive routing algorithm for 3D NOCs


GO through the following files. These four files are what we must conern ourselves with 
1.NoximMain.h
2.NoximMain.cpp
3.NoximRouter.h
4.NoximRouter.cpp



pseudocode:
Traffic Distributing Adaptive Routing Algorithm

Input: Xdiff, Ydiff ,Zdiff
Output: Weight of each output direction

1:Xdiff = Xcurrent – Xdestination;
2:Ydiff = Ycurrent – Ydestination;
3:Zdiff = Zcurrent – Zdestination;

4:Weights of all directions are initialized to 0;

5: if (-1 <=Xdiff <=1 and  -1 <=Ydiff <=1  and -1 <=Zdiff <=1)  then
6:	 if (Zdiff > 0) then
7: 		Downport_weight = vertical_close
8: 	else if (Zdiff < 0 ) then
9: 		Upport_weight = vertical_close;
10: 	end if
11: 	if (Ydiff > 0) then
12: 		Southport_weight = horizontal_close;
13: 	else if (Ydiff < 0) then
14: 		Northport_weight = horizontal_close;
15: 	end if
16: 	if (Xdiff > 0) then
17: 		Eastport_weight = horizontal_close;
18: 	else if (Xdiff < 0) then
19: 		Westport_weight = horizontal_close;
20: 	end if
21: else
22: 	if (Zdiff > 0) then
23: 		Downport_weight = vertical_far;
24: 	else if (Zdiff < 0 ) then
25: 		Upport_weight = vertical_far;
26: 	end if
27: 	if (Ydiff > 0) then
28: 		Southport_weight = horizontal_far_min;
29: 		Northport_weight = horizontal_far_detour;
30: 	else if (Ydiff < 0) then
31: 		Northport_weight = horizontal_far_min;
32: 		Southport_weight = horizontal_far_detour;
33: 	end if
34: 	if (Xdiff > 0) then
35: 		Eastport_weight = horizontal_far_min;
36:		Westport_weight = horizontal_far_detour;
37: 	else if (Xdiff < 0) then
38: 		Westport_weight = horizontal_far_min;
39: 		Eastport_weight = horizontal_far_detour;
40: 	end if
41: end if

42: Traffic Condition = Free Buffer Space x Assigned Weight 

43: if (Xdiff, Ydiff, Zdiff) then
44:	Deliver packet to the local node and exit;
45: endif
46: else
47: 	for all candidate directions 
48:		choose the direction with maximum traffic flow value
49:		if (the direction with best traffic is unique) then
50:			return the direction
51:		else if (two or more directions are tied to be the best) then
52:			return the direction with biggest weight;
53:		endif
54:	end for


Modifications in the code

1.	Files to be modified:
A.	NoximMain.h
B.	NoximRouter.h
C.	NoximRouter.cpp

2.	Network Parameters set:

The parameters listed below are the only parameters whose values have been modified. All other values will remain set to default values set in the code.

DEFAULT_MESH_DIM_X                       8				 DEFAULT_MESH_DIM_Y                       8
DEFAULT_MESH_DIM_Z                       4			
DEFAULT_ROUTING_ALGORITHM                ROUTING_TDAR



