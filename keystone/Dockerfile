FROM ubuntu:14.04
MAINTAINER Abhishek Lekshmanan <abhishek.lekshmanan@gmail.com>

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get install -y keystone python-keystone sqlite
EXPOSE 5000 35357
ADD ./keystone.conf /etc/keystone/keystone.conf
RUN keystone-manage db_sync
CMD ["keystone-all"]
