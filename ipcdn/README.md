## Usage

`cd ipcdn && docker build . -t ipcdn`


`docker run -it --rm --mount type=bind,source="$(pwd)",target=/data ipcdn -c "cat data/input | /bin/ipcdn -m not | tee data/output"`
