# Certificates

```bash
kubectl -n logging-system get certificates
kubectl -n logging-system get issuers
kubectl -n logging-system get secrets
```

```bash
kubectl -n logging-system get secrets elasticsearch-ca-tls \
        -o jsonpath="{.data.tls\.crt}" | base64 -d | openssl x509 -noout -text

kubectl -n logging-system get secrets elasticsearch-ca-ends-tls \
        -o jsonpath="{.data.tls\.crt}" | base64 -d | openssl x509 -noout -text
```

```bash
kubectl  exec -it -n logging-system elasticsearch-aio-0 -- openssl x509 -noout -text -in config/certs/ca.crt
kubectl  exec -it -n logging-system elasticsearch-aio-0 -- openssl x509 -noout -text -in config/certs/tls.crt
```

# Deployment

```bash
kubectl -n logging-system get pods
kubectl -n logging-system get svc
```

```bash
kubectl -n logging-system logs -l app=elasticsearch-aio --follow
```