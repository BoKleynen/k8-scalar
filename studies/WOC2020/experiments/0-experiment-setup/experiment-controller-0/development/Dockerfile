FROM ubuntu:16.04

# [Ubuntu] Install dependencies
RUN apt-get update && \
    apt-get install -y curl vim openssh-client default-jre gnuplot build-essential checkinstall libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev python
RUN mkdir /opt/local && \
    mkdir /opt/local/bin && \
    ln -s /usr/bin/gnuplot /opt/local/bin/gnuplot
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && \
    chmod +x ./kubectl && \
    mv ./kubectl /usr/local/bin/kubectl

WORKDIR /exp
COPY . .

# Infinite loop to be able to access shell in pod
CMD exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"
