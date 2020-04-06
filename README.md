# Introduction
This document serves as the source-of-truth for Crate Security Architecture standards. The table of security standards is defined as follows:
| Property  | Description  |
|---|---|
| Identifier  | A integer representing the standard. Must be unique among all Crate Security standards  |
| Short Name  | A snake_case short name of the standard. Must be unique among all Crate Security standards and no longer than 10-characters. May be used instead of the numerical identifier in diagrams.  |
| Category  | One of "authc", "authz", "trust", or "audit". Defined as: <ul><li>authc - Authentication standard</li><li>authz - Authorization standard</li><li>trust - Trust relationship standard</li><li>audit - Auditing standard</li><li>confidential - Confidentiality standard</li></ul> |
| Strength  | The relative strength of the standard for informing design decision preferences. One of "avoid", "weak", "sufficient", "strong". Defined as:  <ul><li>very weak - Do not use this standard unless no better alternative standard exists. It is considered insufficient.</li><li>weak - If a stronger standard is available, use it instead</li><li>sufficient - A suitable standard for most user cases with a balance of implementation complexity and utility</li><li>strong - The strongest standard available but may not be suitable for all use cases depending on implementation complexity</li></ul>  |
| Expiration  | The date when the standard must be reviewed and renewed or superseded by a new standard.  |
| Superseded By  | The numerical identifier of the standard that has or will replace the standard.  |
| Description  | A complete and accurate description of the standard technical, process, and people elements. A technical criteria section may also be present with a of criteria with requirement level as defined in defined in RFC 2119 <sup>1</sup>  |

# Referencing The Standards
Security standards should be referenced in diagrams or documents using the regex pattern of `\[((?[a-z_]+):(?\d+))|(?[a-z_])\]` such as `[cisco_sso]` or `[authc:100]`. The short name is preferred whenever it provides better readability.

# List of Security Standards

| Identifier  | Short Name  | Category | Strength | Expiration | Description |
|---|---|---|---|---|---|
| 100  | crate_saml  | authc  | sufficient  | 12/01/2020  | End-user (human) authentication via SAML v2 single-sign on exchange via the Crate keycloak deployment brokering Cisco SSO. Cisco policy for 2FA, password complexity, rotation, etc. are applied at the Cisco SSO IdP.  <br /><br /><b>Technical criteria defining this standard:</b><br /><br /><ul><li>SPs that support SAML single-sign-out <b>must</b> be configured to use single-sign-out</li><li>POST binding <b>must</b> be used</li><li>Client signature verification <b>must</b> be used if the SP supports it.</li><li>Assertions <b>may</b> be configured according to SP requirements, but <b>must</b> include either email or cecid as username and <b>should</b> use email whenever possible</li></ul>  |
| 101  | crate_oidc  | authc  | sufficient  | 12/01/2020  | End-user (human) authentication via OIDC single-sign on exchange via the Crate keycloak deployment brokering Cisco SSO. Cisco policy for 2FA, password complexity, rotation, etc. are applied at the Cisco SSO IdP. <br /><br /><b>Technical criteria defining this standard:</b><br /><br /> <ul><li>Clients <b>should</b> use bearer-only access type whenever possible.</li><li>Clients <b>should not</b> use public access type</li></ul>  |
| 102  | 	jwt_authc  | authc  | sufficient  | 12/01/2020  | Bearer (human or machine) authentication using the JWT specification via the Crate keycloak deployment brokering Cisco SSO. Cisco policy for 2FA, password complexity, rotation, etc. are applied at the Cisco SSO IdP.  <br /><br /><b>Technical criteria defining this standard:</b><br /><br /> <ul><li>JWT access token <b>must</b> be used</li><li>Access tokens <b>must</b> expire within 5 minutes of issue</li><li>Access tokens <b>must</b> be treated as secrets with the applicable secrets management standards</li></ul>  |
| 103  | jwt_authz  | authz  | sufficient  | 12/01/2020  | Bearer (human or machine) authorizations using the JWT specification via the Crate keycloak deployment brokering Cisco SSO. Cisco policy for 2FA, password complexity, rotation, etc. are applied at the Cisco SSO IdP. <br /><br /><b>Technical criteria defining this standard:</b><br /><br /> <ul><li>Claims <b>must</b> include userid</li><li>Userid <b>should</b> be email</li><li>Userid <b>should</b> be CEC ID if the SP does not support emails for userid</li><li>Claims <b>must</b> include Cisco AD groups assignment</li></ul> |
| 104  | api_authc  | authc  | sufficient  | 12/01/2020  | Authentication of machine clients to services with a long-lived api key. Inherits all requirements from `jwt_authc` with the exception of changing token type from access to offline.  |
| 105  | https_le  | trust  | weak  | 12/01/2020  | HTTPS using TLS certificates issued for specific DNS names. This is an implicit type of trust based on the client-side configuration of a target URL. It is implicit because the client will trust whatever host it is pointed at as long as the hosts presents a valid certificate signed by the the trusted root CAs of the client. This assumes that DNS is not compromised, and that the CA issuing the certificate for the target host is also not compromised, and the host itself is not compromised. There is no direct trust between the client and server, and trust is only established one direction (client trusts server).    <br /><br /><b>Technical criteria defining this standard:</b><br /><br /> <ul><li>TLS v1.2 or higher <b>must</b> be used to establish authenticity and confidentiality of the network traffic from the server</li><li>The client <b>must</b> not present a certificate for authentication via TLS</li><li>HTTP <b>must</b> be used as the application protocol</li><li>The host certificate must be issued by Let's Encrypt CA's <sup>2</sup></li></ul> |
| test  | test  | test  | test  | test  | test  |
| test  | test  | test  | test  | test  | test  |
| test  | test  | test  | test  | test  | test  |
| test  | test  | test  | test  | test  | test  |
| test  | test  | test  | test  | test  | test  |
| test  | test  | test  | test  | test  | test  |
| test  | test  | test  | test  | test  | test  |
