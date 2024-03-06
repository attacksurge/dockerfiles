## Usage

`docker run -t --rm -i --mount type=bind,source="$(pwd)",target=/data openredirex -l /data/input --keyword FUZZ -p /data/leaky-paths.txt`
