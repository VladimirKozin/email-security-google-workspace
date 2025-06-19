# Email Authentication Setup – Google Workspace

**Domain:** aishield.online  
**Platform:** Namecheap + Google Workspace  

---

## ✅ DNS Records Setup Guide

### Step 1: Log in to Namecheap

- Visit: [https://www.namecheap.com/](https://www.namecheap.com/)
- Go to **Domain List** → Click **Manage** next to your domain
- Open the **Advanced DNS** tab

---

### Step 2: Configure MX Records (for Gmail delivery)

Go to **Mail Settings** → Select `Custom MX`  
Then add these records:

| Type | Host | Value                    | Priority | TTL       |
|------|------|--------------------------|----------|-----------|
| MX   | @    | ASPMX.L.GOOGLE.COM.      | 1        | Automatic |
| MX   | @    | ALT1.ASPMX.L.GOOGLE.COM. | 5        | Automatic |
| MX   | @    | ALT2.ASPMX.L.GOOGLE.COM. | 5        | Automatic |
| MX   | @    | ALT3.ASPMX.L.GOOGLE.COM. | 10       | Automatic |
| MX   | @    | ALT4.ASPMX.L.GOOGLE.COM. | 10       | Automatic |

---

### Step 3: Add SPF Record

- Type: `TXT`
- Host: `@`
- Value: `v=spf1 include:_spf.google.com ~all`
- TTL: `Automatic`

---

### Step 4: Generate and Add DKIM Record

- Go to Admin Console → Apps → Google Workspace → Gmail → Authenticate Email
- Click **Generate New Record** (select 2048-bit, prefix: `google`)
- Add a new TXT record in Namecheap:
  - Type: `TXT`
  - Host: `google._domainkey`
  - Value: (copy DKIM key)
- TTL: `Automatic`

🕓 *Available after 24–72 hours of Gmail activation.*

---

### Step 5: Add DMARC Record

- Type: `TXT`
- Host: `_dmarc`
- Value: `v=DMARC1; p=none; rua=mailto:report@aishield.online`
- TTL: `Automatic`

---

## 📁 Screenshot Directory (GitHub)

Place all screenshots in `/screenshots/` folder.

| Filename                                | Description                      |
|----------------------------------------|----------------------------------|
| `02_email_mx_records_configured_namecheap.png` | MX records set                   |
| `03_spf_record_google_workspace.png`   | SPF record                       |
| `06_dkim_generation_pending.png`       | DKIM key generation              |
| `07_dmarc_record_google_workspace.png` | DMARC TXT record                 |

---

**Maintainer:** Vladimir Kozin  
Repository: `email-security-google-workspace`
