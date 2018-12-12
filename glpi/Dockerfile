FROM nginx:1.15
LABEL maintener="Tec Stéfani <tec@ceramicastefani.com.br>"

RUN apt-get update; \
    apt-get install --no-install-recommends --no-install-suggests -y wget

# Temporario, ou não rs
RUN mkdir /glpi; \
    wget https://github.com/glpi-project/glpi/releases/download/9.3.3/glpi-9.3.3.tgz -O /tmp/glpi.tar.gz --no-check-certificate; \
    tar -C /tmp -xzf /tmp/glpi.tar.gz; \
    cp -R /tmp/glpi/* /glpi; \
    rm -rf /tmp/glpi.tar.gz; \
    rm -rf /tmp/glpi;

RUN chown -R nginx:nginx /glpi; \
    chmod -R 777 glpi/config/; \
     chmod -R 777 glpi/files/;

COPY ./nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
STOPSIGNAL SIGTERM
CMD ["nginx", "-g", "daemon off;"]