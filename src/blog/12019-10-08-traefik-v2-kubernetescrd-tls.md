# traefik v2 kubernetescrd tls

## tls certs with traefik v2

so,
because it wasn't entirely obvious to me,
tls certs are managed by _certResolvers_,
identified by

```
--certificateresolvers.name-of-your-resolver.acme...
```

and used with _IngressRoutes_ like this:

```
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRoute
metadata:
  name: http-server
spec:
  entryPoints:
    - websecure
  tls:
    certResolver: name-of-your-resolver
  routes:
    - kind: Rule
      match: ...
```
