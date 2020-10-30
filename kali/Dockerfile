# From the Kali linux base image
FROM kalilinux/kali
# Update and apt install programs
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get dist-upgrade -y && \
    apt-get install -y \
        awscli curl openssl git gdb gobuster john man-db \
        tmux nmap sqlmap sslscan testssl.sh python3-pip net-tools \
        hping3 hash-identifier netcat whois jq wget libcurl4-openssl-dev \
        exploitdb sudo wordlists awscli openvpn dnsutils host \
        finger crunch cewl python-pip ncat ftp ssh exiftool hydra && \
    apt-get clean

# install shodan
RUN pip3 install shodan
RUN pip3 install --upgrade pycurl
RUN pip3 install --upgrade wfuzz

# Set entrypoint and working directory
WORKDIR /root/
