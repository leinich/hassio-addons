ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

RUN apk update
RUN apk add bash 
RUN apk add avahi-tools 
RUN apk add avahi-compat-libdns_sd 
RUN apk add screen 
RUN apk add python2 
RUN apk add git 
RUN apk add py-tornado 
RUN apk add jq 
RUN apk add py-pip 
RUN apk add make 
RUN apk add sudo 
RUN apk add wget

WORKDIR /home/app
RUN wget https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/pybonjour/pybonjour-1.1.1.tar.gz
RUN tar -zxf pybonjour-1.1.1.tar.gz
RUN cd pybonjour-1.1.1 && /usr/bin/python setup.py install
RUN python2 -m pip install tornado
RUN python2 -m pip install wireless
RUN python2 -m pip install datetime
RUN git clone https://github.com/Tristan79/iBrew.git

EXPOSE 2080

# Copy data for add-on
COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
