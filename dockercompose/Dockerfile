#ARG 		BASE_IMAGE
FROM	 	centos:7.6.1810
RUN 		yum update -y 
RUN 		yum install python36 -y
RUN             yum install epel-release -y
RUN 		pip3.6 install --upgrade pip

#Установка русского языка
RUN 		yum -y install glibc-common
RUN 		localedef -c -f UTF-8 -i ru_RU ru_RU.UTF-8
RUN 		yum reinstall -y glibc-common
COPY		i18n /etc/sysconfig/i18n
#RUN		export LANG=ru_RU.UTF-8
ARG 		RUS_LANG
ENV		LANG=${RUS_LANG}

#Меняем ссылку на python3.6
#RUN 		unlink /usr/bin/python
#RUN 		ln -s /usr/bin/python3.6 /usr/bin/python

#/*************************
WORKDIR 	/app
RUN 		pip install flask redis
ADD 		app2.py /app/app2.py
EXPOSE 		80
CMD 		["python3.6", "app2.py"]
