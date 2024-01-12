IDIR =./
CC=gcc
CFLAGS=-I$(IDIR)  -I../../../libufdt-github/sysdeps/include

ODIR=obj
LDIR = -L/usr/lib/x86_64-linux-gnu/

LIBS= -L/usr/lib/x86_64-linux-gnu/ -lfdt ./libfdt.a

_DEPS = mkdtimg_core.h 
DEPS = $(patsubst %,$(IDIR)/%,$(_DEPS))

_OBJ = mkdtimg.o mkdtimg_cfg_create.o mkdtimg_core.o mkdtimg_create.o mkdtimg_dump.o dt_table.o acpi.o libufdt_sysdeps_posix.o
OBJ = $(patsubst %,$(ODIR)/%,$(_OBJ))


$(ODIR)/%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS)

mkdtimg: $(OBJ)
	$(CC) -o $@ $^ $(CFLAGS) $(LIBS)

.PHONY: clean

clean:
	rm -f $(ODIR)/*.o *~ core $(INCDIR)/*~
