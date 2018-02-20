FROM opensuse:42.2

RUN zypper ar -Gf https://download.opensuse.org/repositories/Cloud:/OpenStack:/Newton/openSUSE_Leap_42.2/Cloud:OpenStack:Newton.repo && \
    zypper -n update && \
    zypper -n in --force-resolution krb5 && \
    zypper -n in openstack-keystone which apache2 apache2-mod_wsgi

ADD ./wsgi-keystone.conf /etc/apache2/conf.d/wsgi-keystone.conf
ADD ./keystone.conf /etc/keystone/keystone.conf

RUN su keystone -s /bin/bash -c "keystone-manage db_sync" && \
    keystone-manage fernet_setup --keystone-user keystone --keystone-group keystone &&\
    keystone-manage bootstrap --bootstrap-password nova \
                    --bootstrap-username admin \
                    --bootstrap-project-name admin \
                    --bootstrap-role-name admin \
                    --bootstrap-service-name keystone

EXPOSE 5000 35357

COPY apache-foreground /usr/local/bin/

ENTRYPOINT ["apache-foreground"]
