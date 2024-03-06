FROM python:alpine3.15 AS compile-image

RUN apk add --no-cache build-base libffi-dev libxml2-dev libxslt-dev git
RUN git clone https://github.com/ProjectAnte/dnsgen.git /dnsgen 
RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
RUN python -m pip install --upgrade pip
RUN python --version
RUN pip3 install --no-cache-dir -r /dnsgen/requirements.txt
RUN cd /dnsgen && python3 setup.py install

FROM python:alpine3.15
COPY --from=compile-image /opt/venv /opt/venv
COPY --from=compile-image /dnsgen /dnsgen/
ENV PATH="/opt/venv/bin:$PATH"
WORKDIR /dnsgen

ENTRYPOINT ["dnsgen", "-"]
