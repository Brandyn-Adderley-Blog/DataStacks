FROM python:3.6.3-slim

#Run an update
RUN apt-get update

#Create a user ds
RUN adduser -D -S -h /home/ds -s /bin/ash ds

#install Jupyter notebook
RUN pip install jupyter

#Set Variables
ENV HOME=/home/ds
ENV SHELL=/bin/bash
ENV USER=ds
VOLUME /home/ds
WORKDIR /home/ds

#run the jupyter notebook
CMD jupyter-notebook --no-browser --port 8888 --ip='*' --allow-root
