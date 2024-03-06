FROM python:alpine3.15 AS compile-image

RUN apk add --no-cache build-base libffi-dev libxml2-dev libxslt-dev git
RUN git clone https://github.com/GerbenJavado/LinkFinder.git
RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
RUN python -m pip install --upgrade pip
RUN python --version
RUN cd /LinkFinder/ ; pip3 install --no-cache-dir -r requirements.txt ; python3 setup.py install

FROM python:alpine3.15
COPY --from=compile-image /opt/venv /opt/venv
COPY --from=compile-image /LinkFinder/ /LinkFinder/
ENV PATH="/opt/venv/bin:$PATH"
WORKDIR /LinkFinder

ENTRYPOINT ["python3", "-u", "linkfinder.py"]
