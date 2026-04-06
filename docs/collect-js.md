# Collect.js Integration Guide

Collect.js allows you to build a completely custom checkout experience while keeping sensitive cardholder data off your servers. This reduces your PCI DSS compliance scope significantly.

---

## 💳 How it Works
1. **Initialize**: Load the Collect.js library with your Tokenization Key.
2. **Secure Fields**: Collect.js creates secure iframes for the Card Number and CVV.
3. **Tokenize**: Upon form submission, Collect.js returns a `payment_token`.
4. **Process**: Send that token to your server to complete the charge.

---

## 🚀 Step 1: Include the Script
Add this to your HTML `<head>`. Replace `YOUR_PUBLIC_KEY_HERE` with your actual key.

```javascript
<script src="https://gateway-url.com/tokenization/collect.js" 
        data-tokenization-key="YOUR_PUBLIC_KEY_HERE">
</script>
```

## 🛠️ Step 2: Create the Payment Form
Copy and paste this into your HTML <body>. These empty div elements are where the gateway will securely "inject" the credit card fields.

'''html
<form id="my-payment-form">
    <div id="collectjs-card-number"></div>
    <div id="collectjs-cvv"></div>
    <div id="collectjs-expiration"></div>
    
    <button type="submit" id="submit-btn">Pay Now</button>
</form>
'''

## 🔄 Step 3: Handle the Response
Add this JavaScript to capture the secure token.

```javascript
CollectJS.configure({
    'callback': function(response) {
        console.log("Tokenization Successful!");
        console.log("Token ID: " + response.token);
    }
});
'''
