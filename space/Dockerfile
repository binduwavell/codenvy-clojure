FROM binduwavell/codenvy-clojure-base:0.1

MAINTAINER Bindu Wavell <bindu@ziaconsulting.com>


# This does two things, it allows us to configure what layers are applied
# when emacs first starts up and does the spacemacs install magic. It 
# also stops emacs from prompting for editing mode vim/emacs and for 
# full or basic mode.
ADD _spacemacs /home/user/.spacemacs

ADD _tmux.conf /home/user/.tmux.conf

# Makes it so emacs can print pretty characters in the modeline and elsewhere
ENV LANG en_US.UTF-8

# Spacemacs seems to need this to set itself up
ENV SHELL /bin/bash

# Setup environment
RUN sudo chown user:user /home/user/.spacemacs && \
    sudo chown user:user /home/user/.tmux.conf && \
    git clone --recursive https://github.com/syl20bnr/spacemacs ~/.emacs.d

# Make sure lein and cider are in sync
RUN echo '{:user {:plugins [[cider/cider-nrepl "0.10.0-SNAPSHOT"] [refactor-nrepl "2.0.0-SNAPSHOT"]] :dependencies [[alembic "0.3.2"] [org.clojure/tools.nrepl "0.2.12"]]}}' >> /home/user/.lein/profiles.clj 

# Run emacs headless to trigger installing all spacemacs deps
RUN /usr/bin/emacs --daemon
