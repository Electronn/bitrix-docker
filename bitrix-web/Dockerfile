FROM centos:7
RUN yum install wget -y
RUN wget http://repos.1c-bitrix.ru/yum/bitrix-env.sh
RUN chmod +x bitrix-env.sh
RUN sed -i 's/^disable_selinux$//g' bitrix-env.sh
RUN ./bitrix-env.sh
RUN yum install -y supervisor openssh-server ethtool net-tools
ADD httpd.ini /etc/supervisord.d/
ADD openssh.ini /etc/supervisord.d/
RUN sed -i 's/nodaemon=false/nodaemon=true/g' /etc/supervisord.conf
RUN /usr/bin/ssh-keygen -A
