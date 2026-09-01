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
2. Go to **Profile -> About -> Contact Support** (this opens a chat with the server).
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

## 🚀 Step 4. Send Notifications (Integration)
Once your `lucy-node` is running, you can send notifications from your backend using a simple HTTP POST request to your node's local port.

You have two ways to send notifications: **OTP Codes** or **Business Statuses**.

### Option A: Send simple OTP Code
Use `type: "otp"`. You only need to pass the code, and the app will format it automatically with a lock icon.

```bash
curl -X POST http://127.0.0.1:7070/api/otp \\
  -H "Content-Type: application/json" \\
  -d '{
    "type": "otp",
    "to_peer_id": "CLIENT_APP_ID",
    "code": "1234",
    "api_key": "YOUR_JWT_TOKEN_FROM_BOT"
  }'
```

### Option B: Send a Business Status
Use `type: "status"`. Perfect for order updates, appointment reminders, etc.

```bash
curl -X POST http://127.0.0.1:7070/api/otp \\
  -H "Content-Type: application/json" \\
  -d '{
    "type": "status",
    "to_peer_id": "CLIENT_APP_ID",
    "sender_name": "Kedr",
    "text": "Your order #832 is packed and ready!",
    "api_key": "YOUR_JWT_TOKEN_FROM_BOT"
  }'
```

**⚠️ Important Note about IP Address (`127.0.0.1`):**
- Use `127.0.0.1` (localhost) **only** if your backend (website/CRM) is running on the **same server** as `lucy-node`.
- If you are sending requests from an Android/iOS app or a different external server, replace `127.0.0.1` with the **Public IP Address** of your node's server and ensure port `7070` is open in your firewall.

**Parameters:**
- `type`: Either `"otp"` or `"status"`.
- `api_key`: The JWT token you got from the bot in Step 2.
- `to_peer_id`: The unique identifier of your user in the Lucy network (you can ask clients to provide it during registration).
- `code` / `text`: The content of your message.

### Limits
**No limits!** Send as many notifications as your business needs. You only pay for the electricity of your own server.

---
*© 2026 Lucy P2P Network. Freedom of communication without servers.*
