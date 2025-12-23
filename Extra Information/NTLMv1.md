Vulnerable to Pass the Hash
- medium risk finding
  
Remediation
- Disable NTLM auth (VERY BAD)
    
    - most production environments would break
    
- Enforce message signing
- disable NTLMv1
- enforce LDAP signing