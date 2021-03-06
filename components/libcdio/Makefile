#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL)". You may
# only use this file in accordance with the terms of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source. A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright 2015 Alexander Pyhalov
#

include ../../make-rules/shared-macros.mk

COMPONENT_NAME=		libcdio
COMPONENT_VERSION=	0.93
COMPONENT_PROJECT_URL=	http://www.gnu.org/software/libcdio/
COMPONENT_SUMMARY=	GNU Compact Disc Input and Control Library
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.bz2
COMPONENT_ARCHIVE_HASH=	\
    sha256:f8276629226c7e1e74209b66ca421d09d6aec87f72f60ae9b1d3debd0a13dda8
COMPONENT_ARCHIVE_URL=	http://ftp.gnu.org/gnu/libcdio/$(COMPONENT_ARCHIVE)
COMPONENT_LICENSE=	GPLv3
COMPONENT_LICENSE_FILE=	COPYING
COMPONENT_CLASSIFICATION=	System/Libraries
COMPONENT_FMRI= 	library/audio/libcdio

include $(WS_TOP)/make-rules/prep.mk
include $(WS_TOP)/make-rules/configure.mk
include $(WS_TOP)/make-rules/ips.mk

PATH=/usr/gnu/bin:/usr/bin

CPPFLAGS += -I/usr/gnu/include -I/usr/gnu/include/ncurses
CPPFLAGS += -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -DDBUS_API_SUBJECT_TO_CHANGE
CPPFLAGS += -D_FILE_OFFSET_BITS=64

LDFLAGS += -lhal -ldbus-1

CONFIGURE_OPTIONS+=	--sysconfdir=/etc
CONFIGURE_OPTIONS+=	--disable-cpp-progs
CONFIGURE_OPTIONS+=	--disable-cxx
CONFIGURE_OPTIONS+=	--disable-static

CONFIGURE_ENV += CPPFLAGS="$(CPPFLAGS)"

COMPONENT_POST_INSTALL_ACTION= \
	(cd $(PROTOUSRDIR) ;  $(MV) include/cdio/cdio_config.h include/cdio/cdio_config-$(BITS).h )

ENV = /usr/bin/env -i

# common targets
build:		$(BUILD_32_and_64)

install:	$(INSTALL_32_and_64)

test:		$(NO_TESTS)
