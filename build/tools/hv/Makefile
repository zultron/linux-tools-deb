OUTDIR = tools/hv

include ../../Makefile.inc

DEB_HOST_ARCH_CPU := $(shell dpkg-architecture -qDEB_HOST_ARCH_CPU)

ifneq ($(filter amd64 i386,$(DEB_HOST_ARCH_CPU)),)

all: hv_kvp_daemon
hv_kvp_daemon: $(top_srcdir)/tools/hv/hv_kvp_daemon.c
	$(CC) $(CFLAGS) -I$(top_srcdir)/include $(LDFLAGS) $< -o $@

install:
	install -D hv_kvp_daemon $(DESTDIR)/usr/sbin/hv_kvp_daemon
	install -D -m 644 $(top_srcdir)/tools/hv/hv_kvp_daemon.8 \
		$(DESTDIR)/usr/share/man/man8/hv_kvp_daemon.8
	install -d $(DESTDIR)/var/lib/hyperv

clean:
	rm -f hv_kvp_daemon

else

all:
install:
clean:

endif
