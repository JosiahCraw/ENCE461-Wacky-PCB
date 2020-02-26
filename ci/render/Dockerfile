FROM python:3.8-buster

RUN apt-get install -y git librsvg2-bin

RUN python3 -m pip install OleFileIO_PL

WORKDIR /renderer
USER root

RUN git clone https://github.com/vadmium/python-altium.git
