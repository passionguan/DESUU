This is the Readme file for DESUU tool.


About the software framework tool
--------------------------------------------------------------------------
DESUU: Design for Embedded Systems Under Uncertainties

Please refer to the following paper for details about the software framework tool:

Authors: Wenkai Guan, Milad Ghorbani Moghaddam, Dr. Cristinel Ababei
Paper Title: Uncertainties Aware Mapping for Embedded Systems for Reliability, Performance, and Power
Journal: International Journal of Embedded Systems (IJES)
Year: 2017
Status: Submitted

Note: The tool is compiled on a Linux machine running Ubuntu 14.04.
It is understood you are working on a linux machine.
---------------------------------------------------------------------------



Install prerequisites library
---------------------------------------------------------------------------
Before compling and running the framework, you need to first install libx11-dev on your Linux Ubuntu machine. Please use the following command to install the package:

sudo apt-get install libx11-dev

Then, you may need to download the Boost library from this website:
https://sourceforge.net/projects/boost/files/boost/1.61.0/boost_1_61_0.tar.bz2/download

In the directory where you want to put the Boost installation, execute:

tar --bzip2 -xf /YOUR_PATH_TO/boost_1_61_0.tar.bz2
(YOUR_PATH_TO is the path you want to store the Boost)

For more information about Boost, please refer to: 

http://www.boost.org/doc/libs/1_61_0/more/getting_started/unix-variants.html
---------------------------------------------------------------------------



How to compile and run the program
---------------------------------------------------------------------------
Makefile has been provided for compiling the program on linux (and unix-like)
systems. Edit the "CLASSDIR", "INCDIRS" and "BOOST" base on your own path.

CLASSDIR: The path you store the DESUU tool. For instance, if you store the tool in /home/passionguan/Downloads/DESUU , then edit CLASSDIR = /home/passionguan/Downloads/DESUU

INCDIRS: The path to the include headfiles. The headfiles are stored in the "include" file inside DESUU, so you should set INCDIRS = $(CLASSDIR)/include

BOOST: The path to the BOOST library. For instance, if you store the BOOST library in /home/passionguan/Downloads/DESUU/include/boost_1_61_0 , then set BOOST = -I/home/passionguan/Downloads/DESUU/include/boost_1_61_0

Please use the command "make" in the terminal to compile all the source files. Then you will get the executable file named "desuu".

Usage: ./desuu random_seed < input_file.in
Example: ./desuu 0.5 < input_data/test.in
Explanation: desuu is the executable file; random_seed is a real number in (0,1) which is used as a seed for random number generator; input_file.in is the file that stores all the input parameters. You can also use "./desuu random_seed" to set the parameters in the terminal.

NOTE: we have used the open source nsga2 algorithm code from Dr. Kalyanmoy Deb.
---------------------------------------------------------------------------



About the output files
--------------------------------------------------------------------------
best_pop.out: This file contains the best solutions obtained at the end of simulation run.
inial_pop.out: This file contains all the information about initial population.
final_pop.out: This file contains the data of final population.
all_pop.out: This file containts the data of populations at all generations.
params.out: This file contains the information about input parameters as read by the program.

The best_pop.out file contains all the non-dominate solutions, which consist of the Pareto frontier.
--------------------------------------------------------------------------


About the input parameters
---------------------------------------------------------------------------
popsize: This variable stores the population size (a multiple of 4);
ngen: Number of generations;
nobj: Number of objectives;
ncon: Number of constraints;
nreal: Number of real variables;
min_realvar[i]: minimum value of i^{th} real variable;
max_realvar[i]: maximum value of i^{th} real variable;
pcross_real: probability of crossover of real variable;
pmut_real: probability of mutation of real variable;
eta_c: distribution index for real variable SBX crossover;
eta_m: distribution index for real variable polynomial mutation;
nbin: number of binary variables;
nbits[i]: number of bits for i^{th} binary variable;
min_binvar[i]: minimum value of i^{th} binary variable;
max_binvar[i]: maximum value of i^{th} binary variable;
pcross_bin: probability of crossover for binary variable;
pmut_bin: probability of mutation for binary variable;
---------------------------------------------------------------------------



Please feel free to send questions/comments/doubts/suggestions/bugs and etc.to 

wenkai.guan@marquette.edu
cristinel.ababei@marquette.edu
---------------------------------------------------------------------------
