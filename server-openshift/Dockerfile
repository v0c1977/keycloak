FROM jboss/keycloak:latest

ENV JBOSS_HOME /opt/jboss/keycloak
  
USER root

RUN chgrp -R 0 /opt/jboss/keycloak \
&& chmod -R g+rwX /opt/jboss/keycloak
  
USER jboss
#Enabling Proxy address forwarding so we can correctly handle SSL termination in front ends
#such as an OpenShift Router or Apache Proxy
RUN sed -i -e 's/<http-listener /& proxy-address-forwarding="${env.PROXY_ADDRESS_FORWARDING}" /' $JBOSS_HOME/standalone/configuration/standalone.xml
