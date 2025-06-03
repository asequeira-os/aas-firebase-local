FROM ubuntu:24.10
RUN apt-get update

RUN apt install -y curl

RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash

RUN . ~/.nvm/nvm.sh && nvm install 22.16
RUN . ~/.nvm/nvm.sh && nvm use node

RUN apt-get install -y openjdk-17-jdk

RUN . ~/.nvm/nvm.sh && npm install -g firebase-tools

RUN mkdir /work
WORKDIR /work

ADD data /work/data


RUN echo 'export PS1="FB-local [\w] \\$ "' >> /root/.bashrc


# CMD . ~/.nvm/nvm.sh && bash
CMD . ~/.nvm/nvm.sh && cd data && firebase emulators:start

