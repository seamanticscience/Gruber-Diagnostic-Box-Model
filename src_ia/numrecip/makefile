# -------------------------------------------------------------------------
# FILE    : makefile
# AUTHOR  : Nicolas Gruber
# LAST REV: 05-AUG-96  adapted for program diag_boxmodel
#           17-SEP-99  adapted for SUN and interannual variability version
#                      special version for numrecip library part
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
!F_C      = lf95
#
F_FLAGS  = -C 

LFLAGS = -s

LIBNAME = libnumrecip.a
L = $(LIBNAME)

# -------------------------------------------------------------------------
# -- LOCATION OF INCLUDE FILES: (for directives like 'include filename')  
# -- example: ( I_PATH = /users/user_name/proj/include )  
# -------------------------------------------------------------------------

I_PATH = \
	 $(ROOT)/incl

O_FILES = \
	ran1.o\
	func.o\
	dfunc.o\
	f1dim.o\
	df1dim.o\
	frprmn.o\
	linmin.o\
	dbrent.o\
	mnbrak.o\
	cost_function.o\
	calc_hessian.o\
	invert_hessian.o\
	svdcmp.o\
	pythag.o\
	gasdev.o
#
H_FILES = \
	${I_PATH}/diagboxmod.h     \
	${I_PATH}/simulation.h     \
	${I_PATH}/gasex_params.h   \
	${I_PATH}/diffent_params.h \
	${I_PATH}/adv_params.h     \
	${I_PATH}/ncp_params.h     \
	${I_PATH}/c13_params.h     \
	${I_PATH}/harm_coeff.h     \
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
	${I_PATH}/conj_grad.h      \
	${I_PATH}/conj_grad_common.h \
	${I_PATH}/sg_params.h      \
	${I_PATH}/op_statistics.h  \
	${I_PATH}/mc_statistics.h  \
	${I_PATH}/monte_carlo.h    \
	${I_PATH}/mc_plot_slabs.h  \
	${I_PATH}/sensitivity.h  
#
# -------------------------------------------------------------------------
# -- LIBRARY OBJECTS
# -------------------------------------------------------------------------
#
LIBOBJ = \
	$(L)(ran1.o)\
	$(L)(func.o)\
	$(L)(dfunc.o)\
	$(L)(f1dim.o)\
	$(L)(df1dim.o)\
	$(L)(frprmn.o)\
	$(L)(linmin.o)\
	$(L)(dbrent.o)\
	$(L)(mnbrak.o)\
	$(L)(cost_function.o)\
	$(L)(calc_hessian.o)\
	$(L)(invert_hessian.o)\
	$(L)(svdcmp.o)\
	$(L)(pythag.o)\
	$(L)(gasdev.o)
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
	rm -f *.o *% core *.f
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
func.f : func.F  $(H_FILES)
func.o : func.f
#
dfunc.f : dfunc.F  $(H_FILES)
dfunc.o : dfunc.f
#
f1dim.f : f1dim.F
f1dim.o : f1dim.f
#
df1dim.f : df1dim.F
df1dim.o : df1dim.f
#
dbrent.f : dbrent.F
dbrent.o : dbrent.f
#
mnbrak.f : mnbrak.F
mnbrak.o : mnbrak.f
#
linmin.f : linmin.F
linmin.o : linmin.f
#
frprmn.f : frprmn.F
frprmn.o : frprmn.f
#
ran1.f : ran1.F
ran1.o : ran1.f
#
gasdev.f : gasdev.F
gasdev.o : gasdev.f
#
calc_hessian.f : calc_hessian.F $(H_FILES)
calc_hessian.o : calc_hessian.f
#
svdcmp.f : svdcmp.F
svdcmp.o : svdcmp.f
#
pythag.f : pythag.F
pythag.o : pythag.f
#
invert_hessian.f : invert_hessian.F 
invert_hessian.o : invert_hessian.f
#
cost_function.f : cost_function.F $(H_FILES)
cost_function.o : cost_function.f
#
$(L) : $(O_FILES)
