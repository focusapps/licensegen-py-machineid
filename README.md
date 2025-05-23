# py-machineid

[![CI](https://github.com/focusapps/licensegen-py-machineid/actions/workflows/test.yml/badge.svg)](https://github.com/focusapps/licensegen-py-machineid/actions)
[![PyPI version](https://badge.fury.io/py/py-machineid.svg)](https://badge.fury.io/py/py-machineid)

Get the unique machine ID of any host (without admin privileges).

_A fair source software licensing and distribution API._

## Install

Install using [`pip`](https://docs.python.org/3/installing/index.html):

```bash
python3 -m pip install py-machineid
```

## Usage

To obtain the raw GUID of the device, use `id() -> str`:

```python
import machineid

print(machineid.id())
```

To obtain an anonymized (hashed) version of the GUID, see below. The
`hashed_id(str) -> str` function takes an optional application ID,
which will ensure a unique ID per-app for the same device.

```python
import machineid

print(machineid.hashed_id('myappid'))
print(machineid.hashed_id())
```

Both `id()` and `hashed_id()` accept a `winregistry: bool` kwarg,
which can be used to disable the registry query on Windows (enabled
by default). Depending on your security posture, disabling the
registry query may help prevent machine fingerprints from
being manually modified by a bad actor.

## Testing

To run tests, invoke `unittest`:

```bash
python3 -m unittest
```

## Building

To build a release, run:

```bash
python3 setup.py sdist bdist_wheel
```

## Publishing

To publish a release, run:

```bash
twine upload dist/*
```

## Thanks

Special thanks to Denis Brodbeck for his Go package, [`machineid`](https://github.com/denisbrodbeck/machineid).
