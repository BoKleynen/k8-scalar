FROM debian:buster
RUN apt-get update && apt-get install -y build-essential libgsl-dev && apt-get clean && rm -rf /var/lib/apt/lists/*
COPY test.c .
RUN gcc -I/usr/include/gsl -lgsl test.c
CMD ./a.out
