FROM dock0/arch

# synchronizing package list
RUN pacman --noconfirm -Sy

# install base-devel and yajl
RUN pacman --noconfirm -S base-devel
RUN pacman --noconfirm -S yajl

# create yaourt user and group
RUN groupadd -r yaourt
RUN useradd -r -g yaourt yaourt

RUN mkdir /tmp/yaourt
RUN chown -R yaourt:yaourt /tmp/yaourt && \
    chmod -R 771 /tmp/yaourt
USER yaourt 
WORKDIR /tmp/yaourt

# cloning and install yaourt dependency (package-query)
RUN git clone https://aur.archlinux.org/package-query.git 
WORKDIR /tmp/yaourt/package-query
RUN makepkg --noconfirm
USER root
WORKDIR /tmp/yaourt/package-query
RUN pacman --noconfirm -U *.tar.xz

# cloning and install yaourt
USER yaourt 
WORKDIR /tmp/yaourt
RUN git clone https://aur.archlinux.org/yaourt.git
WORKDIR /tmp/yaourt/yaourt
RUN makepkg --noconfirm
USER root 
WORKDIR /tmp/yaourt/yaourt
RUN pacman --noconfirm -U *.tar.xz

# remove user yaourt (for security reasons)
RUN userdel -r yaourt
