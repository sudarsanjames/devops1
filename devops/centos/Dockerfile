FROM centos:6.7 
#MAINTAINER Jeganathan Swaminathan <jegan@tektutor.org> <http://www.tektutor.org> 
MAINTAINER	Sudarsan James

RUN yum install -y openssh-server openssh-clients python

# Set the password of root user to root
RUN echo 'root:root' | chpasswd

RUN usermod -aG wheel root 
RUN useradd -d /home/tester -g root tester

##For key based authentication
RUN sed -ri 's/^session\s+required\s+pam_loginuid.so$/session optional pam_loginuid.so/' /etc/pam.d/sshd

# Disable root login &
# Disable password login, only allow public key. 
##COPY sshd_config /etc/ssh/sshd_config
COPY sudoers /etc/sudoers

RUN mkdir -p /root/.ssh
COPY authorized_keys /root/.ssh/authorized_keys
COPY authorized_keys /.ssh/authorized_keys
COPY authorized_keys /etc/ssh/authorized_keys

# Add sshd running directory.
##RUN mkdir -m 755 /var/run/sshd
RUN mkdir -m 700 /var/run/sshd

# Add ssh key directory.
RUN /sbin/service sshd start && /sbin/service sshd stop

EXPOSE 22
EXPOSE 80
CMD ["/usr/sbin/sshd", "-D"]


##docker build -t james/ansible-centos .
##docker run -d --name centos1 -p 3001:22 -p 9001:80 james/ansible-centos
##docker run -d --name centos3 -h myserver1 -p 3003:22 -p 9003:80 james/ansible-centos
###docker run -d --name ubuntu1 -p 2001:22 -p 8001:80 james/ansible-ubuntu-1
##docker  inspect centos2 | grep -i IPA
##docker  inspect centos3 | grep -i Hostname
## ssh -p 3001 root@localhost
## ssh -p 3003 root@myserver1


### ansible all -m ping     ==> only if you have ansible.cfg
### ansible -i hosts  all -m ping
