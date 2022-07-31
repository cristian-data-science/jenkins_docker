FROM ubuntu:20.04
USER root

RUN apt-get update 
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
	
