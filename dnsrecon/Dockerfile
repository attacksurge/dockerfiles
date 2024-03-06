FROM python:alpine3.15 AS compile-image

RUN apk add --no-cache build-base libffi-dev libxml2-dev libxslt-dev git
RUN git clone https://github.com/darkoperator/dnsrecon.git 
RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
RUN python -m pip install --upgrade pip
RUN python --version
RUN pip3 install --no-cache-dir -r /dnsrecon/requirements.txt

FROM python:alpine3.15
COPY --from=compile-image /opt/venv /opt/venv
COPY --from=compile-image /dnsrecon/ /dnsrecon/
ENV PATH="/opt/venv/bin:$PATH"
WORKDIR /dnsrecon

ENTRYPOINT ["python3","dnsrecon.py"]
                                     
