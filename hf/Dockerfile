ARG TOOL_IMAGE=ghcr.io/rpardini/vllm-k8s-image-volume:cpu-amd64-noavx512-latest
FROM ${TOOL_IMAGE} AS builder

ARG HF_MODEL="TinyLlama/TinyLlama-1.1B-Chat-v1.0"

RUN huggingface-cli download ${HF_MODEL}

RUN du -h -x -d 3 /root/.cache/huggingface || true


FROM scratch
COPY --from=builder /root/.cache/huggingface /huggingface
