# FROM ubuntu

# RUN apt-get update -y && apt-get -y upgrade \
# 	&& apt-get -y install \
# 	wget \
# 	openssh-server \
# 	ca-certificates \
# 	postfix

# RUN wget \
# 	https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh \
# 	&& chmod 777 ./script.deb.sh && ./script.deb.sh
# RUN apt-get install -y tzdata gitlab-ce

# EXPOSE 443 80 22

# ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && sleep 2 && gitlab-ctl reconfigure && tail -f /dev/null

# # docker run -p 8080:80 -p 8022:22 -p 8443:443 192.168.99.106

FROM ubuntu:18.04

RUN apt-get update && \
	apt-get upgrade -y && apt-get install -y dialog apt-utils && \
	apt-get install -y curl openssh-server ca-certificates postfix
	
RUN	curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash && \
	apt-get install -y gitlab-ce tzdata && \
	apt update && apt-get clean

EXPOSE 80 22 443

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null

# Build Image
# docker build -t ex03 .

# Create Container
# docker run --name ex03 -it --rm -p 80:80 -p 22:22 -p 443:443 --privileged ex03