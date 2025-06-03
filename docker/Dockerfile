FROM ubuntu:24.10@sha256:aadf9a3f5eda81295050d13dabe851b26a67597e424a908f25a63f589dfed48f
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
# for normal use?
# firebase login --no-localhost 

# ignore below - local project should not need this
# for CICD use
# firebase login:ci --no-localhost
# and create a '.firebase_token' file that looks like
# export FIREBASE_TOKEN=1//ZZZZ....hhhh

RUN echo 'export PS1="FB-local [\w] \\$ "' >> /root/.bashrc

# should not need real project permissions token
#RUN echo 'source /work/.firebase_token' >> /root/.bashrc

# CMD . ~/.nvm/nvm.sh && bash
CMD . ~/.nvm/nvm.sh && cd data && firebase emulators:start

# notes on how I created this
# mkdir data && cd data
# firebase init emulators
#  choose - 'create a new project'
# name 'fblocal01' (learned later to add demo- prefix)
# <space> Authentication Emulator
# port - 9099
# Emulator UI Y
# UI suite port - 4000
# firebase emulators:start
#
# modify firebase.json and add
#         "host": "0.0.0.0",
# for all ports
#
# in docker host http://localhost:4000/auth
