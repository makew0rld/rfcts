# rfcts

This repo contains of couple of Bash scripts for creating and verifying [RFC 3161](https://datatracker.ietf.org/doc/html/rfc3161) timestamps. You can learn more about trusted timestamping and the context for this repo in my [blog post](https://makeworld.space/2023/09/time_for_timestamping.html).

```
$ ./rfcts
help: ./rfcts [-s/--server URL] [-o/--out FILE.TSR]

$ ./rfcts myfile.jpg
Using configuration from /etc/ssl/openssl.cnf
Created myfile.jpg.tsr

$ ./rfcts-verify
help: ./rfcts-verify DATA_FILE TSR_FILE

$ ./rfcts-verify myfile.jpg myfile.jpg.tsr
Verification: OK
Time stamp: Sep  7 04:00:48 2023 GMT

$ ./rfcts-verify myfile.jpg bad.tsr
Verification: FAILED
```

The default timestamp authority is [DigiCert](https://knowledge.digicert.com/generalinformation/INFO4231.html), as they are a reputable and established organization.

By default the verify script uses the system trust store for root certs. This will not work for timestamp authorities that don't sign using CA-signed certs, such as freeTSA.org.

## License

Public domain, using the Unlicense. See [LICENSE](./LICENSE) for details.
