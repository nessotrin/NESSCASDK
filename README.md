# NESSCASDK
The NESSCASDK is a homemade SDK that allows to develop for Casio's Graph calculators.

With Calculib2, it allows for a simple make approach that get's the job done quickly, you just choose PC or Calc and it's done, either in binary format or .G1A.

Use "make -f MAKEFILE_NAME" with the right defines (look in the makefile) in the "Make" folder to compile your project (in the "Projects/YOUR_PROJECT/" folder), use Spassus2 as a template.

#How to use:
Requiered files from casio: Copy all the headers from Casio's SDK and put them in "CasioLib", it's requiered for PC and Calc.
(I'll look later how to include them without breaking Casio's license)

Run ./configure (to build Calculib2)

Go in Make and run "PROJECT_NAME=[YOUR_PROJECT_FOLDER_NAME] make -f [YOUR_CHOSEN_MAKEFILE]", optionally, add ADDIN_NAME and others with the right values. WARNING: Calc is currently broken !

Enjoy, the binary is in Projects/[YOUR_PROJECT_FOLDER_NAME]/build/addin for PC and build_calc/addin.g1A for Calc

#DEPENDENCIES
-SFML is requiered for Calculib2

-Clang is used by default, GCC will work too if you edit the makefile

#TODO:
-Calc compilation is badly broken

-Find a way to fuse fxlib.a and the homebrew .obj without breaking the license

#License
License is not set yet, GLPv2 is considered.
