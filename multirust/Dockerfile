FROM vlpro/arch-yaourt

RUN mkdir /tmp/multirust
WORKDIR /tmp/multirust
RUN curl -O https://raw.githubusercontent.com/brson/multirust/master/blastoff.sh
RUN chmod +x blastoff.sh
RUN ./blastoff.sh --yes
