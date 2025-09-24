# -------------------------------------------------------------------------
# FILE    : makefile
# AUTHOR  : Nicolas Gruber
# LAST REV: 05-AUG-96  adapted for program diag_boxmodel
#           17-SEP-99  adapted for SUN and interannual variability version
#                      special version for chem library part
#           14-NOV-01  adapted for lf95
#
# -------------------------------------------------------------------------
#
# ----------------------------------------------------------------------
# -- Absolute path to the root directory of source code tree
# ----------------------------------------------------------------------
#

ROOT = /home/data/GitHub/Gruber-Diagnostic-Box-Model/src_ia

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
#F_FLAGS  =  

LFLAGS = -s

LIBNAME = libchem.a
L = $(LIBNAME)

# -------------------------------------------------------------------------
# -- LOCATION OF INCLUDE FILES: (for directives like 'include filename')  
# -- example: ( I_PATH = /users/user_name/proj/include )  
# -------------------------------------------------------------------------

I_PATH = \
	 $(ROOT)/incl

O_FILES = \
	vp_purewater.o\
	vp_seawater.o\
	calcco2.o\
	chem.o\
	estimate.o\
	schmidt_number.o
#
H_FILES = \
 
#
# -------------------------------------------------------------------------
# -- LIBRARY OBJECTS
# -------------------------------------------------------------------------
#
LIBOBJ = \
	$(L)(vp_purewater.o)\
	$(L)(vp_seawater.o)\
	$(L)(calcco2.o)\
	$(L)(chem.o)\
	$(L)(estimate.o)\
	$(L)(schmidt_number.o)

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
	@echo " *** removing object and *.f files ***"
	@echo " ***************************************"
	@echo ""
	rm -f *.o *% *.f core
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
vp_purewater.f : vp_purewater.F
vp_purewater.o : vp_purewater.f
#
vp_seawater.f : vp_seawater.F
vp_seawater.o : vp_seawater.f
#
schmidt_number.f : schmidt_number.F
schmidt_number.o : schmidt_number.f
#
chem.f : chem.F
chem.o : chem.f
#
calcco2.f : calcco2.F
calcco2.o : calcco2.f
#
estimate.f : estimate.F
estimate.o : estimate.f
#
$(L) : $(O_FILES)
