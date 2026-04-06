# Three-Step Redirect API Integration Guide

The Three-Step Redirect methodology is a secure way to process payments. By using this method, your web server never sees sensitive credit card data, which significantly simplifies your PCI compliance requirements.

## Integration Workflow

1.  **Step One:** Send transaction details to the Gateway to receive a temporary `form-url`.
2.  **Step Two:** Use that `form-url` as the `action` for your payment form so sensitive data goes directly to the Gateway.
3.  **Step Three:** Receive a `token-id` and submit a final request to complete the transaction.

---

## Step 1: Initiate the Transaction

Submit an HTTPS `POST` to the Gateway with the transaction details (amount, order info, etc.). **Do not include credit card numbers in this step.**

### Required Parameters
| Parameter | Description |
| :--- | :--- |
| `api-key` | Your unique API Key for authentication. |
| `redirect-url` | The page on your site the customer returns to after Step 2. |
| `amount` | The total amount to be charged (e.g., `15.00`). |

### Example Request (XML)
```xml
<sale>
    <api-key>YOUR_API_KEY</api-key>
    <redirect-url>https://your-site.com/checkout/complete</redirect-url>
    <amount>19.99</amount>
</sale>
```
The Gateway will return a `<form-url>` which you must use in the next step.

## Step 2: Collect Sensitive Data

Create an HTML form on your website. The action attribute of the form must be the `form-url` you received in Step 1.
```html
<form action="[INSERT_FORM_URL_HERE]" method="POST">
    <input type="text" name="billing-cc-number" placeholder="Card Number">
    <input type="text" name="billing-cc-exp" placeholder="MMYY">
    <input type="text" name="billing-cvv" placeholder="CVV">
    <button type="submit">Submit Payment</button>
</form>
```
When the customer clicks submit, their browser sends the card data directly to the Gateway. The Gateway then redirects the customer back to your redirect-url with a token-id appended to the query string.

## Step 3: Complete the Transaction

Once the customer is redirected back to your site, extract the token-id from the URL and send a final complete-action request to the Gateway via a background HTTPS POST.
```xml
<complete-action>
    <api-key>YOUR_API_KEY</api-key>
    <token-id>TOKEN_FROM_URL</token-id>
</complete-action>
```

---

**Response Codes**
The final response will include a `result` code indicating the status:

`100`: Transaction Approved

`200-264`: Transaction Declined (e.g., 202 for Insufficient Funds)

`300`: Transaction Rejected by Gateway

`400`: Transaction Error

---

**Subsequent Operations**
After a successful transaction, you will receive a `transaction-id`. You can use this ID later for:

`capture`: Settling a previous authorization.

`void`: Canceling a transaction before it settles.

`refund`: Returning funds to a customer on a settled transaction.
