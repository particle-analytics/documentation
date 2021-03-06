## Using Particle-Analytics with [LIGGHTS](http://www.cfdem.com/liggghts-open-source-discrete-element-method-particle-simulation-code)

Particle-Analytics can read [LIGGHTS](http://www.cfdem.com/liggghts-open-source-discrete-element-method-particle-simulation-code) dump files for processing. Some restrictions, in the structure of the files, apply and  are described below.  The import process is described in the [Converter Toolbox documentation](post_toolbox.md).

The dump files generated by [LIGGHTS](http://www.cfdem.com/liggghts-open-source-discrete-element-method-particle-simulation-code), for the particles, can have any selection of variables with no order imposed. However, to be processed in Particle-Analytics a minimum number of variables is required and the order is fixed. The same restrictions affect the [LIGGHTS](http://www.cfdem.com/liggghts-open-source-discrete-element-method-particle-simulation-code) particle-particle and particle-geometry contacts files

In the particles file, the filename must have the extension ".p". The variables in the command must
follow :
* *id*: column one
* *type*: column two
* *x,y,z*: columns three to five
* *vx,vy,vz*: columns nine to eleven
* *radius*: column eighteen

The rest of columns will be considered as user defined variables, and will be processed in that way.
An example of the [LIGGHTS](http://www.cfdem.com/liggghts-open-source-discrete-element-method-particle-simulation-code) dump command for the particles file is:

    dump Pfile all custom 400 dumpfile.p id type x y z ix iy iz vx vy vz fx fy fz \
      omegax omegay omegaz radius

The particle-particle contacts file must have the same name as the particles file, with the extension ".c".
In this file, just the IDs of particles in contact and forces will be read:
* id: IDs of particles in contact. Columns seven to nine
* fx,fy,fz: Contact forces. Columns two ten to twelve

The rest of the columns will not be considered.

In the case of the particle-geometry contact files, the filename must be the same as the particles file,
with the extension ".w". The rules for such files are similar to the particle-particle contact files, with a condition on the contact point position:
* *cx,cy,cz*: Contact point position. Columns one to three
* *id*: IDs of particles in contact. Columns seven to nine
* *fx,fy,fz*: Contact forces. Columns ten to twelve

An example of the [LIGGHTS](http://www.cfdem.com/liggghts-open-source-discrete-element-method-particle-simulation-code) dump command for both contact files is:

    compute cp all pair/gran/local
    compute cw all wall/gran/local
    dump Cfile all local 400 dumpfile.c c_cp[1] c_cp[2] c_cp[3] c_cp[4] c_cp[5] \
      c_cp[6] c_cp[7] c_cp[8] c_cp[9] c_cp[10] c_cp[11] c_cp[12]
    dump Wfile all local 400 dumpfile.w c_cw[1] c_cw[2] c_cw[3] c_cw[4] c_cw[5] \
      c_cw[6] c_cw[7] c_cw[8] c_cw[9] c_cw[10] c_cw[11] c_cw[12]

