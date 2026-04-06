# Direct Post Payment API

The Direct Post API is a server-to-server integration that allows you to submit credit card and ACH transactions directly to the gateway via an HTTPS POST request.

## 🔐 Authentication
All requests must include your `security_key`, which can be found in your Merchant Control Panel under **Settings** -> **Security Keys**.

**Endpoint:** `https://integratepayments.transactiongateway.com/api/transact.php`

---

## 🚀 Required Fields
To process a basic sale, you must send these minimum variables:

| Variable | Description | Example |
| :--- | :--- | :--- |
| `security_key` | Your private API Key | `your_key_here` |
| `type` | Transaction type | `sale` |
| `amount` | Amount in decimal format | `10.00` |
| `ccnumber` | Credit card number | `4111111111111111` |
| `ccexp` | Expiration (MMYY) | `1230` |

---

## 💻 Example Request (cURL)
Developers can test the connection using this command in their terminal:

```bash
curl -X POST [https://integratepayments.transactiongateway.com/api/transact.php](https://integratepayments.transactiongateway.com/api/transact.php) \
  -d "security_key=YOUR_PRIVATE_KEY" \
  -d "type=sale" \
  -d "amount=1.00" \
  -d "ccnumber=4111111111111111" \
  -d "ccexp=1230" \
  -d "cvv=123"
