FROM jenkins/jenkins
USER root

# actualizando repo e instalando docker

RUN apt-get update && \
apt-get -y install apt-transport-https \
     ca-certificates \
     curl \
     gnupg2 \
     software-properties-common && \
curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg > /tmp/dkey; apt-key add /tmp/dkey && \
add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
   $(lsb_release -cs) \
   stable" && \
apt-get update && \
apt-get -y install docker-ce


RUN curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && chmod +x /usr/local/bin/docker-compose
RUN usermod -aG docker jenkins
#RUN chown jenkins /var/run/docker.sock

# instalando selenium, chromiun y chromedriver (deben tener la misma versión para que funcione correctamente (version de este driver 103.0.5060.53))

RUN apt-get -y install pip && \
pip3 install selenium  && \
apt-get install wget && \
apt-get install -y chromium && \
wget -P ~/downloads/ https://chromedriver.storage.googleapis.com/103.0.5060.53/chromedriver_linux64.zip && \
cd root/downloads && \
apt-get install unzip && \
unzip chromedriver_linux64.zip && \
chmod +x /root/downloads/chromedriver && \
mv ~/downloads/chromedriver /usr/local/share/chromedriver && \
ln -s /usr/local/share/chromedriver /usr/bin/chromedriver

# cambiando usuario
USER jenkins

# en una instalación nueva tanto el chromiun como el chromedriver deben tener la misma version

# fuente: https://www.balioglu.net/python/solved-how-to-install-selenium-on-debian-linux-with-a-chrome-driver-for-python/