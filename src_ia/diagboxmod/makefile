# -------------------------------------------------------------------------
# FILE    : makefile
# AUTHOR  : Nicolas Gruber
# LAST REV: 05-AUG-96  adapted for program diag_boxmodel
#           17-SEP-99  adapted for SUN and interannual variability version
#                      special version for diagboxmod library part
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

F_C      = gfortran
#F_C      = lf95
#
F_FLAGS  = -C 

LFLAGS = -s

LIBNAME = libdiagboxmod.a
L = $(LIBNAME)

# -------------------------------------------------------------------------
# -- LOCATION OF INCLUDE FILES: (for directives like 'include filename')  
# -- example: ( I_PATH = /users/user_name/proj/include )  
# -------------------------------------------------------------------------

I_PATH = \
	 $(ROOT)/incl

O_FILES = \
	intro.o\
	init_params.o\
	userinput.o\
	run_simulation.o\
	set_intval_to_zero.o\
	assign_params.o\
	set_sums_to_zero.o\
	init_val.o\
	input.o\
	gasexchange.o\
	vert_diff.o\
	intvertgrad_ent.o\
	masscons_ent.o\
	episevent_ent.o\
	matear_ent.o\
	advection1.o\
	advection2.o\
	net_comm_prod.o\
	calc_int_val.o\
	calc_run_stat.o\
	write_std_output.o\
	write_op_output.o\
	write_rates_tofile.o\
	write_fluxes_tofile.o\
	write_solution_tofile.o\
	write_mc_rates_tofile.o\
	write_mc_fluxes_tofile.o\
	write_obs_tofile.o\
	write_rateanomalies_tofile.o\
	write_fluxanomalies_tofile.o\
	write_mc_fluxanomalies_tofile.o\
	compute_anomalies.o\
	compute_runavg.o\
	compute_mc_runavg.o\
	harmonic.o\
	delta_to_ratio.o\
	c13_to_delta.o\
	delta_to_c13.o\
	rates_to_fluxes.o\
	fluxes_to_rates.o\
	getdate.o\
	keep_mc_statistics.o\
	calc_mc_statistics.o\
	write_mc_output.o\
	write_sn_output.o\
	spline.o\
	iplin.o
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
	$(L)(intro.o)\
	$(L)(init_params.o)\
	$(L)(userinput.o)\
	$(L)(run_simulation.o)\
	$(L)(set_intval_to_zero.o)\
	$(L)(assign_params.o)\
	$(L)(set_sums_to_zero.o)\
	$(L)(init_val.o)\
	$(L)(input.o)\
	$(L)(gasexchange.o)\
	$(L)(vert_diff.o)\
	$(L)(intvertgrad_ent.o)\
	$(L)(masscons_ent.o)\
	$(L)(episevent_ent.o)\
	$(L)(matear_ent.o)\
	$(L)(advection1.o)\
	$(L)(advection2.o)\
	$(L)(net_comm_prod.o)\
	$(L)(calc_int_val.o)\
	$(L)(calc_run_stat.o)\
	$(L)(write_std_output.o)\
	$(L)(write_op_output.o)\
	$(L)(write_rates_tofile.o)\
	$(L)(write_fluxes_tofile.o)\
	$(L)(write_solution_tofile.o)\
	$(L)(write_mc_rates_tofile.o)\
	$(L)(write_mc_fluxes_tofile.o)\
	$(L)(write_obs_tofile.o)\
	$(L)(write_rateanomalies_tofile.o)\
	$(L)(write_fluxanomalies_tofile.o)\
	$(L)(write_mc_fluxanomalies_tofile.o)\
	$(L)(compute_anomalies.o)\
	$(L)(compute_runavg.o)\
	$(L)(compute_mc_runavg.o)\
	$(L)(harmonic.o)\
	$(L)(delta_to_ratio.o)\
	$(L)(c13_to_delta.o)\
	$(L)(delta_to_c13.o)\
	$(L)(rates_to_fluxes.o)\
	$(L)(fluxes_to_rates.o)\
	$(L)(getdate.o)\
	$(L)(keep_mc_statistics.o)\
	$(L)(calc_mc_statistics.o)\
	$(L)(write_mc_output.o)\
	$(L)(write_sn_output.o)\
	$(L)(spline.o)\
	$(L)(iplin.o)

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
userinput.f : userinput.F $(H_FILES)
userinput.o : userinput.f
#
intro.f : intro.F
intro.o : intro.f
#
init_params.f : init_params.F
init_params.o : init_params.f
#
run_simulation.f : run_simulation.F  $(H_FILES)
run_simulation.o : run_simulation.f
#
assign_params.f : assign_params.F $(H_FILES)
assign_params.o : assign_params.f 
#
set_intval_to_zero.f : set_intval_to_zero.F $(H_FILES)
set_intval_to_zero.o : set_intval_to_zero.f
#
set_sums_to_zero.f : set_sums_to_zero.F $(H_FILES)
set_sums_to_zero.o : set_sums_to_zero.f
#
init_val.f : init_val.F $(H_FILES)
init_val.o : init_val.f
#
input.f : input.F $(H_FILES)
input.o : input.f
#
gasexchange.f : gasexchange.F $(H_FILES)
gasexchange.o : gasexchange.f
#
vert_diff.f : vert_diff.F $(H_FILES)
vert_diff.o : vert_diff.f
#
intvertgrad_ent.f : intvertgrad_ent.F $(H_FILES)
intvertgrad_ent.o : intvertgrad_ent.f
#
masscons_ent.f : masscons_ent.F $(H_FILES)
masscons_ent.o : masscons_ent.f
#
episevent_ent.f : episevent_ent.F $(H_FILES)
episevent_ent.o : episevent_ent.f
#
matear_ent.f : matear_ent.F $(H_FILES)
matear_ent.o : matear_ent.f 
#
advection1.f : advection1.F $(H_FILES)
advection1.o : advection1.f
#
advection2.f : advection2.F $(H_FILES)
advection2.o : advection2.f
#
net_comm_prod.f : net_comm_prod.F $(H_FILES)
net_comm_prod.o : net_comm_prod.f
#
calc_int_val.f : calc_int_val.F $(H_FILES)
calc_int_val.o : calc_int_val.f
#
calc_run_stat.f : calc_run_stat.F $(H_FILES)
calc_run_stat.o : calc_run_stat.f
#
calc_mc_statistics.f : calc_mc_statistics.F $(H_FILES)
calc_mc_statistics.o : calc_mc_statistics.f
#
keep_mc_statistics.f : keep_mc_statistics.F $(H_FILES)
keep_mc_statistics.o : keep_mc_statistics.f
#
write_std_output.f : write_std_output.F $(H_FILES)
write_std_output.o : write_std_output.f
#
write_op_output.f : write_op_output.F $(H_FILES)
write_op_output.o : write_op_output.f
#
write_mc_output.f : write_mc_output.F $(H_FILES)
write_mc_output.o : write_mc_output.f
#
write_sn_output.f : write_sn_output.F $(H_FILES)
write_sn_output.o : write_sn_output.f
#
write_rates_tofile.f : write_rates_tofile.F $(H_FILES)
write_rates_tofile.o : write_rates_tofile.f
#
write_solution_tofile.f : write_solution_tofile.F $(H_FILES)
write_solution_tofile.o : write_solution_tofile.f
#
write_fluxes_tofile.f : write_fluxes_tofile.F $(H_FILES)
write_fluxes_tofile.o : write_fluxes_tofile.f
#
write_mc_rates_tofile.f : write_mc_rates_tofile.F $(H_FILES)
write_mc_rates_tofile.o : write_mc_rates_tofile.f
#
write_mc_fluxes_tofile.f : write_mc_fluxes_tofile.F $(H_FILES)
write_mc_fluxes_tofile.o : write_mc_fluxes_tofile.f
#
write_obs_tofile.f : write_obs_tofile.F $(H_FILES)
write_obs_tofile.o : write_obs_tofile.f
#
write_rateanomalies_tofile.f : write_rateanomalies_tofile.F $(H_FILES)
write_rateanomalies_tofile.o : write_rateanomalies_tofile.f
#
write_fluxanomalies_tofile.f :  write_fluxanomalies_tofile.F $(H_FILES)
write_fluxanomalies_tofile.o :  write_fluxanomalies_tofile.f
#
write_mc_fluxanomalies_tofile.f :  write_mc_fluxanomalies_tofile.F $(H_FILES)
write_mc_fluxanomalies_tofile.o :  write_mc_fluxanomalies_tofile.f
#
compute_anomalies.f : compute_anomalies.F $(H_FILES)
compute_anomalies.o : compute_anomalies.f
#
compute_runavg.f : compute_runavg.F $(H_FILES)
compute_runavg.o : compute_runavg.f
#
compute_mc_runavg.f : compute_mc_runavg.F $(H_FILES)
compute_mc_runavg.o : compute_mc_runavg.f
#
harmonic.f : harmonic.F
harmonic.o : harmonic.f
#
rates_to_fluxes.f : rates_to_fluxes.F
rates_to_fluxes.o : rates_to_fluxes.f
#
fluxes_to_rates.f : fluxes_to_rates.F
fluxes_to_rates.o : fluxes_to_rates.f
#
delta_to_ratio.f : delta_to_ratio.F
delta_to_ratio.o : delta_to_ratio.f
#
c13_to_delta.f : c13_to_delta.F
c13_to_delta.o : c13_to_delta.f
#
delta_to_c13.f : delta_to_c13.F
delta_to_c13.o : delta_to_c13.f
#
spline.f : spline.F
spline.o : spline.f
#
iplin.f : iplin.F
iplin.o : iplin.f
#
$(L) : $(O_FILES)

