<img src='https://user-images.githubusercontent.com/1423657/173144443-fc7ba783-d5bf-47f9-bf59-707693da5ed1.png' style="margin-left:-10px" width=125/>

# qryn-k6

Testing [qryn](https://qryn.dev) using [xk6-loki](https://grafana.com/blog/2022/06/08/a-quick-guide-to-load-testing-grafana-loki-with-grafana-k6/)

Grafana k6 is a modern and scriptable load-testing tool, featuring an extension that allows simulating real-world LogQL load to test the scalability, reliability, and performance of your qryn installation.


## Getting started

1. Install `xk6`

   ```bash
   GOBIN=/usr/local/bin/ go install go.k6.io/xk6/cmd/xk6@latest
   ```

2. Checkout `grafana/xk6-loki`

   ```bash
   git clone https://github.com/grafana/xk6-loki
   cd xk6-loki
   ```

3. Build xk6-loki

   ```bash
   make k6
   ```
   
Once the extension is built, use the resulting binary to execute a load test files written in Javascript.

## Testing
Use the examples folder as a starting point to create custom load test scripts
```
./k6 run examples/simple.js
```

### Multi-Tenance
If Loki is configured in multi-tenant mode but you want to use xk6-loki in single user mode, you can specify the username, and optionally also the password, in the user info part of the URL. It would look like this:

`const conf = loki.Config(“http://username[:password]@localhost:3100”)`

This way, every request, both for pushing and querying logs, is done using the same X-Scope-OrgID header across all VUs on the load test. Otherwise, k6 will attempt using a different X-Scope-OrgID for each VU in the load test. 

### qryn.cloud
When testing with `qryn-cloud` the Customer injected OrgIDs are ignored and auto-injected by the edge upon authentication.
