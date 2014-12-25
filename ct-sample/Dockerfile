FROM bnavetta/crosstool-ng

RUN mkdir -p /tmp/cross \
	&& cd /tmp/cross \
	&& ct-ng m68k-unknown-elf \
	&& ct-ng build \
	&& rm -rf /tmp/cross

ENV PATH /home/ct-ng/x-tools/m68k-unknown-elf/bin:$PATH
