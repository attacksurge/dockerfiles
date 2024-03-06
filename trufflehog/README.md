## Usage

`cd trufflehog && docker build . -t trufflehog`

`docker run -it -v "$PWD:/pwd" trufflehog github --repo https://github.com/trufflesecurity/test_keys`
