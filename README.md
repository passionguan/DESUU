# Design of Embedded Systems Under Uncertainty (DESUU)

DESUU is a software framework tool that can generate the robust Pareto frontier in the objective space formed by reliability, performance, and energy consumption.

## Introduction

Due to technology downscaling, embedded systems have increased in complexity and heterogeneity. The increasingly large process, voltage, and temperature variations negatively affect the design and optimization process of these systems. These factors contribute to increased uncertainties that in turn undermine the accuracy and effectiveness of traditional design approaches. 

In order to solve this problem, we formulate the problem of uncertainty aware mapping for multicore embedded systems as a multi-objective optimization problem. We present a solution to this problem that integrates uncertainty models as a new design methodology constructed with Monte Carlo and evolutionary algorithms. 

![image](https://github.com/passionguan/DESUU/tree/master/Figures/fig_block_diagram.jpg)

The methodology is uncertainty aware because it is able to model uncertainties in design parameters and to identify robust design solutions that limit the influence of these uncertainties onto the objective functions. The proposed design methodology is implemented as a tool called DESUU that can generate the robust Pareto frontier in the objective space formed by reliability, performance, and energy consumption.

![image](https://github.com/passionguan/DESUU/blob/master/Figures/fig_5_percent_ABS_3D.jpg)

## How to use?

### Environment

We implement DESUU on a Linux machine running Ubuntu 14.04.

### Install prerequisites library

Before compiling and running the framework, you need to first install libx11-dev on your Linux Ubuntu machine. Please use the following command to install the package:

sudo apt-get install libx11-dev

Then, you may need to download the Boost library (recommended version 1.61)from this website:

https://sourceforge.net/projects/boost/files/boost/1.61.0/boost_1_61_0.tar.bz2/download

In the directory where you want to put the Boost installation, execute:

tar --bzip2 -xf /YOUR_PATH_TO/boost_1_61_0.tar.bz2
(YOUR_PATH_TO is the path you want to store the Boost)

For more information about Boost, please refer to: 

http://www.boost.org/doc/libs/1_61_0/more/getting_started/unix-variants.html

### How to compile and run the program

Makefile has been provided for compiling the program on Linux (and Unix-like) systems. Edit the "CLASSDIR", "INCDIRS" and "X11_INCLUDE" base on your own path.

CLASSDIR: The path you store the DESUU tool. For instance, if you store the tool in /home/passionguan/Downloads/DESUU , then edit CLASSDIR = /home/passionguan/Downloads/DESUU

INCDIRS: The path to the include headfiles. The headfiles are stored in the "include" file inside DESUU, so you should set INCDIRS = $(CLASSDIR)/include

BOOST: The path to the BOOST library. For instance, if you store the BOOST library in /home/passionguan/Downloads/DESUU/include/boost_1_61_0 , then set BOOST = -I/home/passionguan/Downloads/DESUU/include/boost_1_61_0

Please use the command "make" in the terminal to compile all the source files. Then you will get the executable file named "desuu".

Usage: ./desuu random_seed < input_file.in
Example: ./desuu 0.5 < input_data/test.in
Explanation: desuu is the executable file; random_seed is a real number in (0,1) which is used as a seed for random number generator; input_file.in is the file that stores all the input parameters. You can also use "./desuu random_seed" to set the parameters in the terminal.

NOTE: we have used the open source nsga2 algorithm code from Dr. Kalyanmoy Deb.

### About the input parameters

popsize: This variable stores the population size (a multiple of 4);

ngen: Number of generations;

nobj: Number of objectives;

ncon: Number of constraints;

nreal: Number of real variables;

min_realvar[i]: minimum value of i^{th} real variable;

max_realvar[i]: maximum value of i^{th} real variable;

pcross_real: The probability of crossover of the real variable;

pmut_real: the probability of mutation of the real variable;

eta_c: distribution index for real variable SBX crossover;

eta_m: distribution index for real variable polynomial mutation;

nbin: number of binary variables;

nbits[i]: number of bits for i^{th} binary variable;

min_binvar[i]: minimum value of i^{th} binary variable;

max_binvar[i]: maximum value of i^{th} binary variable;

pcross_bin: the probability of crossover for the binary variable;

pmut_bin: the probability of mutation for the binary variable;

### About the output files

initial_pop.out: This file contains all the information about initial population;

final_pop.out: This file contains the data of final population;

all_pop.out: This file contains the data of populations at all generations;

best_pop.out: This file contains the best solutions obtained at the end of simulation run;

params.out: This file contains the information about input parameters as read by the program;

The best_pop.out file contains all the non-dominate solutions, which consist of the Pareto frontier.


## Publications

If you want to know more detailed information, please refer to this paper:

W. Guan, M.G. Moghaddam, and C. Ababei, Uncertainty aware mapping of embedded systems for reliability, performance, and energy, IEEE Int. Symposium on Quality Electronic Design (ISQED), Santa Clara, CA, March 2018.

## Authors and Copyright

DESUU is developed in Marquette Embedded SystemS (MESS) Lab, Dept. of Electrical and Computer Engineering, Marquette University by Wenkai Guan (wenkai.guan@marquette.edu), Milad Ghorbani Moghaddam (milad.ghorbanimoghaddam@marquette.edu), Cristinel Ababei (cristinel.ababei@marquette.edu).

Copyright (C) 2018, MESS Lab, Marquette University.

