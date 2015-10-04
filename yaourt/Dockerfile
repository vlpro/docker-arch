FROM dock0/arch

# add yaourt user and group
RUN groupadd -r yaourt && \
    useradd -r -g yaourt yaourt && \
    mkdir /home/yaourt && \
    chown -R yaourt /home/yaourt

# install sudo package
RUN pacman -S --noconfirm sudo base-devel

# add root access
RUN echo "yaourt        ALL=(ALL) ALL" > /etc/sudoers.d/yaourt

# create .gnupg folder
RUN dirmngr


# update pacman keys
RUN pacman-key --init && \
    pacman-key --populate archlinux && \
    pacman-key --refresh-keys

RUN echo -e "[archlinuxfr] \n SigLevel = Never \n Server = http://repo.archlinux.fr/\$arch" >> /etc/pacman.conf && \
	pacman -Syy --noconfirm yaourt && \
	pacman -Scc --noconfirm
