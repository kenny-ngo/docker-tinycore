FROM alpine

ADD tce-load.patch /tmp/
RUN wget http://www.tinycorelinux.net/7.x/x86/archive/7.2/distribution_files/rootfs.gz \
    && mkdir rootfs \
    && cd rootfs \
    && gzip -dc ../rootfs.gz | cpio -id \
    && rm -f ../rootfs.gz \
    && cd usr/bin \
    && patch < /tmp/tce-load.patch \
    && cd ../.. \
    && rm -f /tmp/tce-load.patch \
    && tar cf - . | gzip -c > /tmp/rootfs.tar.gz \
    && cd .. \
    && rm -rf rootfs

CMD ["/bin/true"]
