FROM bnavetta/crosstool-ng

ADD defconfig /tmp/

RUN mkdir -p /tmp/cross \
	&& cd /tmp/cross \
	&& cp /tmp/defconfig . \
	&& ct-ng defconfig \
	&& ct-ng build \
	&& rm -rf /tmp/cross

ENV PATH /home/ct-ng/x-tools/i686-unknown-elf/bin:$PATH
