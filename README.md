# Vertical sliced frontend Demo

Reverse Proxyを使用して、ページ単位で分割したフロントエンドのデモ。

## リクエストの流れ
リバースプロキシとして前段に Caddy を置き、パスごとにルーティングする。

```
                                   ┌─────────────┐
                           /app1   │             │
                              ┌───►│   Next.js   │
                              │    │             │
           ┌─────────────┐    │    └─────────────┘
           │             ├────┘                   
    ──────►│    Caddy    │                        
           │             ├────┐                   
           └─────────────┘    │    ┌─────────────┐
localhost:3000                │    │             │
                              └───►│    Remix    │
                           /app2   │             │
                                   └─────────────┘
```

## References

- https://nextjs.org/docs/app/api-reference/next-config-js/basePath
- https://github.com/remix-run/remix/discussions/6797
- https://github.com/kiliman/remix-proxy-basename
- https://caddyserver.com/docs/caddyfile/directives/handle_path
- https://caddyserver.com/docs/caddyfile/directives/reverse_proxy
