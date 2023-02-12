FROM lscr.io/linuxserver/code-server:latest

RUN apt update && apt install -y \
    jq \
    make \
    unzip \
    wget \
    zip

ARG TERRAFORM_VERSION=1.3.8
RUN wget https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    rm terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    mv terraform /usr/local/bin

# HELM
ARG HELM_VERSION=v3.5.4
RUN cd /tmp && \
    wget https://get.helm.sh/helm-${HELM_VERSION}-linux-amd64.tar.gz --no-proxy && \
    tar xf helm-${HELM_VERSION}-linux-amd64.tar.gz && \
    chmod a+x ./linux-amd64/helm && \
    mv ./linux-amd64/helm /usr/local/bin/

#Kubectl
ARG KUBECTL_VERSION=v1.26.1
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/${KUBECTL_VERSION}/bin/linux/amd64/kubectl \
  && chmod +x ./kubectl \
  && mv ./kubectl /usr/local/bin