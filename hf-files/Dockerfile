FROM python:3.13 AS downloader
ENV DEBIAN_FRONTEND=noninteractive
RUN apt -y update && apt -y install tree file
RUN pip install -U "huggingface_hub[cli]"
ARG HF_MODEL="TinyLlama/TinyLlama-1.1B-Chat-v1.0"
RUN hf download "${HF_MODEL}" --local-dir /model && rm -rf /root/.cache/huggingface && du -h -x -d 3 /model && tree -h /model

FROM scratch
COPY --from=downloader /model /
