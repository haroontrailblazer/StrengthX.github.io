# StrengthX – Strengthen Your Passwords

**Project Members:**  
- Haroon K M  
- Balamurugan T  
- Sujay S  
- Enbachozhan V  

---

## Abstract
**StrengthX** is a professional-grade password evaluation system designed to assess password strength and detect exposure in public data breaches. It empowers users with practical insights into password security through an interactive and privacy-focused web interface. The project integrates modern cybersecurity practices, secure hashing, and data breach APIs to deliver accurate feedback without storing sensitive information.

---

## 1. Introduction
In today's digital ecosystem, password compromise remains one of the most common attack vectors. Weak, reused, or previously breached passwords significantly increase the risk of unauthorized access. StrengthX tackles this problem by providing an intuitive platform that analyzes password strength and verifies exposure in known breaches. It promotes security awareness and password hygiene among users, bridging the gap between technical security knowledge and practical usability.

---

## 2. Purpose
The core purpose of StrengthX is to enhance cybersecurity awareness and reduce password-related vulnerabilities by offering a real-time password strength and breach detection platform.

- Educate users about password security best practices.  
- Provide actionable feedback for weak or compromised passwords.  
- Encourage the adoption of strong, unique, and secure credentials.  
- Demonstrate integration of AI and data-driven password assessment models.

---

## 3. Motivation
The project is motivated by the increasing number of global data breaches and poor user password habits. Many individuals reuse simple passwords across multiple platforms. Existing solutions either compromise privacy or fail to educate users about secure password creation. StrengthX provides a transparent, safe, and informative approach to assess password integrity.

---

## 4. Scope
StrengthX focuses on:  
- Password evaluation  
- Breach verification  
- User awareness  

It does **not** handle account management or authentication systems but can be integrated with them. The scope includes backend logic, front-end visualization, API integration, and deployment workflows.

---

## 5. Features
- **Password Strength Analyzer:** Evaluates password entropy, pattern repetition, and complexity.  
- **Breach Exposure Checker:** Uses hashed password lookups with HaveIBeenPwned API.  
- **Privacy-First Model:** No password storage; client-side hashing implemented.  
- **Real-Time Feedback:** Interactive display with strength visualization.  
- **Dockerized Deployment:** Simplified container-based setup for scalability.  

---

## 6. Architecture & System Overview
StrengthX follows a modular architecture separating the front-end UI, backend processing, and API integration layers.

- **Frontend:** Developed with Streamlit for an interactive UI.  
- **Backend:** Python scripts handle logic, scoring, and breach API queries.  
- **Security Layer:** Hash-based lookup ensures no plaintext transmission.  
- **Deployment:** Docker containers ensure consistent builds and portability.  

**System Diagram:**  
 <img width="560" height="376" alt="image" src="https://github.com/user-attachments/assets/580e2dcd-9112-4371-839f-76383f425795" />



**Components:**  
- **Frontend:** Streamlit-based interface for user input and visualization.  
- **Backend:** Python scripts for password strength calculation, regex validation, and breach checking.  
- **Security Layer:** SHA-1 hashing and k-anonymity for safe API queries.  
- **Deployment:** Docker for scalable, portable deployment.

---

## 7. Technology Stack
- **Backend:** Python 3.x  
- **Frontend:** Streamlit  
- **Libraries:** `hashlib`, `zxcvbn`, `requests`, `pwnedpasswords`  
- **Version Control:** Git & GitHub  
- **Deployment:** Render / Docker / Streamlit  
- **License:** Apache License 2.0  

---

## 8. User Workflow

The workflow starts when the user inputs a password into the Streamlit interface. The system calculates its strength score, checks breach databases securely, and returns a detailed report. This interactive loop allows users to refine and improve their passwords instantly.

**Figure 1.2: Workflow Diagram**

<img width="425" height="520" alt="image" src="https://github.com/user-attachments/assets/e912d199-9250-4b99-a694-de7aff9820b3" />

---

## 9. Security & Privacy Considerations

StrengthX ensures privacy by **never storing user passwords**. Key security measures include:

- Hashing techniques such as SHA‑1 for verification with public APIs like HaveIBeenPwned.
- Secure HTTPS connections and encrypted data handling.
- Minimal and anonymized logging.

---

## 10. Testing & Validation

Testing includes:

