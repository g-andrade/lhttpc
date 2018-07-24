# Migration Plan
Whenever there's an interface breaking change (a change in the project's major version),
required migration instructions will be detailed in this file.

## UNRELEASED
### Update
- calls to lhttpc:request/{4,5,6,9} requesting HTTPS URLs which you **do** need to keep
  insecure, and only if you need to do so, by explicitly using the new `verify_ssl_cert` option:
```erlang
% before:
lhttpc:request("https://self-signed.badssl.com", "GET", [], <<>>, 5000).

% after:
lhttpc:request("https://self-signed.badssl.com", "GET", [], <<>>, 5000,
               [{verify_ssl_cert, false}]).
```
### Other info
- new dependencies:
    - `certifi` (version 2.3.1)
    - `ssl_verify_fun` (version 1.1.4)
