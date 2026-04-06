# ChipDNA Cloud API

ChipDNA Cloud allows you to process retail, card-present transactions using internet-connected terminals without needing a local SDK.

## 📡 How it Works
Unlike web integrations, ChipDNA Cloud communicates directly with your payment terminal over the internet.
1. **Initiate**: Your POS sends a transaction request to the Cloud.
2. **Interact**: The terminal lights up, and the customer swipes, dips, or taps their card.
3. **Result**: The Cloud sends the approval or decline back to your POS.

---

## 🛠️ Step 1: Register your Terminal
Before processing, you must link your terminal using its unique **POI Device ID** (found in the device menu).

**Endpoint:** `https://integratepayments.transactiongateway.com/api/v2/terminal-registration`

---

## 💳 Step 2: Start a Sale (cURL)
You can choose **Synchronous** (wait for the result) or **Asynchronous** (check back later). 

```bash
curl -X POST https://integratepayments.transactiongateway.com/api/v2/terminal-transaction \
  -d "api-key=YOUR_PRIVATE_KEY" \
  -d "terminal-id=YOUR_TERMINAL_ID" \
  -d "amount=10.00" \
  -d "action=sale"
