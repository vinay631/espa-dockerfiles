FROM usgs.espa.centos.science


MAINTAINER USGS LSRD http://eros.usgs.gov


LABEL description="This build adds in MODTRAN which we are not allowed to distribute."

# ----------------------------------------------------------------------------
# Build MODTRAN into the docker image
# If ever a new MODTRAN is built, the DATA directory needs to be copied
# to the auxiliaries location
COPY external_tools/modtran-5.3.2 /usr/local/src/modtran
RUN cd $SRC_DIR \
    && cd modtran \
    && ./bootstrap \
    && ./configure \
    && make install \
    && make databases \
    && cp -r DATA /usr/local/share/MODTRAN_DATA \
    && ln -sf /usr/local/bin/mod53 /usr/local/bin/modtran \
    && cd $SRC_DIR \
    && rm -rf modtran
