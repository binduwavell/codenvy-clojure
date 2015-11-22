FROM binduwavell/codenvy-clojure-base:0.2

MAINTAINER Bindu Wavell <bindu@ziaconsulting.com>

RUN wget https://github.com/flyingmachine/emacs-for-clojure/archive/book1.zip -O /home/user/book1.zip && \
    unzip /home/user/book1.zip -d /home/user && \
    rm /home/user/book1.zip && \
    mv /home/user/emacs-for-clojure-book1 /home/user/.emacs.d && \
    echo '{:user {:plugins [[cider/cider-nrepl "0.8.1"]]}}' >> /home/user/.lein/profiles.clj
