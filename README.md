# 🆓 Lucy FreeOTP Gateway

**Absolutely free decentralized gateway for sending OTP codes and system notifications to your clients.**
Forget about expensive SMS services. The **Lucy** network uses P2P routing (Mesh) for instant delivery of authorization codes directly to users' phones.

---

## 🌟 How it works?
Instead of paying telecom operators for every SMS, you send messages through our decentralized network.
1. **P2P Architecture:** Messages are delivered through a network of distributed supernodes.
2. **Instant:** Direct WebSocket connections ensure delivery in milliseconds.
3. **Secure:** Codes arrive in an encrypted chat from the official system bot (preventing phishing).
4. **Unblockable:** If the internet is down, nodes can communicate via local Mesh protocols (Wi-Fi, Bluetooth).

---

## 📱 Step 1. App for Users
For your clients to receive OTP codes, they need to install the Lucy messenger.

👉 **[DOWNLOAD LATEST APK (Android)](https://0i2.ru/downloads/lucy.apk)**

---

## 🔑 Step 2. Get your Access Key (API_KEY)
We dropped boring registrations and web dashboards! To get API access:
1. Download the Lucy app from the link above.
2. Go to **Settings -> Contact Support** (this opens a chat with the server).
3. Send the command: `/api_key` (or just type "get token").
4. The bot will instantly generate a unique cryptographic **JWT token** for you.

---

## 💻 Step 3. Run your own Node (lucy-node)
For maximum privacy, security, and fault tolerance, you don't send messages to our servers. You send them to **your own node**, which you run on your infrastructure.

Node source code and Docker installation instructions:
👉 [Go to lucy-node repository](https://github.com/casetar/lusy/tree/master/server/lucy-node)

Quick install in 1 command (Linux):
```bash
curl -fsSL https://raw.githubusercontent.com/casetar/lusy/master/server/lucy-node/install.sh | bash
```

---

## 🚀 Step 4. Send OTP (Integration)
Once your `lucy-node` is running, you can send OTP codes from your backend using a simple HTTP POST request to your node's local port.

Example using `curl`:
```bash
curl -X POST http://127.0.0.1:7070/api/otp \
  -H "Content-Type: application/json" \
  -d '{
    "token": "YOUR_JWT_TOKEN_FROM_BOT",
    "peerId": "CLIENT_APP_ID",
    "text": "Your verification code: 1234"
  }'
```

**Parameters:**
- `token`: The JWT token you got from the bot in Step 2.
- `peerId`: The unique identifier of your user in the Lucy network (you can ask clients to provide it during registration, or generate QR codes for linking).
- `text`: The message text.

### Limits
**No limits!** Send as many notifications as your business needs. You only pay for the electricity of your own server.

---
*© 2026 Lucy P2P Network. Freedom of communication without servers.*
