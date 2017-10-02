FROM opensuse:42.2

RUN zypper ar -Gf https://download.opensuse.org/repositories/Cloud:/OpenStack:/Newton/openSUSE_Leap_42.2/Cloud:OpenStack:Newton.repo && \
    zypper -n update && \
    zypper -n in --force-resolution krb5 && \
    zypper -n in openstack-keystone which apache2 apache2-mod_wsgi

ADD ./wsgi-keystone.conf /etc/apache2/conf.d/wsgi-keystone.conf
ADD ./keystone.conf /etc/keystone/keystone.conf

RUN keystone-manage db_sync
RUN keystone-manage fernet_setup --keystone-user root --keystone-group root

EXPOSE 5000 35357

CMD ["apachectl","-D","FOREGROUND"]
