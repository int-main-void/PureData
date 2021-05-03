.DEFAULT_GOAL:=pd_darwin

current:
	echo make pd_linux, pd_linux32, pd_nt, pd_darwin

clean: ; rm -f *.pd_linux *.o *.pd_darwin

PD_LIB_INC=/Applications/Pd-0.51-3.app/Contents/Resources/src 

DEST_DIR=~/Documents/Pd/externals/em

install:
	cp *.pd_darwin $(DEST_DIR)

# ----------------------- macOS -----------------------

pd_darwin:  dspobj~.pd_darwin testobj~.pd_darwin

.SUFFIXES: .pd_darwin

DARWINCFLAGS = -DPD -O2 -Wall -W -Wshadow -Wstrict-prototypes \
    -Wno-unused -Wno-parentheses -Wno-switch -arch x86_64

.c.pd_darwin:
	cc $(DARWINCFLAGS) -I $(PD_LIB_INC) -o $*.o -c $*.c
	cc -bundle -undefined suppress -arch x86_64 \
            -flat_namespace -o $*.pd_darwin $*.o 
	# rm -f $*.o

