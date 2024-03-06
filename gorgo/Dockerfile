FROM python:3.7-slim AS compile-image
RUN apt-get update
RUN apt-get install -y --no-install-recommends git build-essential gcc
RUN git clone https://github.com/pry0cc/gorgo.git
RUN apt install medusa -y -qq

RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"

RUN pip install -r /gorgo/requirements.txt

FROM python:3.7-slim
COPY --from=compile-image /opt/venv /opt/venv
COPY --from=compile-image /usr/bin/medusa /usr/bin/medusa
COPY --from=compile-image /gorgo/ /gorgo/


ENV PATH="/opt/venv/bin:$PATH"
ENV HOME /
WORKDIR /gorgo
ENTRYPOINT ["/gorgo/gorgo.py"]
