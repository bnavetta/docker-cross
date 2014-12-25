FROM bnavetta/crosstool-ng

USER root
RUN mkdir -p /opt/cross/m68k-unknown-elf && chown ct-ng /opt/cross/m68k-unknown-elf
USER ct-ng

WORKDIR /opt/cross/m68k-unknown-elf
RUN ct-ng m68k-unknown-elf && ct-ng build

ENV PATH /opt/cross/m68k-unknown-elf:$PATH
