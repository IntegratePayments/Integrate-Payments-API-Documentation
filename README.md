# Integrate-Payments-API-Documentation
Official API documentation and integration guides for the Integrate Payments gateway, featuring RESTful endpoints, SDKs, and secure transaction processing.
# Integrate Payments Developer Portal

Welcome to the official developer documentation repository for **Integrate Payments**. This portal provides the technical specifications, implementation guides, and API references required to integrate secure payment processing into web, mobile, and retail applications.

## 🚀 Quick Start

To begin testing our APIs, you will need a **Security Key** or **Tokenization Key** from your Merchant Control Panel.

- **Sandbox Gateway URL:** `https://integratepayments.transactiongateway.com/api/v2/three-step`
- **Testing Credentials:** Use Card Number `4111 1111 1111 1111` for successful authorizations in Test Mode.

## 🛠 Integration Methodologies

Select the integration method that best fits your security requirements and user experience:

### 1. [Collect.js Integration Guide](docs/collect-js) – Recommended client-side tokenization.
A JavaScript framework for modern web applications. It allows you to build custom checkout forms while remaining in a low PCI-compliance scope by tokenizing sensitive data directly in the browser.
* **Best for:** Custom web checkouts.
* **Key Feature:** Iframes for sensitive fields to ensure data never touches your server.

### 2. [Three-Step Redirect API Guide](docs/three-step-redirect)
A secure redirect-based integration that handles sensitive data on the gateway's side.
* **Best for:** High-security environments.
* **Flow:** 1. Init Transaction -> 2. Customer enters data on Gateway -> 3. Finalize on your server.

### 3. [Direct Post API Guide](docs/direct-post-payment-api)
A traditional server-to-server HTTPS POST integration.
* **Best for:** Backend-heavy systems or legacy migrations.
* **Note:** Requires a higher level of PCI compliance (SAQ D) as your server handles raw card data.

### 4. ChipDNA Cloud
Process retail, card-present transactions using internet-connected terminals without a local SDK.
* **Best for:** POS systems and physical retail locations.
* **Support:** Synchronous and Asynchronous polling.

### 5. Query API
A machine-readable reporting API for reconciliation and accounting.
* **Format:** Name/value pairs via HTTPS POST.

## 📂 Repository Structure

- `/docs`: Detailed markdown files for each API.
- `/examples`: Sample code snippets in Node.js, PHP, and cURL.
- `/assets`: Diagrams of transaction lifecycles and branding assets.

## 🔐 Security & Compliance

- **PCI DSS:** Always use **Collect.js** or **Three-Step Redirect** to minimize your PCI footprint.
- **API Keys:** Never commit your `security_key` to version control. Use environment variables.
- **Encryption:** All requests must be sent over HTTPS.

## 📖 Documentation Build
This site is built using [GitHub Pages](https://pages.github.com/). To run the documentation locally:
1. Clone the repo.
2. Install Jekyll: `bundle install`
3. Serve the site: `bundle exec jekyll serve`

---
© 2026 Integrate Payments. All rights reserved.
