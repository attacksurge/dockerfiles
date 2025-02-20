FROM python:alpine3.15 AS compile-image

RUN apk add --no-cache build-base libffi-dev
RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
RUN python -m pip install --upgrade pip && \
    python -m pip install dnsgen

FROM python:alpine3.15
COPY --from=compile-image /opt/venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"

ENTRYPOINT ["dnsgen", "-"]
