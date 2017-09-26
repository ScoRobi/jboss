FROM tifayuki/java:6
MAINTAINER Scott Robinson <scott.robinson@contrastsecurity.com>

RUN apt-get update && \
    apt-get install -y pwgen && \
    wget -q http://download.jboss.org/jbossas/7.0/jboss-as-7.0.2.Final/jboss-as-7.0.2.Final.tar.gz && \
    tar zxf jboss-as-7.0.2.Final.tar.gz && \
    rm jboss-as-7.0.2.Final.tar.gz && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN sed -i -r 's/jboss.bind.address.management:127.0.0.1/jboss.bind.address.management:0.0.0.0/' /jboss-as-7.0.2.Final/standalone/configuration/standalone.xml

ADD run.sh /run.sh
ADD set_jboss_admin_pass.sh /set_jboss_admin_pass.sh
RUN chmod +x /*.sh

# Exposed ENV
ENV JBOSS_PASS **Random**

EXPOSE 8080 9990
CMD ["/run.sh"]
