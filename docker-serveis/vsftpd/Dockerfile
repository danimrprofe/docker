FROM alpine:latest

EXPOSE 21 21/udp

RUN apk --update upgrade && apk --update --no-cache add vsftpd

COPY vsftpd.sh /usr/sbin/
RUN chmod +x /usr/sbin/vsftpd.sh
RUN ./usr/sbin/vsftpd.sh 

VOLUME ["srv","/srv"]

CMD ["vsftpd"]
