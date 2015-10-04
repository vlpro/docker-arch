FROM dock0/arch

# create .gnupg folder
RUN dirmngr

# update pacman keys
RUN pacman-key --init && \
    pacman-key --populate archlinux && \
    pacman-key --refresh-keys

# install sudo package
RUN pacman -S --noconfirm sudo

RUN echo -e "[archlinuxfr] \n SigLevel = Never \n Server = http://repo.archlinux.fr/\$arch" >> /etc/pacman.conf && \
	pacman -Syy --noconfirm yaourt && \
	pacman -Scc --noconfirm

# add yaourt user and group
RUN groupadd -r yaourt && \
    useradd -r -g yaourt yaourt
