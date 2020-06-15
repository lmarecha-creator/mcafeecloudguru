FROM centos:centos8.1.1911
MAINTAINER adrianp@stindustries.net

# If you need to use a proxy to get to the internet, build with:
#   docker build --build-arg CURL_OPTIONS="..."
#
# The default is empty (no special options).
#
ARG CURL_OPTIONS=""

# Prep environment
#
#RUN yum groupinstall "Development tools" -y 

# Install build utils
#
RUN touch /var/lib/rpm/* && \
    yum -y install gnutls-devel gcc  gcc-c++ && \
    yum clean all

# wget - command line utility (installed via. RPM)
#
# https://www.cvedetails.com/cve/CVE-2014-4877/
#
RUN curl -LO ${CURL_OPTIONS} \
   http://mirror.centos.org/centos/7/os/x86_64/Packages/wget-1.14-18.el7_6.1.x86_64.rpm  && \
    yum -y install wget-1.14-18.el7_6.1.x86_64.rpm && \
    rm *.rpm

# wget - command line utility (manual install)
#
# https://www.cvedetails.com/cve/CVE-2014-4877/
#
# Precautionary failure with messages

CMD echo 'McAfee Vulnerable Containers LAB - Vulnerable image' && /bin/false

# Basic labels.
# http://label-schema.org/
#
LABEL \
    org.label-schema.name="McAfee-lab-CVEs-bad-dockerfile" \
    org.label-schema.description="Reference Dockerfile containing software with known vulnerabilities." \
    org.label-schema.url="http://www.stindustries.net/docker/bad-dockerfile/" \
    org.label-schema.vcs-type="Git" \
    org.label-schema.vcs-url="https://github.com/ianmiell/bad-dockerfile" \
    org.abel-schema.docker.dockerfile="/Dockerfile"
