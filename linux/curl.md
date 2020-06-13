# Curl

## Prettify json output

### MacOS Setup

```bash
brew install jq
```

### Usage

```bash
curl https://api.1inch.exchange/v1.1/exchanges | jq
[
  {
    "name": "WETH"
  },
  ...
]

```
