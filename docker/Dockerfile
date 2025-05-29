#FROM dustynv/nano_llm:24.5-r36.2.0
# FROM llamacpp:r36.4.3-llama_cpp
# BUILD llamacpp:r36.4.3-llama_cpp this image with: 
# jetson-containers build --name=llamacpp triton llama_cpp

# https://hub.docker.com/u/dustynv
FROM  dustynv/cuda:12.2-r36.2.0

USER root
# https://forums.developer.nvidia.com/t/libopenblas-so-0-not-found/264406
RUN apt update && apt install -y vim libopenblas-dev pip git
RUN pip install cmake==3.25.0 

# https://github.com/abetlen/llama-cpp-python/issues/1779#issuecomment-2396550099
#https://medium.com/@ryan.stewart113/a-simple-guide-to-enabling-cuda-gpu-support-for-llama-cpp-python-on-your-os-or-in-containers-8b5ec1f912a4
# RUN CUDACXX=/usr/local/cuda/bin/nvcc CMAKE_ARGS="-DGGML_CUDA=on -DCMAKE_CUDA_ARCHITECTURES=native" FORCE_CMAKE=1 VIRTUAL_ENV=/root/venv-3.10-llama_cpp-CUDA uv pip install llama-cpp-python --no-cache-dir --force-reinstall --upgrade

RUN pip uninstall --yes transformers
RUN pip install transformers

# https://llm.mlc.ai/docs/install/mlc_llm.html
#RUN curl -y --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
RUN apt install -y cargo

ENV MLC_LLM_SOURCE_DIR=/workspace/mlc-llm
ENV PYTHONPATH=$MLC_LLM_SOURCE_DIR/python:$PYTHONPATH



