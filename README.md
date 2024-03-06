# dockerfiles

This repository contains various dockerized tools used in security assesments with a focus on minimazing image size.

To reduce the size of the docker image, we use [multi-stage](https://docs.docker.com/build/building/multi-stage/) builds and selectively copy artifacts from one stage to another, leaving behind everything we don't want in the final image.

For example [openredirex](https://github.com/ax-ng/dockerfiles/blob/main/openredirex/Dockerfile):

```
##########################################################
# Use Python Alpine as a base image named "compile-image"
#
FROM python:alpine3.15 AS compile-image
#
##########################################################
# Install dependencies needed on the base image
#
RUN apk add --no-cache build-base libffi-dev libxml2-dev libxslt-dev git
#
##########################################################
# Git clone the tool to the base image
#
RUN git clone https://github.com/devanshbatham/OpenRedireX.git
#
##########################################################
# Create a Python Virtual Environment on the base image
#
RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
#
##########################################################
# Install aiohttp dependency via pip on the base image
#
RUN python -m pip install --upgrade pip
RUN python --version
RUN pip3 install aiohttp -q
#
##########################################################
# Start a new Docker build stage with a fresh Python Alpine
#
FROM python:alpine3.15
#
##########################################################
# Copy the Python Virtual Environment from the base image to final image
#
COPY --from=compile-image /opt/venv /opt/venv
#
##########################################################
# Copy the OpenRedireX tool folder from base image to final image
#
COPY --from=compile-image /OpenRedireX/ /OpenRedireX/
#
##########################################################
# Add Python Virtual Environment to path to final image
#
ENV PATH="/opt/venv/bin:$PATH"
#
##########################################################
# Set the working directory
#
WORKDIR /OpenRedireX
#
##########################################################
# Set the Docker Entrypoint
#
ENTRYPOINT ["python3", "-u", "openredirex.py"]
```

Building the above Docker image **without** multi-stage builds results in a image size of 335MB <br>
Building the above Docker image **with** multi-stage builds reduces the image size to 84MB.
