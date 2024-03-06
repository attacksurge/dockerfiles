## Usage

```
docker image build - < Dockerfile -t axiom/cero

docker run --rm -i --mount type=bind,source="$(pwd)",target=/data axiom/cero -c 1000 < input | tee output
```

## Manual

```
usage: cero [options] [targets]
if [targets] not provided in commandline arguments, will read from stdin

options:
  -c int
        Concurrency level (default 100)
  -d    Output only valid domain names (e.g. strip IPs, wildcard domains and gibberish)
  -p string
        TLS ports to use, if not specified explicitly in host address. Use comma-separated list (default "443")
  -t int
        TLS Connection timeout in seconds (default 4)
  -v    Be verbose: Output results as 'addr -- [result list]', output errors to stderr as 'addr -- error message'
```
