Project: Email Authentication Setup – Google Workspace
Domain: aishield.online
Platform: Namecheap + Google Workspace

✅ DNS Records Setup Guide

Step 1: Log in to Namecheap

Visit: https://www.namecheap.com/

Go to Domain List → Click Manage next to your domain

Open the Advanced DNS tab

Step 2: Configure MX Records (for Gmail delivery)

Scroll to Mail Settings and select Custom MX from the dropdown.

Click Add New Record and input the following:

Type

Host

Value

Priority

TTL

MX

@

ASPMX.L.GOOGLE.COM.

1

Automatic

MX

@

ALT1.ASPMX.L.GOOGLE.COM.

5

Automatic

MX

@

ALT2.ASPMX.L.GOOGLE.COM.

5

Automatic

MX

@

ALT3.ASPMX.L.GOOGLE.COM.

10

Automatic

MX

@

ALT4.ASPMX.L.GOOGLE.COM.

10

Automatic

📸 Screenshot: 02_email_mx_records_configured_namecheap.png

Step 3: Add SPF Record

Click Add New Record

Select TXT Record

Use:

Host: @

Value: v=spf1 include:_spf.google.com ~all

TTL: Automatic

📸 Screenshot: 03_spf_record_google_workspace.png

Step 4: Generate and Add DKIM Record

Go to: Admin Console → Apps → Google Workspace → Gmail → Authenticate Email

Click Generate New Record (use 2048-bit key, prefix google)

Copy the generated TXT record (you will see a name like: google._domainkey.aishield.online)

In Namecheap:

Type: TXT Record

Host: google._domainkey

Value: (your long DKIM key)

📸 Screenshot: 06_dkim_generation_pending.png

⏱️ Note: Available 24–72 hours after Gmail setup.

Step 5: Add DMARC Record

In Namecheap → Add New Record:

Type: TXT Record

Host: _dmarc

Value: v=DMARC1; p=none; rua=mailto:report@aishield.online

TTL: Automatic

📸 Screenshot: 07_dmarc_record_google_workspace.png

📁 Screenshot Directory in GitHub

Store all screenshots in /screenshots/ folder of your repository.
Use .gitkeep file to preserve empty folders.

Filename

Description

01_before_dns_setup.png

DNS panel before setup

02_email_mx_records_configured_namecheap.png

MX records configured

03_spf_record_google_workspace.png

SPF record added

05_gmail_activation.png

Gmail activation in Workspace

06_dkim_generation_pending.png

DKIM record pending

07_dmarc_record_google_workspace.png

DMARC policy record added

🧠 Notes

Platform: Namecheap Advanced DNS

Mail: Google Workspace trial

Email used: info@aishield.online

Repo name: email-security-google-workspace

Maintainer: Vladimir Kozin

