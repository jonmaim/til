# Command-line arguments parsing

[Documentation](https://docs.python.org/3/library/argparse.html)

```python
import argparse

parser = argparse.ArgumentParser(description='Fetch some candles baby 🍹🕯.')
# nargs=1 means only one argument will be parsed
parser.add_argument('--timeframe', nargs=1, required=True, help='specify timeframe: 1h, 1d, ...')
args = parser.parse_args()
timeframe = args.timeframe
```
