FROM ubuntu:22.04

WORKDIR /usr/src/app

RUN apt-get update
RUN apt-get -y install curl

COPY script.sh .

RUN chmod u+x script.sh

ENTRYPOINT [ "./script.sh" ] 