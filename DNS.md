# DNS for openchronicles.org → GitHub Pages

Repo: https://github.com/pmcmurry/openchronicles.org  
Pages source: `master` branch, root  
CNAME file: `openchronicles.org`  
DNS host: **Cloudflare** (zone for openchronicles.org)

## Temporary URL (works before custom DNS)

https://pmcmurry.github.io/openchronicles.org/

(If paths break on that URL, prefer the custom domain once DNS is live.)

## Apex domain records

In Cloudflare DNS (or at your registrar if nameservers point elsewhere), set:

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

## Email (Cloudflare Email Routing)

Inbound contact: **paul@openchronicles.org** → forwards to **pmcmurry@gmail.com**.

Managed in Cloudflare → Email Service → Email Routing. DNS records for routing are typically **Locked** by Email Routing — do not delete them when editing site DNS.

| Type | Name | Value | Notes |
|------|------|--------|--------|
| **MX** | `@` | `route2.mx.cloudflare.net` | Priority 9 (typical) |
| **MX** | `@` | `route3.mx.cloudflare.net` | Priority 73 (typical) |
| **MX** | `@` | `route1.mx.cloudflare.net` | Priority 89 (typical) |
| **TXT** | `@` | `v=spf1 include:_spf.mx.cloudflare.net ~all` | Single SPF only; merge later providers into this one record |

Routing rule: custom address `paul` → destination `pmcmurry@gmail.com`.

Outbound “Send mail as” from Gmail is **not** configured yet (needs an SMTP provider and SPF merge). Site A/`www` records are independent of MX/TXT.

### Verify email DNS

```bash
nslookup -type=MX openchronicles.org
# should show route*.mx.cloudflare.net

nslookup -type=TXT openchronicles.org
# should include SPF with _spf.mx.cloudflare.net
```

## Note

Remove any parking page or placeholder A/CNAME records from the registrar so they don’t conflict. Do not remove Email Routing MX/TXT while inbound mail is in use.
