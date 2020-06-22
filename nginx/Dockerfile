FROM nginx:1.16-alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY goapp.conf.tmpl /goapp.conf.tmpl
CMD envsubst '$$GOAPP_HOST' < /goapp.conf.tmpl \
    > /etc/nginx/conf.d/goapp.conf && nginx -g 'daemon off;'
