FROM continuumio/miniconda3:4.3.27p0

#Update the image
RUN apt-get update


#Create User and Working Directory
RUN useradd --create-home --home-dir /home/ds --shell /bin/bash ds
RUN adduser ds sudo

#Make directory for notebooks
RUN mkdir -p /home/ds/notebooks

#Make the working directory
WORKDIR /home/ds

#Make config folder for the requirements text file
RUN mkdir -p /home/ds/config
ADD requirements.txt /home/ds/config

#Install the packages from the requirements file and clean up
RUN conda install --yes --file config/requirements.txt  && \
    conda clean --yes --all

#Install Django and Django Rest Framework through pip
RUN pip install django==2.0 djangorestframework==3.7

#Set Variables
ENV HOME=/home/ds
ENV SHELL=/bin/bash
ENV USER=ds
VOLUME /home/ds

#Startup the Jupyter notebook when this runs.
CMD jupyter-notebook --no-browser --port 8888 --ip='*' --allow-root
