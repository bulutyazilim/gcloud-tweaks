## How do I set up Gmail for my domain on Google Cloud Platform DNS
1. Add your domain to GCP console's DNS tab
  [zones](https://console.cloud.google.com/networking/dns/zones)

2. save: **google_apps_mx.yml** (replace *DNS_NAME* with your domain.tld)

  ```yaml
  ---
  kind: dns#resourceRecordSet
  name: DNS_NAME.
  rrdatas:
  - 1 aspmx.l.google.com.
  - 5 alt1.aspmx.l.google.com.
  - 5 alt2.aspmx.l.google.com.
  - 10 alt3.aspmx.l.google.com.
  - 10 alt4.aspmx.l.google.com.
  ttl: 300
  type: MX
  ```
3. Run this command (replace *ZONE_NAME* with your zone name)

  `gcloud dns record-sets import google_apps_mx.yml -z ZONE_NAME`
