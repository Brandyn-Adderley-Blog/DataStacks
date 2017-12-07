FROM python:3.6.3-alpine

#Run an update
RUN apk update add bash wget

#Create a user ds
RUN adduser -D -S -h /home/ds -s /bin/ash ds

#RUN adduser ds sudo

#Set Variables
ENV HOME=/home/ds
ENV SHELL=/bin/ash
ENV USER=ds
VOLUME /home/ds
WORKDIR /home/ds

CMD ["/bin/ash"]
