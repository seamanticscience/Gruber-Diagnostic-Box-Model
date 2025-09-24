# -------------------------------------------------------------------------
# FILE    : makefile
# AUTHOR  : Nicolas Gruber
# LAST REV: 05-AUG-96  adapted for program diag_boxmodel
#           17-SEP-99  adapted for SUN and interannual variability version
#                      special version for plot library part
#           14-NOV-01  adapted for lf95
#
# -------------------------------------------------------------------------
#
# ----------------------------------------------------------------------
# -- Absolute path to the root directory of source code tree
# ----------------------------------------------------------------------
#

ROOT = /usr/local/pinus/home/gruber/diag_boxmod/src_ia

#
# ----------------------------------------------------------------------
# -- Colon separated list of directories which includes include files
#    and modules.
# ----------------------------------------------------------------------
#

DIRS = .:$(ROOT)/incl

#
# ----------------------------------------------------------------------
# -- Colon separated list of directories containing source code.
#    Directories will be searched in the order given
# ----------------------------------------------------------------------
#

SRC_DIRS = .

#
# ----------------------------------------------------------------------
# -- File containing list of CPP define directives
#    (default: $(ROOT)/ifdefs)
# ----------------------------------------------------------------------
#

include $(ROOT)/ifdefs

# -------------------------------------------------------------------------
# -- COMPILATION MACROS 
# -------------------------------------------------------------------------

F_C      = g77
#F_C      = lf95
#
F_FLAGS  = -C 

LFLAGS = -s

LIBNAME = libplot.a
L = $(LIBNAME)

# -------------------------------------------------------------------------
# -- LOCATION OF INCLUDE FILES: (for directives like 'include filename')  
# -- example: ( I_PATH = /users/user_name/proj/include )  
# -------------------------------------------------------------------------

I_PATH = \
	 $(ROOT)/incl

O_FILES = \
	generate_ncar_plots.o\
	plot_results.o\
	generate_mc_ncar_plots.o\
	calc_grid.o\
	bkgroundcolor.o\
	simplecolor.o
#
H_FILES = \
	${I_PATH}/diagboxmod.h     \
	${I_PATH}/simulation.h     \
	${I_PATH}/input.h          \
	${I_PATH}/slabs.h          \
	${I_PATH}/periods.h        \
	${I_PATH}/processes.h      \
	${I_PATH}/averages.h       \
	${I_PATH}/intval.h         \
	${I_PATH}/solution.h       \
	${I_PATH}/ncar.h           \
	${I_PATH}/plot_sets.h      \
	${I_PATH}/obs_values.h     \
	${I_PATH}/statistics.h     \
	${I_PATH}/mc_plot_slabs.h  
 
#
# -------------------------------------------------------------------------
# -- LIBRARY OBJECTS
# -------------------------------------------------------------------------
#
LIBOBJ = \
	$(L)(generate_ncar_plots.o)\
	$(L)(plot_results.o)\
	$(L)(generate_mc_ncar_plots.o)\
	$(L)(calc_grid.o)\
	$(L)(bkgroundcolor.o)\
	$(L)(simplecolor.o)

#
# -------------------------------------------------------------------------
# -- SET Default
# -------------------------------------------------------------------------
#
default: all
#
# -------------------------------------------------------------------------
# -- MAIN DEPENDENCY for library
# -------------------------------------------------------------------------
#
$(LIBNAME) : $(LIBOBJ)
	@echo ""
	@echo " *****************************"
	@echo " *** running ranlib        ***"
	@echo " *****************************"
	@echo ""
	ranlib $(LIBNAME)
	@echo ""
	@echo " *****************************"
	@echo " *** lib is now up to date ***"
	@echo " *****************************"
	@echo ""
library: all

all: FIRST_ACTION \
     $(LIBNAME) \
     LAST_ACTION

clean:
	@echo ""
	@echo " ***************************************"
	@echo " *** removing object files ***"
	@echo " ***************************************"
	@echo ""
	rm -f *.o *% core *.f *.a
#
small:
	@echo ""
	@echo " ***************************************"
	@echo " *** compressing .f and .r files     ***"
	@echo " ***************************************"
	@echo ""
	compress *.r *.f
#
big:
	@echo ""
	@echo " ***************************************"
	@echo " *** uncompressing .Z files"
	@echo " ***************************************"
	@echo ""
	uncompress *.Z
#
FIRST_ACTION:
	@echo ""
	@echo " ***************************************"
	@echo " *** UPDATING $(L) ***"
	@echo " ***************************************"
	@echo ""
 
LAST_ACTION:
	@echo ""
	@echo " *************"
	@echo " *** DONE. ***"
	@echo " *************"

	@echo ""
# -------------------------------------------------------------------------
# -- Default Rules and Suffixes
# -------------------------------------------------------------------------

.SUFFIXES:
.SUFFIXES: .a .o .f .F

.F.f: 
	@echo ""
	@echo " *** PREPROCESSING $<... ***"
	$(F_C) $(D_FLAGS) $(F_FLAGS) -I$(I_PATH) -E $< > $*.f 
#	$(F_C) $(D_FLAGS) $(F_FLAGS) -I$(I_PATH) -P $< -o $*.f

.f.o:   
	@echo ""
	@echo " *** COMPILING $<... ***"
	$(F_C) -c $(F_FLAGS) $*.f -o $*.o

.o.a:
	@echo ""
	@echo " *** ARCHIVING $<... ***"
	ar rv $(L) $*.o
#	rm -f $*.o


# -------------------------------------------------------------------------
# -- Dependencies (explicit) 
#          if you have include files in a subdirectory they must be 
#          indicated together with the path
# -------------------------------------------------------------------------
#
#
generate_ncar_plots.f : generate_ncar_plots.F $(H_FILES)
generate_ncar_plots.o : generate_ncar_plots.f
#
generate_mc_ncar_plots.f : generate_mc_ncar_plots.F $(H_FILES)
generate_mc_ncar_plots.o : generate_mc_ncar_plots.f
#
plot_results.f : plot_results.F $(H_FILES)
plot_results.o : plot_results.f
#
calc_grid.f : calc_grid.F
calc_grid.o : calc_grid.f
#
bkgroundcolor.f     : bkgroundcolor.F
bkgroundcolor.o     : bkgroundcolor.f
#
simplecolor.f : simplecolor.F
simplecolor.o : simplecolor.f
#
$(L) : $(O_FILES)
