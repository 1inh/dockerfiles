FROM alpine:latest

# Install base tools
RUN apk --no-cache update && \
	apk add gcc \
	git \
	vim \
	wget \
	curl \
	make \
	nmap \
	nmap-ncat \
	whois \
	python \
	python3 \
	py-pip \
	bash \
	perl \
	nikto \
	net-tools \
	dnsrecon \
	go \
	john \
	docs \
	aircrack-ng \
	tmux \
	whois \
	jq \
	openssh-client \
	exiftool \
	bind-tools \
	ca-certificates \
	py-crcmod \
	libc6-compat \
	socat \
	openssl \
	libffi-dev \
	musl-dev \
	openssl-dev \
	python-dev \
	&& rm -rf /var/cache/apk/*

# Install AWS CLI
RUN pip install --no-cache --upgrade awscli

RUN git clone https://github.com/RhinoSecurityLabs/pacu /opt/pacu && cd /opt/pacu && bash /opt/pacu/install.sh
RUN git clone https://github.com/toniblyx/prowler /opt/prowler

# Install Gcloud SDK
ARG CLOUD_SDK_VERSION=240.0.0
ENV CLOUD_SDK_VERSION=$CLOUD_SDK_VERSION
ENV PATH /google-cloud-sdk/bin:$PATH
RUN curl -O https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-${CLOUD_SDK_VERSION}-linux-x86_64.tar.gz && \
    tar xzf google-cloud-sdk-${CLOUD_SDK_VERSION}-linux-x86_64.tar.gz && \
    rm google-cloud-sdk-${CLOUD_SDK_VERSION}-linux-x86_64.tar.gz && \
    ln -s /lib /lib64 && \
    gcloud config set core/disable_usage_reporting true && \
    gcloud config set component_manager/disable_update_check true && \
    gcloud config set metrics/environment github_docker_image && \
    gcloud --version

# Install Azure CLI
RUN pip install --no-cache azure-cli

# Install kubectl
COPY --from=dtzar/helm-kubectl /usr/local/bin/kubectl /usr/local/bin/kubectl

# Install helm binary
COPY --from=dtzar/helm-kubectl /usr/local/bin/helm /usr/local/bin/helm

# Install Docker client
ARG DOCKER_CLI_VERSION="17.06.2-ce"
ENV DOWNLOAD_URL="https://download.docker.com/linux/static/stable/x86_64/docker-$DOCKER_CLI_VERSION.tgz"
RUN mkdir -p /tmp/download \
    && curl -L $DOWNLOAD_URL | tar -xz -C /tmp/download \
    && mv /tmp/download/docker/docker /usr/local/bin/ \
    && rm -rf /tmp/download

WORKDIR /root/

# Install amass
ENV GO111MODULE=on
RUN go get -v -u github.com/OWASP/Amass/v3/...
ENV GOPATH=/root/go/
ENV PATH="/root/go/bin:$PATH"
