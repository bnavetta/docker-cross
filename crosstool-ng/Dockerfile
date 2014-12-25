FROM debian:sid

RUN apt-get update \
	&& apt-get install -y curl \
	&& rm -rf /var/lib/apt/lists/*

ENV CROSSTOOL_NG_VERSION 1.20.0
ENV CROSSTOOL_NG_DOWNLOAD_URL http://crosstool-ng.org/download/crosstool-ng/crosstool-ng-1.20.0.tar.bz2
ENV CROSSTOOL_NG_DOWNLOAD_SHA1 b11f7ee706753b8cf822f98b549f8ab9dd8da9c7

# These are needed to build crosstool-ng, but most are also needed for it to build toolchains
RUN apt-get update \
	&& apt-get install -y gcc g++ libc6-dev make bzip2 gperf bison flex texinfo wget patch gawk libtool libtool-bin libncurses5-dev automake --no-install-recommends

RUN set -x \
	&& mkdir -p /usr/src/crosstool-ng \
	&& curl -sSL "$CROSSTOOL_NG_DOWNLOAD_URL" -o crosstool-ng.tar.bz2 \
	&& echo "$CROSSTOOL_NG_DOWNLOAD_SHA1 *crosstool-ng.tar.bz2" | sha1sum -c - \
	&& tar -xjf crosstool-ng.tar.bz2 -C /usr/src/crosstool-ng --strip-components=1 \
	&& rm crosstool-ng.tar.bz2 \
	&& cd /usr/src/crosstool-ng \
	&& ./configure \
	&& make \
	&& make install \
	&& cd .. && rm -rf /usr/src/crosstool-ng

RUN groupadd ct-ng && useradd -g ct-ng -m ct-ng
USER ct-ng
