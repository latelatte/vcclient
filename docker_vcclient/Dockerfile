# FROM nvidia/cuda:11.8.0-cudnn8-runtime-ubuntu22.04
# FROM nvidia/cuda:12.0.1-cudnn8-runtime-ubuntu22.04
FROM --platform=linux/amd64 nvidia/cuda:11.8.0-cudnn8-runtime-ubuntu22.04


RUN apt-get update \
        && apt-get install -y python3-pip espeak gosu libsndfile1-dev emacs git \
        && apt-get clean \
        && rm -rf /var/lib/apt/lists/*

WORKDIR /
ADD dummy /

RUN git clone https://github.com/latelatte/vcclient.git



RUN chmod 0777 /vcclient/server
WORKDIR /vcclient/server
RUN pip install numpy==1.23.5 \
        && pip install pyworld==0.3.3 --no-build-isolation \
        && pip install -r requirements.txt


ADD /setup.sh  /vcclient/server
ADD /exec.sh  /vcclient/server


ENTRYPOINT ["/bin/bash", "setup.sh"]
