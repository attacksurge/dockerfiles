FROM python:alpine3.15 AS compile-image

RUN apk add --no-cache build-base libffi-dev libxml2-dev libxslt-dev git
RUN git clone https://github.com/devanshbatham/OpenRedireX.git 
RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
RUN python -m pip install --upgrade pip
RUN python --version
RUN pip3 install aiohttp -q

FROM python:alpine3.15
COPY --from=compile-image /opt/venv /opt/venv
COPY --from=compile-image /OpenRedireX/ /OpenRedireX/
ENV PATH="/opt/venv/bin:$PATH"
WORKDIR /OpenRedireX

ENTRYPOINT ["python3", "-u", "openredirex.py"]
