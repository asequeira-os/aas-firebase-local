FROM ubuntu:20.04
RUN apt-get update

# without tzdata install, nodejs prompts for geographic region
RUN apt install -y tzdata  wget apt-transport-https curl gnupg
RUN apt install -y lsof git

# two seem to be required for nodejs?
RUN apt-get update
RUN apt-get update

RUN apt-get install -y nodejs npm

RUN apt-get install -y openjdk-11-jdk-headless

RUN npm install -g firebase-tools

RUN mkdir /work
WORKDIR /work

# for normal use?
# firebase login --no-localhost 

# for CICD use
# firebase login:ci --no-localhost
# and create a '.firebase_token' file that looks like
# export FIREBASE_TOKEN=1//ZZZZ....hhhh

RUN echo 'export PS1="FB-local [\w] \\$ "' >> /root/.bashrc
RUN echo 'source /work/.firebase_token' >> /root/.bashrc

CMD bash
