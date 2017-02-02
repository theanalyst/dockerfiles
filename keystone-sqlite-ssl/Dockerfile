FROM ubuntu:14.04
MAINTAINER Abhishek Lekshmanan <abhishek.lekshmanan@gmail.com>

ENV DEBIAN_FRONTEND noninteractive
# TODO: move to adding via the conventional repo file etc.
RUN apt-get update && apt-get install -y software-properties-common && add-apt-repository cloud-archive:liberty
RUN apt-get update && apt-get install -y keystone python-keystone sqlite
EXPOSE 5000 35357
ADD ./keystone.conf /etc/keystone/keystone.conf
RUN keystone-manage db_sync
CMD ["keystone-all"]
