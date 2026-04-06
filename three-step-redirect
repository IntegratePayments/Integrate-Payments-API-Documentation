# Three-Step Redirect API

The Three-Step Redirect API is the most secure way to process payments while keeping your server completely out of the path of sensitive payment data.

## 🔄 The Process
1. **Initiate**: Your server sends transaction details (amount, order ID) to the gateway. The gateway returns a unique `form-url`.
2. **Redirect**: You send the customer to that `form-url` to enter their credit card details securely on our hosted page.
3. **Finalize**: The gateway redirects the customer back to your site with a `token-id`. Your server then performs one final "complete" step to capture the funds.

---

## 🚀 Step 1: Obtain a Form-URL
Send a POST request from your server to the Three-Step endpoint.

**Endpoint:** `https://integratepayments.transactiongateway.com/api/v2/three-step`

```bash
curl -X POST https://integratepayments.transactiongateway.com/api/v2/three-step \
  -d "api-key=YOUR_PRIVATE_KEY" \
  -d "redirect-url=https://your-site.com/receipt" \
  -d "amount=25.00" \
  -d "action=sale"
