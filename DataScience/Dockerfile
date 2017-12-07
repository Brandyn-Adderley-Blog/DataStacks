FROM continuumio/miniconda3:4.3.27p0

#Update the image
RUN apt-get update


#Create User and Working Directory
RUN useradd --create-home --home-dir /home/ds --shell /bin/bash ds
RUN adduser ds sudo


#Install Python packages
WORKDIR /home/ds

RUN mkdir -p /home/ds/config
ADD requirements.txt /home/ds/config
ADD run_jupyter.sh /home/ds/config
RUN chmod +x /home/ds
RUN chown ds /home/ds
RUN chmod +x /home/ds/config/run_jupyter.sh
RUN chown ds /home/ds/config/run_jupyter.sh
RUN cd config
RUN conda install --yes --file config/requirements.txt  && \
    conda clean --yes --all


RUN mkdir -p /home/ds/notebooks

#Set Variables
ENV HOME=/home/ds
ENV SHELL=/bin/bash
ENV USER=ds
VOLUME /home/ds

#Startup the Jupyter notebook when this runs.
CMD ["/home/ds/config/run_jupyter.sh"]
