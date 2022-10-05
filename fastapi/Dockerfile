FROM debian:latest
ENV TZ=Asia/Ho_Chi_Minh
ENV DEBIAN_FRONTEND noninteractive

ENV DEBCONF_NOWARNINGS yes


# oracle
RUN apt-get update && apt-get install -y --no-install-recommends apt-utils && \
	apt-get  install -y ca-certificates libaio1 wget unzip gnupg2 gnupg

RUN wget -O /tmp/instantclient-basic-linux-x64.zip https://download.oracle.com/otn_software/linux/instantclient/193000/instantclient-basic-linux.x64-19.3.0.0.0dbru.zip

RUN mkdir -p /usr/lib/oracle && unzip /tmp/instantclient-basic-linux-x64.zip -d /usr/lib/oracle

RUN ldconfig -v /usr/lib/oracle/instantclient_19_3

RUN ldd /usr/lib/oracle/instantclient_19_3/libclntsh.so

# python
RUN  apt-get install software-properties-common -y && \
	apt-get update && \
	apt-get install python3.8-dev python3-pip python3-venv -y

ENV LD_LIBRARY_PATH=/usr/lib/oracle/instantclient_19_3

WORKDIR /app

# Create a group and user
RUN addgroup  appgroup && \
    adduser  app_user --ingroup appgroup && \
    chown -R app_user:appgroup /app

USER app_user


CMD ["/bin/bash"]