<img src='https://user-images.githubusercontent.com/1423657/173144443-fc7ba783-d5bf-47f9-bf59-707693da5ed1.png' style="margin-left:-10px" width=125/>

# qryn-k6

Testing [qryn](https://qryn.dev) using [xk6-loki](https://grafana.com/blog/2022/06/08/a-quick-guide-to-load-testing-grafana-loki-with-grafana-k6/)

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
