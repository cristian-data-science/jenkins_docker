FROM ubuntu:20.04
USER root

RUN apt-get update 

#RUN apt install chromium-browser -y
RUN	apt-get install -y lsb-release  
RUN	apt install -y curl 
RUN	apt install -y gnupg1 
RUN	apt install -y gnupg2 
RUN	curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add - 
RUN	curl https://packages.microsoft.com/config/ubuntu/$(lsb_release -rs)/prod.list > /etc/apt/sources.list.d/mssql-release.list 
RUN	apt-get update -y 
RUN	ACCEPT_EULA=Y apt-get install -y msodbcsql18 
RUN	ACCEPT_EULA=Y apt-get install -y mssql-tools18 
RUN	echo 'export PATH="$PATH:/opt/mssql-tools18/bin"' >> ~/.bashrc 
#RUN	source ~/.bashrc 
RUN	apt install -y unixodbc-dev 
RUN	apt install -y pip 
RUN	pip install pyodbc 
RUN	pip install pandas 
RUN	pip install xlrd 
RUN	pip install openpyxl 
RUN	pip install xlsxwriter 
RUN	pip install pandas 

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get -y install pip && \
pip3 install selenium  && \
apt-get install wget && \
apt-get install -y chromium-browser && \
wget -P ~/downloads/ https://chromedriver.storage.googleapis.com/103.0.5060.53/chromedriver_linux64.zip && \
cd root/downloads && \
apt-get install unzip && \
unzip chromedriver_linux64.zip && \
chmod +x /root/downloads/chromedriver && \
mv ~/downloads/chromedriver /usr/local/share/chromedriver && \
ln -s /usr/local/share/chromedriver /usr/bin/chromedriver

RUN wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
RUN apt --fix-broken install
#RUN apt install -y google-chrome-stable
#RUN apt install -y google-chrome-stable
RUN wget -q https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
RUN apt-get install -y ./google-chrome-stable_current_amd64.deb

#ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get -y install ssh
RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd
RUN echo 'root:patagonia' | chpasswd
#RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config
RUN sed 's@session\srequired\spam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile
#CMD ["/usr/sbin/sshd", "-D"]
RUN apt install -y default-jre

RUN apt-get -y install tzdata
#RUN apt-get install -y nginx
RUN service ssh start
#CMD "nginx" "-g" "daemon off;"
CMD /usr/sbin/sshd -D
