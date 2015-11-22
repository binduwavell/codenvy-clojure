FROM binduwavell/codenvy-alfresco-base:0.4

MAINTAINER Bindu Wavell <bindu@ziaconsulting.com>

RUN sudo apt-get update && \
    sudo apt-get install -y emacs && \
    sudo apt-get clean && \
    sudo rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN mkdir /home/user/bin
ENV PATH /home/user/bin:$PATH
RUN echo "export PATH=$PATH" >> /home/user/.bashrc

RUN wget https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein -O /home/user/bin/lein && \
    chmod 755 /home/user/bin/lein && \
    /home/user/bin/lein && \
    timeout 30 /home/user/bin/lein repl :headless ; \
    /bin/cat /dev/null

RUN wget https://github.com/boot-clj/boot-bin/releases/download/2.4.2/boot.sh -O /home/user/bin/boot && \
    chmod 755 /home/user/bin/boot && \
    /home/user/bin/boot && \
    /home/user/bin/boot

ENV CODENVY_APP_BIND_DIR /home/user/application
VOLUME ["/home/user/application"]

ENV CODENVY_APP_PORT_8080_HTTP 8080
EXPOSE 8080
