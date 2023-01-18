FROM amazon/aws-cli

RUN yum install -y net-tools jq nmap-ncat && \
    yum clean all

RUN wget https://github.com/digitalocean/doctl/releases/download/v1.92.0/doctl-1.92.0-linux-amd64.tar.gz && \
tar xf ~/doctl-1.92.0-linux-amd64.tar.gz && \
mv ~/doctl /usr/local/bin

COPY ./watchdog.sh .

ENTRYPOINT ["./watchdog.sh"]
