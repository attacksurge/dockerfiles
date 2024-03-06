FROM python:alpine3.15 as compile-image

RUN apk add --no-cache build-base libffi-dev libxml2-dev libxslt-dev git
RUN git clone https://github.com/devanshbatham/ParamSpider.git /ParamSpider
RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
RUN python -m pip install --upgrade pip
RUN python --version
RUN cd /ParamSpider && pip3 install .

FROM python:alpine3.15
COPY --from=compile-image /opt/venv /opt/venv
COPY --from=compile-image /ParamSpider /ParamSpider/
ENV PATH="/opt/venv/bin:$PATH"
WORKDIR /ParamSpider

ENTRYPOINT ["paramspider"]
