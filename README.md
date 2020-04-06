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
| test  | test  | test  | test  | test  | test  |
| test  | test  | test  | test  | test  | test  |
| test  | test  | test  | test  | test  | test  |
| test  | test  | test  | test  | test  | test  |
