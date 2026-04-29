FROM jenkins/inbound-agent
USER root

RUN apt update
RUN apt install -y unzip git-ftp
# Install Node.js
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - &&\
    apt install -y nodejs

# Install Sonar Scanner
RUN curl -L -O https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-5.0.1.3006-linux.zip
RUN unzip sonar-scanner-cli-5.0.1.3006-linux.zip
RUN mkdir sonar-scanner
RUN cd sonar-scanner-5.0.1.3006-linux && mv bin conf jre lib ../sonar-scanner
RUN rm sonar-scanner-cli-5.0.1.3006-linux.zip
RUN rmdir sonar-scanner-5.0.1.3006-linux
ENV PATH="$PATH:/home/jenkins/sonar-scanner/bin/"

RUN curl -fsSL https://get.docker.com -o get-docker.sh
RUN sh get-docker.sh