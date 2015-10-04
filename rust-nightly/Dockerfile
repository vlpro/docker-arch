FROM vlpro/arch-yaourt

USER yaourt
RUN yaourt --noconfirm -Sa rust-nightly

# remove user yaourt (for security reasons)
USER root
RUN userdel -r yaourt && rm /etc/sudoers.d/yaourt


