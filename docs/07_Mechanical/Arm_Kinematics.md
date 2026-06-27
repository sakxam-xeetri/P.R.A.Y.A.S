# Arm Kinematics (3-DOF Planar/Spherical)

## Purpose
This document details the kinematic configurations for the 3-DOF robotic arms, providing equations for joint positioning.

## DH Parameters & Joint Coordinates
Each arm has 3 Degrees of Freedom (Shoulder Pitch, Elbow Pitch, Wrist Roll). We calculate forward kinematics using the link lengths:
*   Link 1 (Upper Arm, Shoulder to Elbow): $a_1 = 250	ext{ mm}$
*   Link 2 (Forearm, Elbow to Wrist): $a_2 = 220	ext{ mm}$

```
       (Shoulder Joint: q1)
               o
              / \ 
             /   \ 
            /     \ Link 1 (a1 = 250mm)
           /       \ 
          /         \ 
         /           o (Elbow Joint: q2)
        /             \ 
                       \ Link 2 (a2 = 220mm)
                        \ 
                         o (Wrist Joint: q3)
```

## Kinematic Equations
Assuming planar movement for simplicity during forward calculations, the coordinates of the wrist ($x, y$) relative to the shoulder joint are:

$$x = a_1 \cos(	heta_1) + a_2 \cos(	heta_1 + 	heta_2)$$
$$y = a_1 \sin(	heta_1) + a_2 \sin(	heta_1 + 	heta_2)$$

Where $	heta_1$ and $	heta_2$ represent the shoulder and elbow joint angles.
