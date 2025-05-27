# Phishing Email Sample:
![image](https://github.com/user-attachments/assets/91e33d30-dbc7-4b44-bbff-08e559157156)

# Phishing Email Analysis:
## 1. Obtain a Sample Phishing Email
- **Sample Used**: Screenshot of an email pretending to be from Chase Bank.
- **Source**: Provided image showing a suspisious banking alert email.


## 2. Example Sender's Email Address for Spoofing
- **From**: `customer.service@intranet-fi.com`
- **Analysis**:
  - This is ***not a legitimate Chase domain*** (should be something like `@chase.com`).
  - **Spoofed domain** designed to trick recipients.

## 3. Check Email Headers for Descrepancies
- Header Not Provided in Image.
  - Since we only have an image, we **cannnot analyze full email headers**.
  - In a real case, we would copy headers nto a tool line `MXToolbox Email Header Analyzer`.

## 4. Identify Suspicious Links or Attachments
- **Links Mentioned**:
  - "Chase Online Banking"
  - "U.S. Bank Mobile Banking website"
- **Analysis**:
  - **Two different banks** mentioned in one email = **suspicious**.
  - Links are likely phishing URLs masked with legit text.
  - **No attachments** visible in this email.

## 5. Look for Urgent or Threatening Language in the Email Body
- **Example Phrase**:
  | "An ATM withdrawal or debit card purchase exceeds the amount you have chosen."
- **Analysis**:
  - Uses urgent to **trick user into clicking the link** to protect their account.
  - Classic fear-based phishing.

## 6. Note Any Mismatched URLs (Hover to See Real Link)
- **Image Limitation**:
  - You can't hover over links in an image.
- **What to Note**:
  - In actual analysis, if a link **says chase.com** but **points to another domain**, it's a phishing attemp.
- **Assumption**:
  - Based on domain spoofing and urgency, links are likely mismatched.

## 7. Verify Presence of Spelling or Grammer Errors
- **Spelling**: No major spelling errors.
- **Grammer & Phrasing**:
  - Slightly awakward: "To view more information on this transaction lon in to..."
  - Minor grammer issues -- common in phishing emails.
  - Supports suspicion, though not a strong signal alone.
 
## 8. Summerize Phishing Traits Found in the Email
| Trait                      | Found? | Notes                                        |
| -------------------------- | ------ | -------------------------------------------- |
| **Spoofed Email Address**  | ✅      | `intranet-fi.com` instead of `chase.com`     |
| **Suspicious Links**       | ✅      | Hyperlinks likely redirect to phishing pages |
| **Urgency/Fear Tactic**    | ✅      | Fake alert about ATM withdrawal              |
| **Multiple Brand Names**   | ✅      | Chase and U.S. Bank mentioned together       |
| **No Personalization**     | ✅      | No user name or personal details             |
| **Poor Grammar**           | ⚠️     | Minor phrasing issues                        |
| **Email Headers Analyzed** | ❌      | Not available in image                       |
| **Attachments**            | ❌      | None in this example                         |


## Final Conslusion:
This is a **clear phishing email**, using a **spoofed sender, fake links,** and **urgent language** to manipulate users into clicking a malicious link and entering credentials.
