# 📄 Phishing Email Analysis Findings Report

## 🔍 Overview
This report details the forensic analysis of a suspicious email received on **August 8, 2023**, at **11:14:15 PM GMT+5:30**. The email was flagged for potential phishing activity due to its sender, subject line, and failed authentication checks.

The email was analyzed using **Google Admin Toolbox – Messageheader**, which decodes and validates email headers for security indicators.

---

## 📬 Email Metadata

| Field         | Value                                                                 |
|---------------|-----------------------------------------------------------------------|
| **Message ID** | `04418440-957a-c8df-171f-05ae3fcdec24@mercadolivre.br`               |
| **Created At** | `8/8/2023, 11:14:15 PM GMT+5:30` (Delivered after 1 second)          |
| **From**       | `Mercado Livre <notificacoes@mercadolivre.br>`                        |
| **To**         | `phishing@pot`                                                        |
| **Subject**    | `BLOQUEAMOS UM ACESSO SUSPEITO - PROTOCOLO: 262677886`                |

> 💡 **Note**: The recipient address `phishing@pot` appears to be a test or honeypot account — likely used for educational or security research purposes.

---

## ⚠️ Authentication & Security Checks

### ✅ SPF (Sender Policy Framework)
- **Result**: `none`
- **Analysis**: No SPF record was published or validated for `mercadolivre.br`. This means there’s no mechanism to verify if the sending server is authorized to send emails on behalf of this domain.
- **Risk**: High — attackers can easily spoof emails from this domain.

### ❌ DKIM (DomainKeys Identified Mail)
- **Result**: `fail with domain Unknown!`
- **Analysis**: DKIM signature validation failed. The domain used in the signature does not exist or is misconfigured.
- **Risk**: Critical — indicates the email may have been altered in transit or forged.

### ✅ DMARC (Domain-based Message Authentication, Reporting & Conformance)
- **Result**: `none`
- **Analysis**: No DMARC policy is configured for `mercadolivre.br`.
- **Risk**: High — without DMARC, receiving servers cannot enforce SPF/DKIM policies or report abuse.

> 📌 **Summary**: All three major email authentication protocols (SPF, DKIM, DMARC) are either missing or failing — a **strong indicator of phishing or spoofing**.

---

## 🧭 Delivery Path / Routing

| # | Delay | From                                 | To                                     | Protocol | Time Received        |
|---|-------|--------------------------------------|----------------------------------------|----------|----------------------|
| 0 | 1 sec | `AM7EUR06FT047.eop-eur06.prod.protection.outlook.com` | `AM6P193CA0049.outlook.office365.com` | SMTP     | 8/8/2023, 11:14:16 PM |

- **Observation**: The email passed through Microsoft’s Exchange Online Protection (EOP), suggesting it originated from an external source and was routed via Outlook 365 infrastructure.
- **Implication**: While EOP scanned it, the lack of authentication allowed delivery — highlighting how spoofed emails can bypass basic filters if authentication is weak.

---

## 🎯 Phishing Indicators Identified

Based on header analysis and metadata:

1. **Spoofed Sender Identity**  
   - Claims to be from “Mercado Livre” (`notificacoes@mercadolivre.br`) — a legitimate Brazilian e-commerce platform.
   - However, **no valid SPF/DKIM/DMARC** = high chance of impersonation.

2. **Urgent & Threatening Subject Line**  
   - “BLOQUEAMOS UM ACESSO SUSPEITO” → “We blocked a suspicious access”
   - Designed to trigger panic and prompt immediate action.

3. **Lack of Authentication Protocols**  
   - SPF: none | DKIM: fail | DMARC: none → classic red flags in phishing emails.

4. **Unusual Recipient Address**  
   - `phishing@pot` suggests this may be a test environment, but in real-world scenarios, such emails target real users with urgent messages.

5. **Fast Delivery Time (1 sec)**  
   - Often seen in automated phishing campaigns — minimal delay between sending and receipt.

---

## 🛡️ Recommendations

✅ **For End Users**:
- Never click links or reply to emails claiming “suspicious access” unless verified via official website/app.
- Hover over links before clicking — check if domain matches expected brand.
- Report suspicious emails to your organization’s IT/security team.

✅ **For Domain Owners (e.g., Mercado Livre)**:
- Implement SPF, DKIM, and DMARC records immediately.
- Set DMARC policy to `p=quarantine` or `p=reject` to block unauthorized senders.
- Monitor DMARC reports to detect spoofing attempts.

✅ **For Security Teams**:
- Use tools like Google Admin Toolbox, MXToolbox, or Mail Tester to validate incoming email headers.
- Train users on recognizing spoofed domains and authentication failures.

---

## 📎 Conclusion

This email exhibits multiple hallmarks of a **phishing attempt**, including:
- Spoofed sender identity
- Failed email authentication
- Urgent language
- Lack of domain security policies

While the recipient (`phishing@pot`) may be a controlled test account, the same tactics are used daily against real users. Awareness and technical controls (like DMARC) are essential defenses.

---

## 🔗 References

- [Google Admin Toolbox – Messageheader](https://toolbox.googleapps.com/apps/messageheader/)
- [DMARC.org – What is DMARC?](https://dmarc.org/)
- [SPF Record Guide](https://spf-record.net/)
- [DKIM Core Specification](https://datatracker.ietf.org/doc/html/rfc6376)