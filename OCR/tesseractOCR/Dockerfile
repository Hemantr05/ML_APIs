FROM python:3.9.9-slim

WORKDIR /app
COPY ./requirements.txt /app/requirements.txt
RUN apt-get update && \
    apt install gcc g++ libgeos-dev -y && \
    apt install poppler-utils ffmpeg libsm6 libxext6 libgl1-mesa-glx -y && \
    pip install --upgrade pip && \
    pip install --no-cache-dir --upgrade -r /app/requirements.txt

COPY ./main.py /app/main.app
COPY ./tess_ocr.py /app/tess_ocr.py
COPY ./utils.py /app/utils.py

EXPOSE 8080

CMD ["unvicorn", "main:app", "--host", "0.0.0.0", "--port", "8080"]
