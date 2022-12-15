# ezmsg

Messaging and Multiprocessing.

`ezmsg` is a pure-python implementation of a directed acyclic graph (DAG) pub/sub messaging pattern based on [`labgraph`](https://github.com/facebookresearch/labgraph) which is optimized and intended for use in constructing real-time software.  `ezmsg` implements much of the `labgraph` API (with a few notable differences), and owes a lot of its design to the `labgraph` developers/project.

`ezmsg` is very fast and uses Python's (currently) new `multiprocessing.shared_memory` module to facilitate efficient message passing without C++ or any compilation/build tooling.

## Installation
`pip install ezmsg`

## Dependencies

Due to reliance on `multiprocessing.shared_memory`, `ezmsg` requires __minimum Python 3.8__. Beyond that, `ezmsg` is a pure Python library with no external dependencies.

Testing `ezmsg` requires: 
* `pytest`
* `pytest-cov`
* `pytest-asyncio`
* `numpy`

## Setup (Development)
``` bash
$ python3 -m venv env
$ source env/bin/activate
(env) $ pip install --upgrade pip
(env) $ pip install -e ".[test]"

(env) $ python -m pytest tests # Optionally, Perform tests
```

## Documentation
https://ezmsg.readthedocs.io/en/latest/

`ezmsg` is very similar to [`labgraph`](https://www.github.com/facebookresearch/labgraph), so you might get a primer with their documentation and examples. Additionally, there are many examples provided in the examples/tests directories strewn throughout this repository.

## Extensions
See the extension directory for more details
* `ezmsg-sigproc` -- Timeseries signal processing modules
* `ezmsg-websocket` -- Websocket server and client nodes for `ezmsg` graphs
* `ezmsg-zmq` -- ZeroMQ pub and sub nodes for `ezmsg` graphs
* ... More to come!

Every extension has its own set of additional dependencies.  Once ezmsg is installed, these can be installed manually with:
``` bash
(env) $ pip install -e extensions/[extension]
```

Once `ezmsg` has been packaged and is available on PyPI (which it isn't quite yet) you may have luck batch installing all extensions with:
``` bash
(env) $ pip install ".[all_ext]"
```
