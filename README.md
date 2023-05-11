cFDAP v.0.1.0
=============

cFDAP is a command-line Linux tool for fitting FRAP/FDAP data.

The overall goal of cFDAP is to provide a fast and robust way to extract kinetic parameters from FRAP/FDAP data gathered from outgrowths of living neuronal cells. Nevertheless, the code can be relatively simply adapted to any experiment outline, which, in turn, requires theoretical expressions for FRAP(t)/FDAP(t) signals be hardcoded explicitly (for more details please read Igaev et al. (2015) Biophys. J. 107: 2567-2578).

New
===

 * 10.05.2023 ([dhesenkamp](https://github.com/dhesenkamp))
   
   Adapted code to work universally on 32-bit and 64-bit systems. Added instructions for compilation on MacOS with ARM chip architecture.

 * 30.08.2016

    A new option "-w" has been introduced which allows the user to choose
    between weighted and unweighted fitting.

 * 09.02.2016

    GSL 2.0 support has been implemented.

 * 13.09.2015

    Several bugs have been fixed. From now on, cFDAP and curve/error files
    must be located in the same folder.

 * 12.08.2015

    cFDAP now supports kinetic models with 1 and 2 fit parameters and
    calculates 95%, 97.5% and 99.9% confidence intervals.

Requirements
============

 To successfully compile cFDAP, you need to install the GNU Scientific Library
(http://www.gnu.org/software/gsl/). For Ubuntu/Debian, one needs to install gsl-bin
(binary package), libgsl2 (library package) and, optionally, libgsl-dev (development
package).

Compilation
===========

 ```
 cc cFDAP.c -o cFDAP -lgsl -lgslcblas -lm
 ```

##  On MacOS

 *NB*: instructions written for and tested on Macbook with M1 chip.

**Requirements**
 
 * Command line developer tools  
   `xcode-select --install`
* C compiler  
   Usually Clang and GCC are installed with command line tools, check whether properly installed with `clang --version` or `gcc --version`
* Homebrew  
   `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
   Verify installation with `brew doctor`
* MPICH and GSL packages  
   `brew install mpich`  
   `brew install gsl`
  
After installing all prerequisites, run

```sh
clang `pkg-config --libs --cflags gsl` cFDAP.c -o cFDAP
```

Compiled output file will appear in the folder in which the terminal session is open. Check executability with `file cFDAP`, it will give information on the type of architecture the file was compiled for (e.g. *Mach-O 64-bit executable arm64*).

Usage
=====

 To get quick start just run
 ```
 ./cFDAP
 ```

Copying
======

 cFDAP is licensed under a GPL license. That means that distributing the code is only
allowed under the same terms. 

TODO
====

 * statically linked GSL 2.0
 * cFDAP version for Windows 7
 * a simple GUI (preferably a Fiji plugin)
