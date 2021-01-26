FROM ubuntu:18.04 as base 
          
MAINTAINER adderbyte  adderbyte@icloud.com


############# Run required installation and set Work directory #########
# installation
RUN apt-get update \ 
&& apt-get install -y tshark \
&& apt-get install -y wireshark\
  && apt-get install -y python3-pip python3-dev \
  && cd /usr/local/bin \
  && ln -s /usr/bin/python3 python \
  && pip3 install --upgrade pip 
  
     
# work drectory
RUN mkdir -p /work

WORKDIR /work
# add and install requirements
COPY ./requirements.txt /work

RUN pip3 install -r requirements.txt
#CMD ["python3"]