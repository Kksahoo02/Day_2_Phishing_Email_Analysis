# 🎯 Phishing Email Analysis – Cybersecurity Internship Task

## 🎯 Objective  
Analyze a phishing email sample to identify common **indicators of compromise** and understand **attacker tactics**.

---

## 📥 Sample Email Source  
- 🔗 Obtained from: [https://github.com/rf-peixoto/phishing_pot/tree/main](https://github.com/rf-peixoto/phishing_pot/tree/main)  
- 💾 Saved as: `sample-1062.eml`

---

## 🛠️ Tools Used  
- 📧 **Email Header Analyzer**: [Google Admin Toolbox – Messageheader](https://toolbox.googleapps.com/apps/messageheader/analyzeheader)  
- 👁️ **Manual Inspection**: Reviewed in email client for visual and textual red flags

---

## 🚩 Phishing Indicators Identified  

1. **Spoofed Sender**  
   📨 `security@amaz0n-services.net` (note the **zero** instead of "o") — **not** the legitimate `@amazon.com` domain.

2. **Urgent & Threatening Language**  
   ⏳ *"Your account will be suspended in 24 hours!"* — classic **social engineering** to provoke panic.

3. **Suspicious Link**  
   🔗 Hovering reveals: `http://amaz0n-verify.ru/login` — a **non-Amazon domain** with a `.ru` TLD (Russia), often used in phishing.

4. **Spelling & Grammar Errors**  
   ✍️ *"Please verifed your account immediatly."* — poor English is a common trait in phishing emails.

5. **Header Analysis (via Google Toolbox)**  
   - 🛑 **SPF**: **Fail**  
   - 🌐 **Origin IP**: `192.168.10.55` (private/internal IP — **not Amazon’s infrastructure**)  
   - 🔐 **DKIM**: No valid signature → email integrity **not verified**

6. **Mismatched Branding**  
   🎨 Pixelated logo and off-brand colors — visual cues that the email is **not from Amazon**.

---

## ✅ Conclusion  
This email exhibits **6+ classic phishing traits**, including **domain spoofing**, **urgency**, **malicious links**, and **authentication failures**.  

🔐 **Best Practice**: Never click links or enter credentials from unsolicited emails. Always navigate directly to the official website.

---

## 📚 References  
- 🛡️ **CISA – Secure Our World**: [https://www.cisa.gov/secure-our-world](https://www.cisa.gov/secure-our-world)  
- 🐟 **PhishTank – Phishing Intelligence**: [https://www.phishtank.com/](https://www.phishtank.com/)  

> ℹ️ *PhishTank is a collaborative clearinghouse for phishing data and offers a free API for researchers and developers.*
