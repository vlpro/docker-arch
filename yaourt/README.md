https://github.com/vlpro/docker-arch/tree/master/yaourt

# Usage:
```Dockerfile
FROM vlpro/arch-yaourt

# create user yaourt
RUN useradd -r -g yaourt yaourt

# add root access
RUN echo "yaourt        ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/yaourt
USER yaourt
RUN yaourt --noconfirm -Sa SOME_AUR_PACKAGE

# remove user yaourt (for security reasons)
USER root
RUN userdel -r yaourt && rm /etc/sudoers.d/yaourt
```
