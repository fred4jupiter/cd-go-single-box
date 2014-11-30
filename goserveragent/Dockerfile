FROM rattermeyer/ubuntu-jdk:1.0
MAINTAINER Michael Staehler <hamsterhase@gmail.com>

RUN apt-get update
RUN apt-get upgrade -y --force-yes
RUN apt-get install -y wget unzip dnsutils dos2unix

# --- go server ---
RUN wget -O /tmp/go-agent.deb http://download.go.cd/gocd-deb/go-server-14.3.0-1186.deb
# COPY go-server-14.3.0-1186.deb /tmp/go-server.deb

RUN dpkg -i /tmp/go-server.deb
RUN rm -f /tmp/go-server.deb

# --- go agent ---
RUN wget -O /tmp/go-agent.deb http://download.go.cd/gocd-deb/go-agent-14.3.0-1186.deb
# COPY go-agent-14.3.0-1186.deb /tmp/go-agent.deb

RUN dpkg -i /tmp/go-agent.deb
RUN rm /tmp/go-agent.deb

# RUN sed -i 's/GO_SERVER/GO_SERVER=127.0.0.1/g' /etc/default/go-agent
RUN sed -i 's/DAEMON=Y/DAEMON=N/g' /etc/default/go-agent

CMD service go-server start && service go-agent start

EXPOSE 8153
EXPOSE 8154
