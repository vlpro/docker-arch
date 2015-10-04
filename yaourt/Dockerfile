FROM dock0/arch

RUN echo -e "[archlinuxfr] \n SigLevel = Never \n Server = http://repo.archlinux.fr/\$arch" >> /etc/pacman.conf && \
	pacman -Syy --noconfirm yaourt && \
	pacman -Scc --noconfirm

# add yaourt user and group
RUN groupadd -r yaourt && \
    useradd -r -g yaourt yaourt
