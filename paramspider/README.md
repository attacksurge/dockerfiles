## Paramspider

[Source](https://github.com/devanshbatham/ParamSpider)

`docker build . -t axiom/paramspider` <br>
`docker run axiom/paramspider --domain tesla.com`

## Usage

To use `paramspider`, follow these steps:

```sh
paramspider -d example.com
```

## Examples

Here are a few examples of how to use `paramspider`:

- Discover URLs for a single domain:

  ```sh
  docker run axiom/paramspider -d example.com
  ```

- Discover URLs for multiple domains from a file:

  ```sh
  docker run axiom/paramspider -l domains.txt
  ```

- Stream URLs on the termial:

    ```sh 
    docker run axiom/paramspider -d example.com -s
    ```

- Set up web request proxy:

    ```sh
    docker run axiom/paramspider -d example.com --proxy '127.0.0.1:7890'
    ```
- Adding a placeholder for URL parameter values (default: "FUZZ"): 

  ```sh
  docker run axiom/paramspider -d example.com -p '"><h1>reflection</h1>'
  ```
