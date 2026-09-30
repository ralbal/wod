FROM python:3.10-slim

WORKDIR /workspace

RUN python -m pip install --upgrade pip setuptools wheel && \
    python -m pip install waymo-open-dataset-tf-2-11-0==1.6.1

CMD ["bash"]