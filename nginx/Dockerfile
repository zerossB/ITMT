FROM nginx:1.15
LABEL maintener="Tec Stéfani <tec@ceramicastefani.com.br>"

COPY default.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
STOPSIGNAL SIGTERM
CMD ["nginx", "-g", "daemon off;"]