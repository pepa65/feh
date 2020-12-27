include ../config.mk

SOURCES = ${shell echo *.pre}
TARGETS = ${SOURCES:.pre=.1}
ZOOMRATE := ${shell grep -o 'ZOOM_RATE.*' ../src/feh.h |sed 's/.* //'}
ZOOMSLOWRATE := ${shell grep -o 'ZOOMSLOW_RATE.*' ../src/feh.h  |sed 's/.* //'}

all: ${TARGETS}

.pre.1:
	sed \
	-e 's/\$$VERSION\$$/${VERSION}/g' \
	-e 's/\$$DATE\$$/${MAN_DATE}/g' \
	-e 's/\$$MAN_CURL\$$/${MAN_CURL}/' \
	-e 's/\$$MAN_DEBUG\$$/${MAN_DEBUG}/' \
	-e 's/\$$MAN_EXIF\$$/${MAN_EXIF}/' \
	-e 's/\$$MAN_INOTIFY\$$/${MAN_INOTIFY}/' \
	-e 's/\$$MAN_XINERAMA\$$/${MAN_XINERAMA}/' \
	-e 's/\$$ZOOM_RATE\$$/${ZOOMRATE}/' \
	-e 's/\$$ZOOMSLOW_RATE\$$/${ZOOMSLOWRATE}/' \
	< ${@:.1=.pre} > $@

clean:
	rm -f *.1

.SUFFIXES: .pre .1

.PHONY: clean
