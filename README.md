# edgetunnel-sub

Static mirror of a VLESS-over-WebSocket subscription.

## Endpoints

| File | Purpose |
| --- | --- |
| `sub.txt` | Base64 subscription payload (standard format) |
| `sub-plain.txt` | Same nodes, plain `vless://` lines, one per line |
| `clash-config.yaml` | mihomo / Clash Meta profile with `url-test` + `fallback` groups |

## Raw links

```
https://raw.githubusercontent.com/jacktony2001/edgetunnel-sub/main/sub.txt
https://raw.githubusercontent.com/jacktony2001/edgetunnel-sub/main/sub-plain.txt
https://raw.githubusercontent.com/jacktony2001/edgetunnel-sub/main/clash-config.yaml
```

## Notes

- Nodes are Cloudflare edge IPs that passed a real end-to-end HTTPS check through the tunnel.
- The edge IP block list rotates, so these entries go stale after a while. Refresh by
  re-running the health scanner and re-uploading `ADD.txt` to KV, then updating this repo.
- Client requirements: `security=tls`, `type=ws`, `path=/ws`, `fp=chrome`,
  `encryption=none`, `alpn=http/1.1`, and uppercase `host` / `sni`
  (`EDGETUNNEL-PAGES-DI9.PAGES.DEV`). Do not lowercase them.
- Certificate is valid; keep `skip-cert-verify` off.
