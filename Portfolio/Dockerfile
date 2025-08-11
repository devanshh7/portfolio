FROM nginx:alpine

#remove default html for nginx
RUN rm -rf /usr/share/nginx/html/*

#copy your static website file
COPY . /usr/share/nginx/html/


EXPOSE 80

