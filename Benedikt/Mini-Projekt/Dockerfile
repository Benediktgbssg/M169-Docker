# Datei Dockerfile
FROM httpd:2.4
COPY ./public-html /usr/local/apache2/htdocs/
COPY ./my-httpd.conf /usr/local/apache2/conf/httpd.conf

#docker run -d --name web -p 8080:80 -v /home/vmadmin/Desktop/dock/html_log/:/usr/local/apache2/logs/ -v /home/vmadmin/Desktop/dock/html_html/:/usr/local/apache2/htdocs/ my-webserver 