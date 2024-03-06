FROM python:3.9-slim AS compile-image
RUN apt update
RUN apt install -y git
RUN git clone https://github.com/s0md3v/Corsy.git
RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
RUN cd Corsy && pip install -r requirements.txt

FROM python:3.9-slim
COPY --from=compile-image /opt/venv /opt/venv
COPY --from=compile-image /Corsy/ /Corsy/
ENV PATH="/opt/venv/bin:$PATH"

WORKDIR /Corsy

ENTRYPOINT ["python3", "corsy.py"]
