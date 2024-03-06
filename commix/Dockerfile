FROM python:3.7-slim AS compile-image
RUN apt-get update
RUN apt-get install -y --no-install-recommends git 
RUN git clone https://github.com/commixproject/commix.git

RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"

FROM python:3.7-slim
COPY --from=compile-image /opt/venv /opt/venv
COPY --from=compile-image /commix/ /commix/

ENV PATH="/opt/venv/bin:$PATH"
ENV HOME /
WORKDIR /commix
ENTRYPOINT ["/commix/commix.py"]
