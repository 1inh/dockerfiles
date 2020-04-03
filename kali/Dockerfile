# From the Kali linux base image
FROM kalilinux/kali-linux-docker
# Update and apt install programs
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get dist-upgrade -y && \
    apt-get install -y \
        awscli curl openssl git gdb gobuster john man-db \
        tmux nmap sqlmap sslscan testssl.sh python3-pip net-tools \
        hping3 wfuzz hash-identifier netcat whois jq wget \
        exploitdb sudo wordlists awscli openvpn \
        finger crunch cewl python-pip ncat ftp ssh exiftool hydra && \
    apt-get clean

# install shodan
RUN pip3 install shodan

# Set entrypoint and working directory
WORKDIR /root/
