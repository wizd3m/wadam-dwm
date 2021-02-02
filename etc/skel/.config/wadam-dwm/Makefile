# dwm - dynamic window manager
# See LICENSE file for copyright and license details.

include config.mk

SRC = drw.c dwm.c util.c
OBJ = ${SRC:.c=.o}

all: options dwmwadam

options:
	@echo dwmwadam build options:
	@echo "CFLAGS   = ${CFLAGS}"
	@echo "LDFLAGS  = ${LDFLAGS}"
	@echo "CC       = ${CC}"

.c.o:
	${CC} -c ${CFLAGS} $<

${OBJ}: config.h config.mk

config.h:
	cp config.def.h $@

dwmwadam: ${OBJ}
	${CC} -o $@ ${OBJ} ${LDFLAGS}

clean:
	rm -f dwmwadam ${OBJ} dwmwadam-${VERSION}.tar.gz

dist: clean
	mkdir -p dwmwadam-${VERSION}
	cp -R LICENSE Makefile README config.def.h config.mk\
		dwm.1 drw.h util.h ${SRC} dwm.png transient.c dwm-${VERSION}
	tar -cf dwmwadam-${VERSION}.tar dwm-${VERSION}
	gzip dwmwadam-${VERSION}.tar
	rm -rf dwmwadam-${VERSION}

install: all
	mkdir -p ${DESTDIR}${PREFIX}/bin
	cp -f dwmwadam ${DESTDIR}${PREFIX}/bin
	chmod 755 ${DESTDIR}${PREFIX}/bin/dwmwadam

uninstall:
	rm -f ${DESTDIR}${PREFIX}/bin/dwmwadam

.PHONY: all options clean dist install uninstall