- **Unit tests** for password scoring algorithms.
- **Integration tests** for API communication.
- **Manual UI testing** across different browsers.
- **Security testing** to ensure no sensitive data leakage.

### 10.1 User Input

- User enters a password in the Streamlit input box (`st.text_input`).
- The password is captured as a string variable `pwd`.

### 10.2 Preliminary Validation

- Checks whether a password is entered.
  - If **no password** → displays: "Please enter a password to evaluate its strength."
  - If **entered** → proceeds to evaluation.

### 10.3 Hashing and Breach Check

- Password is SHA-1 hashed: `hashlib.sha1(pwd.encode())`.
- Only the **first 5 characters** of the hash are sent to the Pwned Passwords API (k-anonymity model).
- API returns matching suffixes and breach counts.
- Full hash checked against results:
  - **Found** → password marked as *Compromised*.
  - **Not found** → password is safe from known breaches.

### 10.4 Strength Evaluation

- Uses **zxcvbn** library for entropy and pattern analysis.
- Metrics returned:
  - `score` (0–4)
  - `crack_times_display`
  - `feedback` (suggestions/warnings)
- Password strength classification:
  - 0 → Very Weak
  - 1 → Weak
  - 2 → Fair
  - 3 → Strong
  - 4 → Very Strong

### 10.5 Regex-Based Validation

- Checks for numbers: `(?=.*\d)`
- Checks for uppercase: `(?=.*[A-Z])`
- Checks for special characters: `[!@#$%^&*()_+{}\[\]:;"'<>?,./\|\\-]`
- Checks for minimum length (12 chars)  
- Each failed check adds a recommendation (e.g., "Add numbers", "Increase length").

### 10.6 Feedback and Visualization

- Displays:
  - Crack time estimates
  - Zxcvbn feedback
  - Custom improvement suggestions
  - Breach check result
- Feedback is **color-coded**:
  - Red → Weak
  - Green → Strong

### 10.7 Security Assurance

- Passwords are **never stored or transmitted in plaintext**.
- All validation occurs locally, except SHA-1 prefix lookup.

---

## 11. Limitations & Future Work

- **Limitations**: Breach database coverage may be partial; strength evaluation is heuristic-based.
- **Future Work**:
  - AI-based predictive strength analysis
  - Multi-factor authentication (MFA) suggestions
  - Integration with password managers
  - Mobile-friendly interface

---

## 12. Author Contributions

The StrengthX project was collaboratively developed by a team of passionate individuals:

### Team Members

**Haroon K M – Project Lead & Full-Stack Developer**
- Conceptualized and led development
- Integrated password strength algorithms (Regex + zxcvbn) and Pwned Passwords API
- Designed Streamlit UI and managed project structure, GitHub, and deployment

**Balamurugan T – Backend Developer & Security Engineer**
- Implemented encryption and hashing techniques
- Developed backend logic for validation and regex optimization
- Conducted security testing and validation

**Sujay S – Data Analyst & Validation Specialist**
- Analyzed password strength data and API responses
- Handled testing scenarios and performance validation
- Designed validation flow diagrams and QA reports

**Enbachozhlan V – Technical Writer & Frontend Designer**
- Created documentation and visual diagrams
- Contributed to UI/UX design
- Assisted with architecture, testing, and workflow diagrams

---

## 13. References

1. [StrengthX - GitHub Repository](https://github.com/haroontrailblazer/StrengthX)  
2. [StrengthX Website](https://strengthx.onrender.com/)  
3. [HaveIBeenPwned API Documentation - Troy Hunt](https://haveibeenpwned.com/API/v3)  
4. [zxcvbn Password Strength Estimator](https://github.com/dropbox/zxcvbn)  
5. [Streamlit Developer Guide](https://docs.streamlit.io/)  
6. [Render Hosting Developer Guide](https://render.com/docs)  
7. [GitHub Contributors](https://github.com/haroontrailblazer/StrengthX/graphs/contributors)


## 14. Installation & Setup

**Prerequisites:** Python 3.x, Git, Streamlit, Docker (optional)  

```bash
# Clone Repository
git clone https://github.com/haroontrailblazer/StrengthX.git

# Navigate into directory
cd StrengthX

# Install dependencies
pip install -r requirements.txt

# Pull latest updates
git pull origin main

# Run the application
streamlit run app.py


