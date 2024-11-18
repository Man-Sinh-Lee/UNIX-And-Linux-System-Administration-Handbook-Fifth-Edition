### Chapter 18: Electronic Mail - Summary with Example Commands

---

#### **18.1 Mail System Architecture**
- **Components**:
  - **Mail User Agent (MUA)**: Allows users to compose and read emails (e.g., Thunderbird).
  - **Mail Submission Agent (MSA)**: Prepares emails for transport.
  - **Mail Transport Agent (MTA)**: Delivers emails between servers (e.g., Postfix, Sendmail).
  - **Delivery Agent (DA)**: Places emails in user mailboxes.
  - **Access Agent (AA)**: Retrieves emails using IMAP or POP.

Example:
```bash
# Check mail queue on Postfix
postqueue -p
```

---

#### **18.2 Anatomy of a Mail Message**
- **Parts**:
  1. **Envelope**: Routing information for the MTA.
  2. **Headers**: Metadata (e.g., sender, recipient, date).
  3. **Body**: Message content.
- **Dissecting Headers**:
  ```bash
  # View email headers
  less /var/mail/username
  ```

---

#### **18.3 The SMTP Protocol**
- **Commands**:
  - `HELO/EHLO`: Initiate communication.
  - `MAIL FROM`: Specify sender.
  - `RCPT TO`: Specify recipient.
  - `DATA`: Send email content.
- **Example Debugging**:
  ```bash
  # Connect to SMTP server
  telnet mail.example.com 25
  HELO mydomain.com
  MAIL FROM: user@mydomain.com
  RCPT TO: recipient@example.com
  DATA
  Subject: Test Email
  This is a test.
  .
  QUIT
  ```

---

#### **18.4 Spam and Malware**
- **Solutions**:
  - **SPF**: Authenticate outbound mail servers via DNS.
  - **DKIM**: Sign emails cryptographically.
  - **Cloud-Based Tools**: Services like Barracuda or Google G Suite handle spam effectively.
- **Forgeries and Phishing**:
  - Educate users on suspicious email handling.

---

#### **18.5 Message Privacy and Encryption**
- **Techniques**:
  - **PGP/GPG**:
    ```bash
    # Encrypt a message
    gpg --encrypt --recipient recipient@example.com message.txt
    ```
  - **S/MIME**: Often integrated into email clients.
- **TLS**: Encrypts communication between mail servers.

---

#### **18.6 Mail Aliases**
- **Aliases Configuration**:
  - Edit `/etc/aliases`:
    ```bash
    alias_name: recipient@example.com
    ```
  - Apply changes:
    ```bash
    sudo newaliases
    ```

---

#### **18.7 Email Configuration**
- Centralize configuration using tools like Ansible.
- Use `.forward` for per-user mail redirection.

---

#### **18.8 Sendmail**
- **Overview**:
  - Versatile but complex.
  - Configuration involves `.mc` files processed into `.cf`.
- **Example**:
  ```bash
  # Test sendmail configuration
  sendmail -bt
  ```

---

#### **18.9 Exim**
- Simple and highly configurable MTA.
- **Example**:
  ```bash
  # Send a test email
  exim -v recipient@example.com < message.txt
  ```

---

#### **18.10 Postfix**
- **Configuration**:
  - Primary files: `main.cf` and `master.cf`.
  - **Example**:
    ```bash
    # Check Postfix queue
    postqueue -p
    # Send queued mail
    postqueue -f
    ```

---

#### **18.11 Recommended Reading**
- Refer to books like *Postfix: The Definitive Guide* for in-depth understanding of mail systems and configurations.

This summary includes key concepts and example commands to manage email systems effectively. Let me know if further details are needed!