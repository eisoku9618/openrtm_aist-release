# -*- Makefile -*-
#------------------------------------------------------------
# @file   Makefile.am
# @brief  Makefile.am for OrganizationProxy unit test
# @date   $Date$
# @author Noriaki Ando <n-ando@aist.go.jp>
#
# $Id$
#
#------------------------------------------------------------

#
# $Log$
#


AUTOMAKE_OPTIONS = 1.9

IDLC = @IDLC@
IDLFLAGS = @IDL_FLAGS@
LIBS = @LIBS@

AM_CPPFLAGS= -I.                                    \
	-I$(includedir)                             \
	-I$(top_builddir)                           \
	-I.                                         \
	-I../                                       \
        -I$(top_builddir)/../../../../              \
        -I$(top_builddir)/../../../../rtm           \
        -I$(top_builddir)/../../../../coil/include  \
        -I$(top_builddir)/../../../../rtc/corba/idl \
        -I$(top_builddir)/../../../../rtc/corba     \
        -I/usr/include/                             \
        -I/usr/include/omniORB4/

AM_LDFLAGS= -L.                   \
	-L$(top_builddir)         \
        -L$(top_builddir)/../../../../coil/lib


IDL_SOURCES = \
        $(top_builddir)/../../../../rtc/corba/idl/SDOPackage.idl \
        $(top_builddir)/../../../../rtc/corba/idl/RTC.idl        \
        $(top_builddir)/../../../../rtc/corba/idl/OpenRTM.idl 

noinst_PROGRAMS = OrganizationProxyTests

OrganizationProxyTests_SOURCES = \
        ../TestRunner.cpp                                       \
	$(IDL_SOURCES:.idl=Skel.cpp)                            \
        $(top_builddir)/../../../../doil/corba/CORBAManager.cpp \
        $(top_builddir)/../../../../doil/ORBManager.cpp         \
        $(top_builddir)/../../../../rtm/NVUtil.cpp              \
        $(top_builddir)/RTCTypeConversion.cpp                   \
        $(top_builddir)/SDOPackageTypeConversion.cpp            \
        $(top_builddir)/OrganizationProxy.cpp \
        OrganizationProxyTests.cpp
OrganizationProxyTests_LDFLAGS = -L$(libdir)
OrganizationProxyTests_LDADD   = \
         -lcppunit                                 \
         -lomniORB4                                \
         -lomnithread                              \
         -lomniDynamic4                            \
         -lcoil 

TEST_SRC = $(OrganizationProxyTests_SOURCES)
TEST_H   = 

# all
all: do-test

# do tests
do-test:
	./OrganizationProxyTests

# clean-up
clean-local:
	rm -f *.o *.Po *.gch *.la
	rm -f *~ *core
	rm -f *.xml
	rm -f Makefile.old
	rm -f *.vcproj
	rm -rf Release Debug

#------------------------------------------------------------
# vcproj file build rules
#------------------------------------------------------------
win32_builddir = .

vcproj: OrganizationProxy_vc8.vcproj OrganizationProxy_vc9.vcproj OrganizationProxy_vc10.vcproj


OrganizationProxy_vc8.vcproj:
	$(top_builddir)/build/vcprojtool.py vcproj \
		--projectname OrganizationProxyTest \
		--type EXE \
		--vcversion "8.00" \
		--version $(COIL_VERSION) \
		--out $(win32_builddir)/OrganizationProxy_vc8.vcproj \
		--yaml ../coil_test.vcproj.yaml \
		--source $(TEST_SRC)
#		--header $(TEST_H)
	qkc -O- -sm $(win32_builddir)/OrganizationProxy_vc8.vcproj

OrganizationProxy_vc9.vcproj:
	$(top_builddir)/build/vcprojtool.py vcproj \
		--projectname OrganizationProxyTest \
		--type EXE \
		--vcversion "9.00" \
		--version $(COIL_VERSION) \
		--out $(win32_builddir)/OrganizationProxy_vc9.vcproj \
		--yaml ../coil_test.vcproj.yaml \
		--source $(TEST_SRC)
#		--header $(TEST_H)
	qkc -O- -sm $(win32_builddir)/OrganizationProxy_vc9.vcproj


OrganizationProxy_vc10.vcproj:
	$(top_builddir)/build/vcprojtool.py vcproj \
		--projectname OrganizationProxyTest \
		--type EXE \
		--vcversion "10.00" \
		--version $(COIL_VERSION) \
		--out $(win32_builddir)/OrganizationProxy_vc10.vcproj \
		--yaml ../coil_test.vcproj.yaml \
		--source $(TEST_SRC)
	qkc -O- -sm $(win32_builddir)/OrganizationProxy_vc10.vcproj

