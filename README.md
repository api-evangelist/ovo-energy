# OVO Energy (ovo-energy)

OVO Energy is a United Kingdom household electricity and gas supplier founded in Bristol in 2009 by Stephen Fitzpatrick, and — after absorbing SSE's household energy business in January 2020 — the third-largest domestic supplier in Great Britain with roughly four million home energy customers. It sits at the retail end of the GB energy value chain: buying wholesale, holding an Ofgem supply licence, settling through Elexon, reading SMETS2 smart meters over the licensed Smart DCC network, and billing the customer, alongside solar, home battery, heat pump, EV smart-charging (Charge Anytime) and demand-flexibility (Power Move) propositions. Its parent OVO Group also owns Kaluza, an API-first energy intelligence platform licensed to utilities worldwide — the direct British analogue to Octopus Energy's Kraken — but that platform is a separate brand on a separate domain, and none of its API surface is published under OVO Energy. OVO Energy's own API posture is closed: no developer portal, no API documentation, no machine-readable contract, and no third-party route to a customer's usage or billing data.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/ovo-energy/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/ovo-energy/refs/heads/main/apis.yml)

## Tags

- Energy
- United Kingdom
- Utilities
- Electricity
- Gas
- Smart Metering
- Energy Retail
- Solar
- EV Charging
- Demand Response

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## APIs

No public, documented APIs were found. Every developer surface probed on 2026-07-27
returned 404 or failed to resolve. `api.ovoenergy.com` resolves and is live but answers
every path with a bare `text/plain` 404 — `No context-path matches the request URI`.
The one real consumer-data endpoint found,
`https://smartpaymapi.ovoenergy.com/usage/api/half-hourly`, returns HTTP 401 JSON to an
anonymous caller: it is undocumented, unsupported, and reachable only with a signed-in
OVO customer session. It is deliberately **not** listed as an API here. See `review.yml`
for the full probe log.

## Artifacts

Round 2 enrichment (2026-07-27) re-ran contract discovery against every OVO host and found
no machine-readable contract — no OpenAPI, no GraphQL, no AsyncAPI, no MCP server. What it
did harvest is the security, packaging and conformance posture:

- `well-known/ovo-energy-well-known.yml` — `/.well-known/` probe index across five hosts
- `well-known/ovo-energy-security.txt` — verbatim RFC 9116 security.txt (the only
  `.well-known` document served anywhere on the estate)
- `security/ovo-energy-vulnerability-disclosure.yml` — the responsible-disclosure programme
  (Tines intake, no bug bounty, conditional no-legal-action commitment)
- `security/ovo-energy-domain-security.yml` — TLS/HSTS/cert/DNSSEC/CAA/SPF/DMARC for eight
  hosts and two domains
- `conformance/ovo-energy-conformance.yml` — what OVO conforms to (RFC 9116, GB Smart Energy
  Code, HSTS, DMARC `p=reject`) and what it demonstrably does not (OpenAPI, OIDC, OAuth2,
  RFC 9457, Green Button, CDR, OCPP/OCPI, OpenADR)
- `packages/ovo-energy-packages.yml` — first-party OVO Technology open-source libraries
  (npm `@ovotech`, Maven `com.ovoenergy`, Go) and the one **community** Python client; there
  is no first-party API client SDK, because there is no API
- `llms/ovo-energy-llms.txt` — generated llms.txt (OVO publishes none; `/llms.txt` 404s)

## Common Properties

- [Website](https://www.ovoenergy.com/)
- [About](https://www.ovoenergy.com/about)
- [Group Website](https://company.ovo.com/)
- [GitHub Organization](https://github.com/ovotech)
- [LinkedIn](https://www.linkedin.com/company/ovoenergy)
- [Blog](https://www.ovoenergy.com/blog)
- [Support](https://www.ovoenergy.com/help)
- [Forum](https://forum.ovoenergy.com/)
- [Customer Portal / Login](https://my.ovoenergy.com/login)
- [Sign Up (energy quote)](https://www.ovoenergy.com/get-energy-quote)
- [Pricing (home energy plans)](https://www.ovoenergy.com/home-energy-plans)
- [Privacy Policy](https://www.ovoenergy.com/privacy-policy)
- [Terms of Service](https://www.ovoenergy.com/terms)
- [security.txt](https://www.ovoenergy.com/.well-known/security.txt)
- [Security / responsible disclosure](https://www.ovoenergy.com/security)
- [Careers](https://careers.ovo.com/)

## Mandate Posture

- **Mandate regime:** `smart-meter-infrastructure` — the GB Smart Energy Code and the
  Smart DCC licensed monopoly. This is an infrastructure obligation on licensed suppliers,
  **not** a consumer data right.
- **Mandate status:** `live-implemented` — OVO demonstrably operates a smart-meter estate
  at scale (eleven smart-meter product/help pages in the sitemap, including a SMETS1 4G
  upgrade programme) and a live half-hourly consumption endpoint proves DCC-sourced data
  actually flows to customers. The implementation surface is the private licensed DCC User
  Interface and an internal customer API, not a public API.
- **CDR homonym trap:** `cdr-energy` does **not** apply. OVO Energy Pty Ltd in Australia
  publishes a Consumer Data Right policy and is a designated CDR energy data holder — but
  AGL Energy took it to 100% ownership in April 2024, so that obligation belongs to an
  AGL-owned company, not to this one. Do not attribute it here.
- **Data standard:** no standard reference found. SMETS1/SMETS2 metering under the Smart
  Energy Code is the only standard in play, and it is infrastructure, not a published API
  contract. No Green Button / ESPI, no CDR Consumer Data Standards, no OpenAPI, no
  OCPP/OCPI, no IEC CIM, no IEEE 2030.5, no OpenADR.
- **Consumer data API:** none documented. **Open market data:** none — GB open market and
  system data comes from NESO, Elexon and the DNOs, not from a retailer.
- **Access gate:** `customer-account-required` — the only route to energy data is your own
  account, through `my.ovoenergy.com` or the OVO app. There is no developer programme to
  apply to.

## Corporate Note

On 11 May 2026 OVO agreed the sale of this UK energy retail business to E.ON (and its Home
Services business to Hometree), subject to regulatory approval and expected to complete
later in 2026. The Kaluza software platform is explicitly excluded from the sale; E.ON will
continue the existing Kaluza platform licence for OVO's customer base.

## Maintainers

- Kin Lane — kin@apievangelist.com
