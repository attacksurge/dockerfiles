## Usage

`cat input| docker run -t --rm -i --mount type=bind,source="$(pwd)",target=/data corsy | tee output`
