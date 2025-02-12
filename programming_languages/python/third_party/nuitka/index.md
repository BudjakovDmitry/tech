# Nuitka

## Download

```shell
python -m pip install -U nuitka
```

## Command line usage

Example: `hello.py`

```python
def talk(message):
    return "Talk " + message

def main():
    print(talk("Hello world"))

if __name__ == "__main__":
    main()
```

Build it:

```shell
python -m nuitka hello.py
```

## Options

### help

```shell
python -m nuitka --help
```
