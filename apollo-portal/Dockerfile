# Dockerfile for apollo-portal
# Build with:
# docker build -t apollo-portal .
# Run with:
# docker run -p 9090:8080 -d --name apollo-portal apollo-portal

FROM java:8-jre
MAINTAINER huyuhao

ENV VERSION 1.6.0
#ADD env /
#RUN rm /bin/sh \
#    && ln -s /bin/bash /bin/sh
#RUN cat env >> /etc/profile \
#    && cat env >> ~/.bashrc \
#    && sh /etc/profile;source ~/.bashrc \
#    && cat /etc/profile


RUN apt-get install unzip

ADD apollo-portal-${VERSION}-github.zip /apollo-portal/apollo-portal-${VERSION}-github.zip

RUN unzip /apollo-portal/apollo-portal-${VERSION}-github.zip -d /apollo-portal \
    && rm -rf /apollo-portal/apollo-portal-${VERSION}-github.zip \
    && sed -i '$d' /apollo-portal/scripts/startup.sh \
    && echo "tail -f /dev/null" >> /apollo-portal/scripts/startup.sh

EXPOSE 8070
#ENTRYPOINT ["bash"]
CMD ["/apollo-portal/scripts/startup.sh"]
