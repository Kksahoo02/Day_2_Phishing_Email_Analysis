# Phishing Email Analysis – Cybersecurity Internship Task

## Objective
Analyze a phishing email sample to identify common indicators of compromise and understand attacker tactics.

## Sample Email Source
- Obtained from: https://github.com/rf-peixoto/phishing_pot/tree/main
- Saved as: `sample-1062.eml`s

## Tools Used
- Email Header Analyzer (https://toolbox.googleapps.com/apps/messageheader/analyzeheader)
- Manual inspection in email client

## Phishing Indicators Identified
1. **Spoofed Sender**: `security@amaz0n-services.net` (not amazon.com)
2. **Urgent Language**: "Your account will be suspended in 24 hours!"
3. **Suspicious Link**: Hover reveals `http://amaz0n-verify.ru/login` (not Amazon’s domain)
4. **Grammar Errors**: "Please verifed your account immediatly."
5. **Header Analysis**: 
   - SPF: **Fail**
   - Origin IP: 192.168.10.55 (not Amazon’s network)
   - No valid DKIM signature
6. **Mismatched Branding**: Logo looks pixelated; colors slightly off

## Conclusion
This email exhibits 6+ classic phishing traits. Users should never click links or provide credentials. Always verify sender authenticity via official channels.

## References
- CISA: https://www.cisa.gov/secure-our-world
- PhishTank: https://www.phishtank.com/