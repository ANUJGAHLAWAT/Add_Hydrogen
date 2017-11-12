# Add_Hydrogen
Add hydrogen to .PDB file in JAVA language

 
This is a program to add hydrogen atoms to the .cif file (a PDB file format), Generally, PDB file doesn't contain the hydrogen atom. But we have to add hydrogens to make the structure more informative.
we can write this program through two ways according to my gained knowledge I will explore how we can do so,

1. If we know distance and angle from the PDB atom then it easy to add hydrogen atom. We knew the standard distance between atoms
(C, N, O, S) and hydrogen. But a problem with the angle it hard to find it because it affected by the corresponding environment of PDB atom of PDB file. So, this idea didn't work out for me.
2. If we have reference atoms then we can move these atoms in space by subtracting reference atoms from PDB atoms coordinates. Let we have Nitrogen atom with coordinates (xr,yr,zr) and followed by two hydrogen atoms in the reference file, one of the hydrogen atom has coordinates (hx, hy, hz) in the reference file. We have corresponding coordinates of the Nitrogen atom(xp,yp,zp) in PDB file. then we subtract coordinates of Nitrogen from Reference and PDB file, it gives us the distance by which we must move the Hydrogen atom of the reference file, to add hydrogen to the PDB nitrogen atom.

d(sx, sy, sz)=coordinates of Nitrogen from reference - coordinates of PDB file Nitrogen
d(sx, sy, sz)=(xr-xp,yr-yp,zr-zp)

Assume by subtracting we get the coordinates d (sx, sy, sz). then we subtract same d coordinates from the hydrogen atom coordinates.

coordinates of the Hydrogen atom in PDB file= coordinates of Hydrogen in reference file -coordinates of d(sx, sy,sz).
coordinates of the Hydrogen atom in PDB file= (hx-sx, hy-sy, hz-sz)

In this way, hydrogen gets added to the PDB Nitrogen atom.

(The idea is mine even I can prove it. I haven't taken it from web or any document)

Next thing is to create Reference file:
  I had created reference file from Mole2 File of each individual amino acid. and in most of protein contain L-form of Amino Acid instead of D-form so, I had taken L- form of mole2 file for each amino acid. then I removed all the unnecessary information and instead of atom name used (A, B, G, D.....etc.) behind atom name. Here (A, B, G, D,..) represent Alpha, Beta, Gamma, Delta,... etc. a notation used in all PDB file. 
  I had taken only those atoms on which hydrogen atom present in mole2 file rest were excluded from the reference file. I had saved the reference file as amino acid.txt file in this program.

Now java code opens both files and starts comparing and adding Hydrogen atoms to corresponding atoms of PDB file from the reference file.

Future Plan:

1. using the same strategy we can check missing atoms in PDB.file, make a report of them and can be corrected.
2. we can also check the overlapping of the atoms in the PDB file.
3. we can also add new or delete existing amino acids in the PDB file as part of mutation in protein.

