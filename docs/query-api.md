# Query API (Reporting)

The Query API allows you to programmatically retrieve transaction data. This is essential for building custom dashboards, automated accounting, or verifying payment statuses.

**Endpoint:** `https://integratepayments.transactiongateway.com/api/query.php`

---

## 🔍 Common Search Variables
You can filter your report using these common variables:

| Variable | Description |
| :--- | :--- |
| `security_key` | **Required.** Your private API key. |
| `transaction_id` | Search for a specific transaction by its ID. |
| `orderid` | Search by your custom Order ID. |
| `start_date` | Format: `YYYYMMDDHHMMSS` |
| `end_date` | Format: `YYYYMMDDHHMMSS` |

---

## 💻 Example Request (cURL)
Use this command to pull details for a specific transaction:

```bash
curl -X POST https://integratepayments.transactiongateway.com/api/query.php \
  -d "security_key=YOUR_PRIVATE_KEY" \
  -d "transaction_id=123456789"
