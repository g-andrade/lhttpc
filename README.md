# lhttpc

![build](https://github.com/miniclip/lhttpc/workflows/build/badge.svg)
[![erlang][erlang badge]][erlang downloads]

[erlang badge]: https://img.shields.io/badge/erlang-%3E%3D19.3-lightgrey
[erlang downloads]: http://www.erlang.org/download

`lhttpc` is a **lightweight** HTTP client.

## Usage

```erlang
URL = "https://www.google.com",
Method = get,
Hdrs = [],
Timeout = 5000, % in milliseconds

lhttpc:request(URL, Method, Hdrs, Timeout).
```
