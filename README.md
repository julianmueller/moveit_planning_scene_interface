This repository is used to understand and work with the MoveIt PlanningScene. To do so, the `.scene` file format was reverse engineered as good as possible.


- https://github.com/ros-planning/moveit/blob/master/moveit_core/planning_scene/src/planning_scene.cpp#L962
- https://github.com/ros-planning/geometric_shapes/blob/noetic-devel/src/shape_operations.cpp#L428

## Table of Contents

1. [Scene File](#scene-file)
2. [Box Shape](#box-shape)
3. [Cone Shape](#cone-shape)
4. [Cylinder Shape](#cylinder-shape)
5. [Sphere Shape](#sphere-shape)
6. [Plane Shape](#plane-shape)
7. [Mesh Shape](#mesh-shape)
8. [Multiple Shapes](#multiple-shapes)

## [Scene File][scene-file]

- in a scene file are multiple **objects**, each having its own name, pose and shapes
- a shape is some kind of primitive (box, cone, cylinder, sphere, mesh)
- one object can have multiple shapes inside of it

```
<SCENE_ID>
* <OBJECT_ID_1>
...
* <OBJECT_ID_2>
...
. # always end with a single lined dot and an empty line

```

example:

```
(noname)+
* Box_0
...
* Cone_0
...
.
```

## [Box Shape][box-shape]

```
* <BOX_OBJECT_ID>
<POS_X_OBJ>     <POS_Y_OBJ>     <POS_Z_OBJ>
<ROT_QX_OBJ>    <ROT_QY_OBJ>    <ROT_QZ_OBJ>    <ROT_QW_OBJ>
1 # Number of shapes
box
<X_SIZE>        <Y_SIZE>        <Z_SIZE>
<POS_X_SHAPE>   <POS_Y_SHAPE>   <POS_Z_SHAPE>
<ROT_QX_SHAPE>  <ROT_QY_SHAPE>  <ROT_QZ_SHAPE>  <ROT_QW_SHAPE>
# if the shape has a color
<COLOR_R_SHAPE> <COLOR_G_SHAPE> <COLOR_B_SHAPE> <COLOR_A_SHAPE>
# if not
0               0               0               0
0 # number of subframes
```

example:

```
* Box_0
-1.33 0 0
0 0 0 1
1
box
0.2 0.45 0.2
0 0 0
0 0 0 1
0 0 0 0
0
```

## [Cone Shape][cone-shape]

```txt
* <CONE_OBJECT_ID>
<POS_X_OBJ>     <POS_Y_OBJ>     <POS_Z_OBJ>
<ROT_QX_OBJ>    <ROT_QY_OBJ>    <ROT_QZ_OBJ>    <ROT_QW_OBJ>
1 # Number of shapes
cone
<RADIUS>        <LENGTH>
<POS_X_SHAPE>   <POS_Y_SHAPE>   <POS_Z_SHAPE>
<ROT_QX_SHAPE>  <ROT_QY_SHAPE>  <ROT_QZ_SHAPE>  <ROT_QW_SHAPE>
# if the shape has a color
<COLOR_R_SHAPE> <COLOR_G_SHAPE> <COLOR_B_SHAPE> <COLOR_A_SHAPE>
# if not
0               0               0               0
0 # number of subframes
```

example:

```
* Cone_0
0 -1.79 0
0 0 0 1
1
cone
0.325 0.2
0 0 0
0 0 0 1
0 0 0 0
0
```

## [Cylinder Shape][cylinder-shape]

```
* <CYLINDER_OBJECT_ID>
<POS_X_OBJ>     <POS_Y_OBJ>     <POS_Z_OBJ>
<ROT_QX_OBJ>    <ROT_QY_OBJ>    <ROT_QZ_OBJ>    <ROT_QW_OBJ>
1 # Number of shapes
cylinder
<RADIUS>        <LENGTH>
<POS_X_SHAPE>   <POS_Y_SHAPE>   <POS_Z_SHAPE>
<ROT_QX_SHAPE>  <ROT_QY_SHAPE>  <ROT_QZ_SHAPE>  <ROT_QW_SHAPE>
# if the shape has a color
<COLOR_R_SHAPE> <COLOR_G_SHAPE> <COLOR_B_SHAPE> <COLOR_A_SHAPE>
# if not
0               0               0               0
0 # number of subframes
```

example:

```
* Cylinder_0
0.77 0.55 0
0 0 0 1
1
cylinder
0.425 0.2
0 0 0
0 0 0 1
0 0 0 0
0
```

## [Sphere Shape][sphere-shape]

```
* <SPHERE_OBJECT_ID>
<POS_X_OBJ>     <POS_Y_OBJ>     <POS_Z_OBJ>
<ROT_QX_OBJ>    <ROT_QY_OBJ>    <ROT_QZ_OBJ>    <ROT_QW_OBJ>
1 # Number of shapes
sphere
<RADIUS>
<POS_X_SHAPE>   <POS_Y_SHAPE>   <POS_Z_SHAPE>
<ROT_QX_SHAPE>  <ROT_QY_SHAPE>  <ROT_QZ_SHAPE>  <ROT_QW_SHAPE>
# if the shape has a color
<COLOR_R_SHAPE> <COLOR_G_SHAPE> <COLOR_B_SHAPE> <COLOR_A_SHAPE>
# if not
0               0               0               0
0 # number of subframes
```

example:

```
* Sphere_0
0.71 0 0
0 0 0 1
1
sphere
0.325
0 0 0
0 0 0 1
0 0 0 0
0
```

## [Plane Shape][plane-shape]

```
* <PLANE_OBJECT_ID>
<POS_X_OBJ>     <POS_Y_OBJ>     <POS_Z_OBJ>
<ROT_QX_OBJ>    <ROT_QY_OBJ>    <ROT_QZ_OBJ>    <ROT_QW_OBJ>
1 # Number of shapes
plane
<A>             <B>             <C>             <D>
<POS_X_SHAPE>   <POS_Y_SHAPE>   <POS_Z_SHAPE>
<ROT_QX_SHAPE>  <ROT_QY_SHAPE>  <ROT_QZ_SHAPE>  <ROT_QW_SHAPE>
# if the shape has a color
<COLOR_R_SHAPE> <COLOR_G_SHAPE> <COLOR_B_SHAPE> <COLOR_A_SHAPE>
# if not
0               0               0               0
0 # number of subframes
```

example:

```
* Plane_0
0 0 0
0 0 0 1
1
plane
1 2 3 4
0 0 0
0 0 0 1
0 0 0 0
0
```


## [Mesh Shape][mesh-shape]

```
* <MESH_OBJECT_ID>
<POS_X_OBJ>     <POS_Y_OBJ>     <POS_Z_OBJ>
<ROT_QX_OBJ>    <ROT_QY_OBJ>    <ROT_QZ_OBJ>    <ROT_QW_OBJ>
1 # Number of shapes
mesh
<VERTEX_COUNT>  <TRANGLE_COUNT> 
<VERTEX_0_X>    <VERTEX_0_Y>    <VERTEX_0_Z>
<VERTEX_1_X>    <VERTEX_2_Y>    <VERTEX_3_Z>
...
<TRIAG_0_V1>    <TRIAG_0_V2>    <TRIAG_0_V3>
<TRIAG_1_V1>    <TRIAG_1_V2>    <TRIAG_1_V3>
...
<POS_X_SHAPE>   <POS_Y_SHAPE>   <POS_Z_SHAPE>
<ROT_QX_SHAPE>  <ROT_QY_SHAPE>  <ROT_QZ_SHAPE>  <ROT_QW_SHAPE>
# if the shape has a color
<COLOR_R_SHAPE> <COLOR_G_SHAPE> <COLOR_B_SHAPE> <COLOR_A_SHAPE>
# if not
0               0               0               0
0 # number of subframes
```

example:

```
* mesh_obj.stl_0
0 0 0
0 0 0 1
1
mesh
388 792
-1.14053 0.119852 0.0019
-1.14055 0.119852 0.0019
-1.14053 0.119852 0.002475
...
0 1 2
2 1 3
2 4 0
...
0 0 0
0 0 0 1
0 0 0 0
0
```


## Octree shape (not working yet)

```
* <OCTREE_OBJECT_ID>
<POS_X_OBJ>     <POS_Y_OBJ>     <POS_Z_OBJ>
<ROT_QX_OBJ>    <ROT_QY_OBJ>    <ROT_QZ_OBJ>    <ROT_QW_OBJ>
1 # Number of shapes
octree
# not sure yet how this works
<POS_X_SHAPE>   <POS_Y_SHAPE>   <POS_Z_SHAPE>
<ROT_QX_SHAPE>  <ROT_QY_SHAPE>  <ROT_QZ_SHAPE>  <ROT_QW_SHAPE>
# if the shape has a color
<COLOR_R_SHAPE> <COLOR_G_SHAPE> <COLOR_B_SHAPE> <COLOR_A_SHAPE>
# if not
0               0               0               0
0 # number of subframes
```

example:

```
* octree_0
?
```


## [Multiple Shapes][multiple-shapes]

- when an object has multiple shapes inside of it, it looks like this:

```
* <OBJECT_ID>
<POS_X_OBJ>     <POS_Y_OBJ>     <POS_Z_OBJ>
<ROT_QX_OBJ>    <ROT_QY_OBJ>    <ROT_QZ_OBJ>    <ROT_QW_OBJ>
3 # Number of shapes
box
<X_SIZE>        <Y_SIZE>        <Z_SIZE>
<POS_X_SHAPE>   <POS_Y_SHAPE>   <POS_Z_SHAPE>
<ROT_QX_SHAPE>  <ROT_QY_SHAPE>  <ROT_QZ_SHAPE>  <ROT_QW_SHAPE>
0               0               0               0
cylinder
<RADIUS>        <LENGTH>
<POS_X_SHAPE>   <POS_Y_SHAPE>   <POS_Z_SHAPE>
<ROT_QX_SHAPE>  <ROT_QY_SHAPE>  <ROT_QZ_SHAPE>  <ROT_QW_SHAPE>
0               0               0               0
sphere
<RADIUS>
<POS_X_SHAPE>   <POS_Y_SHAPE>   <POS_Z_SHAPE>
<ROT_QX_SHAPE>  <ROT_QY_SHAPE>  <ROT_QZ_SHAPE>  <ROT_QW_SHAPE>
0               0               0               0
0 # number of subframes
```

