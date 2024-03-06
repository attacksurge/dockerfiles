FROM debian:stable as build

ENV DEBIAN_FRONTEND noninteractive

ADD https://nmap.org/dist/nmap-7.92.tgz ./nmap.tar.gz
RUN apt-get -q update && \
    apt-get -qy --no-install-recommends install build-essential libssl-dev flex bison && \
    tar zxf nmap.tar.gz && \
    mv nmap-* nmap && \
    cd nmap && \
    ./configure --without-ndiff --without-zenmap --without-nping \
                --without-ncat --without-nmap-update \
                --with-libpcap=included && \
    make && make install && \
    cd ../ && rm -rf nmap nmap.tar.gz && \
    apt-get -qy --purge autoremove build-essential libssl-dev flex bison && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

FROM debian:stable-slim
COPY --from=build /usr/local/bin/nmap /bin/nmap
ENV HOME /
ENTRYPOINT ["/bin/nmap"]
