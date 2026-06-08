### Security Audit
The following supporting materials will help you complete this activity. Keep materials open as you proceed to the next steps. 

To use the supporting materials for this course item, click the links. 
Links to supporting materials: 
- [Botium Toys: Scope, goals, and risk assessment report](https://docs.google.com/document/d/1s2u_RuhRAI40JSh-eZHvaFsV1ZMxcNSWXifHDTOsgFc/template/preview#heading=h.evidx83t54sc)
- [Control categories](https://docs.google.com/document/d/1HsIw5HNDbRXzW7pmhPLsK06B7HF-KMifENO_TlccbSU/template/preview)
Link to template: [Controls and compliance checklist](https://docs.google.com/document/d/10NoXfyE3ZSiHFqiTE0fINL3xdPvTZq0j0VwnFEM0N3g/template/preview#heading=h.87tykp1u0l36)
****
### Notes
Scope: the entire security program at Botium Toys including assets such as employee equipment and devices, internal networks, and systems.

**Objective**: review the organization's assets and check for controls and compliance practices in place to improve Botium Toys' security posture.

Botium Toys

What works:
- A working firewall that blocks network traffic based on a set of security rules
- Antivirus software installed company-wide and actively monitored by IT team
- Physical Controls like locks, CCTV, and fire detection/prevention

What doesn’t work:
- Least Privilege is not implemented as potentially any employee can access PII and even SPII of clients stored in internal db
- no Disaster recovery plans no backups in place for faster recovery, depending on how data is stored could cause irrevocable data loss.
- Password policies are implemented but not up to par, potentially a security issue.
- Password management system not in place hurting employee productivity with change password tickets.
- Intrusion Detection System (IDS) not implemented, so someone could have access to all company data without anyone knowing.
- Legacy systems are looked after, but it seems not in a consistent manner. Potential attack vector as these software could be outdated with potential active threats.
- company communications and sensitive information should be encrypted so as not to reveal operations and PII/SPII
- Separation of duties is not in place so that one person/account doesn’t have access/ability to overthrow everything/everyone else when compromised.

Unknown/Lacking
- deterrent like alarm provider signage, lights

With these in mind lets look at compliance:

Payment Card Industry Data Security Standard (PCI DSS)
	NOT COMPLIANT
- any employee potentially has access to customers’ credit card information
- Credit card information is stored internally, but not in a secure environment as least privilege, encryption, and disaster recovery plans are not implemented
- There is no encryption for transaction touchpoints and data on transactions and credit card information
- Password policies and management systems are weak and not in place respectively

General Data Protection Regulation (GDPR)
	NOT FULLY COMPLIANT
- E.U. customer data is not kept private/secured
- E.U. customers will be notified of data breaches within 72 hours
- Data seems to be properly inventoried however there should be further investigation into this matter.
- Privacy policies, procedures, and processes are not properly enforced to document and maintain data. Disaster recovery, encryption, password management and policies, all could be potential points of failure here.


Systems and Organizations Controls (SOC type 1 & 2)
	NOT COMPLIANT
- User access policies are not established. Any employee can access sensitive information.
- PII/SPII is not kept confidential/private
- Data might be accurate but there need to be validation measures, disaster recovery, accessed by many willie nillie
- Data is available to those authorized however those with authorization does not follow principle of least privilege

### Message to IT Manager

After a review of the company’s assets, risks, and controls, I have come to the conclusion that a major overhaul of the company’s administrative and technical controls needs to take place.

Only a few technical and physical controls are up to standard: firewall, antivirus, and physical controls like fire detection/prevention, locks, and CCTV.

Many administrative and technical controls need to be implemented correctly: least privilege, separation of duties, account management policies, access control management, disaster recovery plans, backups, password policies and management, intrusion detection system, legacy system monitoring, encryption.

Some security controls are unknown such as sufficient lighting to reduce the number of hiding places in company facility, locks for networking equipment, server/database security from physical threats, alarm provider signage, potentially the need for a bigger team to monitor, maintain, and prevent security risks, 

There are many points of possible failure which goes hand in hand with the lack of compliance. The company is not compliant with PCI DSS, GDPR, or SOC type 1 & type 2 frameworks.

**Potential liabilities:**
Being [PCI DSS non-compliant](https://nordlayer.com/learn/pci-dss/pci-fines/) will eventually trigger a combination of monthly fees, per-transaction costs, and other severe liabilities levied by banks and payment processors. Failure to comply within a few months could cost the company $10,000+  up to $100,000+ in a year. If this non-compliance leads to a data breach, credit card companies could impose penalties $50-$90 per compromised card record. The company may get fined larger sums, up to $500,000 per security incident while hiking up overall transaction costs.

Being [GDPR non-compliant](https://sentra.io/blog/gdpr-compliance-failures-lead-to-surge-in-fines) could lead to fines up to $11.35 million or 2% of global annual revenue (whichever is higher) for less severe issues like lack of staffing, documentation, or simple technical failures. These fines could increase to $22.7 million of 4% of global annual revenue (whichever is higher) for severe issues like failing to get user consent for data storage, mishandling sensitive data, and violating core data processing principles.

All in all, the potential fiscal liabilities are massive and should be an encouragement to be compliant as soon as possible but also correctly.

Other liabilities include damage to the company's credibility and public posture, data breaches leading to client, vendor, and employee sensitive information being leaked and/or used in the means of other crimes, and potential physical threats stemming from bad actors internally or externally.

**Suggestions:**
To comply with these laws and standards, the company must spend more energy and money to put into place these lacking controls. The company should also do more investigation into controls I listed unknown as they may potentially be more points of failure.

The company has a few ongoing eminent threats that need to be addressed as soon as possible. This includes access control, least privilege, intrusion detection systems, consistent maintaining and auditing legacy systems, and password policies/management, encryption. I believe these issues greatly increase the threat surface area and need to be addressed which additionally helps with compliance with jurisdictional regulations and other standards, overall securing the company, it’s employees, and its assets.