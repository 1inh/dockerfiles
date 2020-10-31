# From the Kali linux base image
FROM kalilinux/kali
# Update and apt install programs
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get dist-upgrade -y && \
    apt-get install -y \
	cewl \
	crunch \
	curl \
	dnsutils \
	host \
	exiftool \
	exploitdb \
	finger \
	ftp \
	gdb \
	git \
	gobuster \
	hashcat \
	hash-identifier \
	hping3 \
	hydra \
	john \
	jq \
	libcurl4-openssl-dev \
	libssl-dev \
	man-db \
	ncat \
	net-tools \
	netcat \
	nmap \
	openssl \
	openvpn \
	python-pip \
	python3-pip \
	sqlmap \
	ssh \
	sslscan \
	sudo \
	testssl.sh \
	tmux \
	vim \
	wget \
	whois \
	wordlists \
    && apt-get clean

# install shodan
RUN pip3 install --no-cache shodan

# install wfuzz
RUN pip3 install --no-cache --upgrade pycurl
RUN pip3 install --no-cache --upgrade wfuzz

# install awscli
RUN pip3 install --no-cache --upgrade awscli

# install pacu
# RUN git clone https://github.com/RhinoSecurityLabs/pacu /opt/pacu && cd /opt/pacu && bash /opt/pacu/install.sh

# install prowler
# RUN git clone https://github.com/toniblyx/prowler /opt/prowler

# Install Azure CLI
# RUN pip3 install --no-cache azure-cli

# Install kubectl
# COPY --from=dtzar/helm-kubectl /usr/local/bin/kubectl /usr/local/bin/kubectl

# Install helm binary
# COPY --from=dtzar/helm-kubectl /usr/local/bin/helm /usr/local/bin/helm

# Set entrypoint and working directory
WORKDIR /root/
