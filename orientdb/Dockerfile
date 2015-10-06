FROM vlpro/arch-yaourt

ENV ORIENTDB_ROOT_PASSWORD root

# create user and group
RUN groupadd -r yaourt
RUN useradd -r -g yaourt yaourt

# add root access
RUN echo "yaourt        ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/yaourt
USER yaourt
RUN yaourt --noconfirm -Sa orientdb-community

# remove user yaourt (for security reasons)
USER root
RUN userdel -r yaourt && rm /etc/sudoers.d/yaourt

USER orient

VOLUME ["/opt/orientdb/databases", "/opt/orientdb/config"]

# configure system 
EXPOSE 2424 
EXPOSE 2480

CMD ["/opt/orientdb/bin/server.sh"]
