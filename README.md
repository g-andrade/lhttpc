# lhttpc [![GitHub Actions CI][ci-img]][ci]

[ci]: https://github.com/miniclip/lhttpc
[ci-img]: https://github.com/miniclip/lhttpc/workflows/build/badge.svg

`lhttpc` is a **lightweight** HTTP client.

## Usage

```erlang
URL = "https://www.google.com",
Method = get,
Hdrs = [],
Timeout = 5000, % in milliseconds

lhttpc:request(URL, Method, Hdrs, Timeout).
```
