FROM lscr.io/linuxserver/code-server:latest

RUN apt update && apt install -y \
    jq \
    make \
    unzip \
    wget \
    zip

ARG TFENV_VERSION=v2.2.2
ARG TERRAFORM_VERSION=1.3.8
RUN git clone https://github.com/tfutils/tfenv.git --depth 1 --branch ${TFENV_VERSION} ~/.tfenv && \
    ln -s ~/.tfenv/bin/* /usr/local/bin/ && \
    tfenv install ${TERRAFORM_VERSION} && \
    tfenv use ${TERRAFORM_VERSION}

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