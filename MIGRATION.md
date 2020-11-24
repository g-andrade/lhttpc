# Migration guide

Whenever there's an interface breaking change (a change in the project's major version),
required migration instructions will be detailed in this file.

## From [3.x] to [4.x]
### Update
- your code to depend on types from `lhttpc:` and `lhttpc_client:` and not (imported)
`lhttpc_types.hrl` (a simple `dialyzer` procedure should put into evidence what is mis-specified)
- your code to not depend on `lhttpc.hrl`'s `lhttpc_url` record:
  - if you're "building" the record, you can use
`lhttpc_client:new_url(Host, Port, Path, IsSSL, User, Password)` where you were once using
`#lhttpc_url{ host = Host,
              port = Port,
              path = Path,
              is_ssl = IsSSL,
              user = User,
              password = Password }`
(`lhttpc_client:new_url/4` also available, for convenience)
- your code to access the `lhttpc_url` record content via new accessor functions
`lhttpc_client:url(LhttpcURL, FieldName)`

### Remove
- your code's import of `lhttpc_types.hrl`
- your code's import of `lhttpc.hrl`

## From [2.x] to [3.x]
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
