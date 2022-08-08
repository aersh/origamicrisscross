# Supporting files for manuscript "Multi-micron crisscross structures grown from DNA-origami slats"

## Megastructure design scripts

**Note:** these files are provided as-is to aid with the design of typical crisscross origami megastructures.

1. ```input_example.xlsx```
A null spreadsheet containing a sheet for the x- and y- slats of the shape occupied with -1 or -2 in the cells. You can make the layout of slats here after conceiving the high-level design, e.g. pen-and-paper or in Illustrator.

2. ```kinetic_trap_design.ipynb```
* A random number matrix is generated to fill the null spreadsheet above. From the above null matrix, cells with -1 will be occupied with a random number from 1 to 32 to define a binding handle. Cells with -2 will be replaced with -1 after the random number assignment to indicate a control site with no handle. 
* This script then tests the various slats from the random number assignment for their Hamming distance (i.e. kinetic traps). You set a threshold trap strength and then the script keeps looping through (2) until it finds the appropriate set of numbers that allows for the desired trap. Note: depending on the size of the shape and the selected threshold, this can be quite slow, and certain traps might not be possible with the 32x depth library.
* The best matrix from the above script is then saved. Sometimes it might be worth stopping the loop and manually saving it. The distribution of kinetic traps can also be plotted.

3. ```generate_echo_instructions.ipynb```
To turn the optimized matrix into a .csv file that the Echo acoustic liquid handler can read, this script takes the various matrices, reads them into a series of 32 length number lists for each slat, looks up the sequence location in the plate library, and then writes it to a dataframe that will make the final pipette instructions.
