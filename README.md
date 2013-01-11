`rle-voxels`
=========

...is a Javascript library for working with narrowband level sets in 3D.  It is currently a work in progress, so expect this stuff to change over time.

Features for v0.1:

* Run length encoding for high performance and low memory cost
* Can perform dense sampling of implicit functions
* Isosurface extraction
* Point membership queries
* Boolean set operations (CSG)
* Morphological operations (dilation, erosion, etc.)
* Connected component labelling

Planned features:

* Triangular mesh to level set conversion
* Advection/upwind methods
* Eikonal solvers
* Transformation routines
* Fast single component level set extraction (marching methods)
* Ray casting tests
* Integral operations (Minkowski functionals, etc.)
* Collision tests

Installation
============

Via npm:

    npm install rle-voxels

And to use it:

    var rle = require("rle-voxels");
    var box = rle.sample([100, 100, 100], new Function("x",
          "return Math.min(Math.min(Math.abs(x[0]-50), Math.abs(x[1]-50)), Math.abs(x[2]-50)) - 30;"
        );
    var mesh = rle.surface(box);


How it works
============

Internally rle-voxels represents a volume as a list of runs sorted in colexicographic order.  This allows for efficient point membership queries and fast iteration.

Limitations
-----------

rle-voxels does not support efficient in place updates of volumes (though this may change in the future).  The reason for this is that there is no standard balanced binary search tree data structure for Javascript, and none of the implementations that I have seen so far are sufficiently mature, robust and performant for these sorts of data sets.

Documentation
=============

Here are some resources which explain how to use this library:

* [API](https://github.com/mikolalysenko/rle-voxels/blob/master/API.md)
* [Examples](https://github.com/mikolalysenko/rle-voxels/tree/master/examples)
* [WebGL Demo](http://mikolalysenko.github.com/)
* [Blog](http://0fps.wordpress.com)

Acknowledgements
================
(c) 2012-2013 Mikola Lysenko (mikolalysenko@gmail.com).  MIT License.
