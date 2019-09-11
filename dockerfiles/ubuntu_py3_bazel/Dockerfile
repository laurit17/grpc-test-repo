FROM ubuntu:18.04

RUN apt-get update && apt-get install -y \
  docker.io \
  git \
  python \
  python-pip \
  python3 \
  python3-pip \
  unzip \
  wget \
  zip

RUN pip3 install awscli keyring
RUN pip3 install --upgrade aws-credential-client --index-url https://docker.int.uberatc.com/artifactory/api/pypi/pypi/simple/ --trusted-host docker.int.uberatc.com --no-cache-dir


RUN cd /tmp && \
  wget https://github.com/bazelbuild/bazel/releases/download/0.28.1/bazel-0.28.1-installer-linux-x86_64.sh && \
  chmod 777 bazel-0.28.1-installer-linux-x86_64.sh && \
  ./bazel-0.28.1-installer-linux-x86_64.sh --user
ENV PATH "$PATH:$HOME/bin"
