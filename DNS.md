# DNS for openchronicles.org → GitHub Pages

Repo: https://github.com/pmcmurry/openchronicles.org  
Pages source: `master` branch, root  
CNAME file: `openchronicles.org`

## Temporary URL (works before custom DNS)

https://pmcmurry.github.io/openchronicles.org/

(If paths break on that URL, prefer the custom domain once DNS is live.)

## Apex domain records

At your registrar (wherever you bought openchronicles.org), set:

### Option A — recommended for apex

| Type | Name / host | Value | TTL |
|------|-------------|--------|-----|
| **A** | `@` | `185.199.108.153` | 3600 |
| **A** | `@` | `185.199.109.153` | 3600 |
| **A** | `@` | `185.199.110.153` | 3600 |
| **A** | `@` | `185.199.111.153` | 3600 |
| **CNAME** | `www` | `pmcmurry.github.io` | 3600 |

### Option B — if your DNS supports ALIAS/ANAME

| Type | Name | Value |
|------|------|--------|
| ALIAS/ANAME | `@` | `pmcmurry.github.io` |
| CNAME | `www` | `pmcmurry.github.io` |

## After DNS propagates

1. Open https://github.com/pmcmurry/openchronicles.org/settings/pages  
2. Confirm custom domain **openchronicles.org**  
3. Enable **Enforce HTTPS** (available after certificate issues—can take minutes to hours)

## Verify

```bash
nslookup openchronicles.org
# should show GitHub A records

curl -I https://openchronicles.org
```

## Note

Remove any parking page or placeholder A/CNAME records from the registrar so they don’t conflict.
