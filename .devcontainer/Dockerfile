FROM nvidia/cuda:12.0.1-cudnn8-devel-ubuntu20.04

ARG DEBIAN_FRONTEND=noninteractive
ARG CUDA='cu121'

RUN apt update && \
    apt install -y bash \
                   build-essential \
                   git \
                   curl \
                   ca-certificates \
                   python3 \
                   python3-pip && \
    rm -rf /var/lib/apt/lists
RUN python3 -m pip install --no-cache-dir --upgrade pip 
RUN python3 -m pip install --pre torch  --index-url https://download.pytorch.org/whl/nightly/$CUDA
RUN python3 -m pip install transformers datasets
    
ENV SHELL /bin/zsh
RUN SNIPPET="export PROMPT_COMMAND='history -a' && export HISTFILE=/commandhistory/.zsh_history" \
    && echo "$SNIPPET" >> "/root/.zsh_history"
COPY .devcontainer/zsh-plugins/.p10k.zsh /root/








