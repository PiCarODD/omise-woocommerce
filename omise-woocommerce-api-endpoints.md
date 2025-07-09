# Omise API Endpoints for WooCommerce Integration

This document lists all the API endpoints used by Omise in WooCommerce integration, customized for your WordPress site at `https://localhost:4433/wordpress-6.8.1/wordpress/`.

## Base URLs

- **Omise API Base URL**: `https://api.omise.co`
- **Omise Vault URL** (for tokenization): `https://vault.omise.co`
- **Your WordPress Site**: `https://localhost:4433/wordpress-6.8.1/wordpress/`

---

## 1. Authentication & Account Information

### Account Information
- **GET** `https://api.omise.co/account`
  - Retrieve account information and capabilities

### Balance
- **GET** `https://api.omise.co/balance`
  - Get current account balance

### Capabilities
- **GET** `https://api.omise.co/capability`
  - Get account capabilities and supported payment methods

---

## 2. Token Management (Client-Side)

### Create Token (Secure)
- **POST** `https://vault.omise.co/tokens`
  - Create secure payment tokens for credit cards
  - **Note**: This endpoint is used client-side for security

### Retrieve Token
- **GET** `https://vault.omise.co/tokens/{token_id}`
  - Retrieve token information

---

## 3. Customer Management

### Create Customer
- **POST** `https://api.omise.co/customers`
  - Create new customer records

### Retrieve Customer
- **GET** `https://api.omise.co/customers/{customer_id}`
  - Get customer information

### Update Customer
- **PATCH** `https://api.omise.co/customers/{customer_id}`
  - Update customer details

### List Customers
- **GET** `https://api.omise.co/customers`
  - List all customers with pagination

### Delete Customer
- **DELETE** `https://api.omise.co/customers/{customer_id}`
  - Delete a customer

---

## 4. Card Management

### Create Card (for Customer)
- **POST** `https://api.omise.co/customers/{customer_id}/cards`
  - Add a card to existing customer

### Retrieve Card
- **GET** `https://api.omise.co/customers/{customer_id}/cards/{card_id}`
  - Get card information

### Update Card
- **PATCH** `https://api.omise.co/customers/{customer_id}/cards/{card_id}`
  - Update card details

### List Cards
- **GET** `https://api.omise.co/customers/{customer_id}/cards`
  - List all cards for a customer

### Delete Card
- **DELETE** `https://api.omise.co/customers/{customer_id}/cards/{card_id}`
  - Remove a card from customer

---

## 5. Payment Sources

### Create Source
- **POST** `https://api.omise.co/sources`
  - Create payment sources for various payment methods:
    - Credit/Debit Cards
    - Internet Banking (SCB, BBL, KTB, BAY, etc.)
    - E-Wallets (TrueMoney, Rabbit LINE Pay, etc.)
    - QR Payments (PromptPay, PayNow)
    - Installments (KBank, BAY, SCB, etc.)
    - Buy Now Pay Later (Atome, ShopeePay)
    - Mobile Banking
    - Alipay, GrabPay, etc.

### Retrieve Source
- **GET** `https://api.omise.co/sources/{source_id}`
  - Get source information

---

## 6. Charges (Payments)

### Create Charge
- **POST** `https://api.omise.co/charges`
  - Process payments using various methods:
    - Token-based charges
    - Customer-based charges
    - Source-based charges

### Retrieve Charge
- **GET** `https://api.omise.co/charges/{charge_id}`
  - Get charge details and status

### List Charges
- **GET** `https://api.omise.co/charges`
  - List all charges with filtering options

### Capture Charge
- **POST** `https://api.omise.co/charges/{charge_id}/capture`
  - Capture authorized charges (for manual capture mode)

### Expire Charge
- **POST** `https://api.omise.co/charges/{charge_id}/expire`
  - Expire pending charges (for specific payment methods)

### Reverse Charge
- **POST** `https://api.omise.co/charges/{charge_id}/reverse`
  - Reverse authorized charges

---

## 7. Refunds

### Create Refund
- **POST** `https://api.omise.co/charges/{charge_id}/refunds`
  - Create full or partial refunds

### Retrieve Refund
- **GET** `https://api.omise.co/charges/{charge_id}/refunds/{refund_id}`
  - Get refund details

### List Refunds (for Charge)
- **GET** `https://api.omise.co/charges/{charge_id}/refunds`
  - List all refunds for a specific charge

### List All Refunds
- **GET** `https://api.omise.co/refunds`
  - List all refunds across account

---

## 8. Events & Webhooks

### List Events
- **GET** `https://api.omise.co/events`
  - Get all events for monitoring

### Retrieve Event
- **GET** `https://api.omise.co/events/{event_id}`
  - Get specific event details

### List Events for Charge
- **GET** `https://api.omise.co/charges/{charge_id}/events`
  - Get events related to specific charge

---

## 9. Disputes

### List Disputes
- **GET** `https://api.omise.co/disputes`
  - Get all disputes

### Retrieve Dispute
- **GET** `https://api.omise.co/disputes/{dispute_id}`
  - Get dispute details

### Accept Dispute
- **PATCH** `https://api.omise.co/disputes/{dispute_id}`
  - Accept or update dispute

---

## 10. Schedules (Recurring Payments)

### Create Schedule
- **POST** `https://api.omise.co/schedules`
  - Set up recurring payments

### Retrieve Schedule
- **GET** `https://api.omise.co/schedules/{schedule_id}`
  - Get schedule details

### List Schedules
- **GET** `https://api.omise.co/schedules`
  - List all schedules

### Delete Schedule
- **DELETE** `https://api.omise.co/schedules/{schedule_id}`
  - Cancel recurring schedule

---

## 11. Transfers

### Create Transfer
- **POST** `https://api.omise.co/transfers`
  - Transfer funds to bank accounts

### Retrieve Transfer
- **GET** `https://api.omise.co/transfers/{transfer_id}`
  - Get transfer status

### List Transfers
- **GET** `https://api.omise.co/transfers`
  - List all transfers

---

## 12. Recipients (For Transfers)

### Create Recipient
- **POST** `https://api.omise.co/recipients`
  - Add bank account for transfers

### Retrieve Recipient
- **GET** `https://api.omise.co/recipients/{recipient_id}`
  - Get recipient details

### List Recipients
- **GET** `https://api.omise.co/recipients`
  - List all recipients

---

## 13. Search

### Search Charges
- **GET** `https://api.omise.co/search`
  - Advanced search for charges with filters

---

## 14. WooCommerce-Specific Endpoints

### Standard WooCommerce REST API Endpoints
- **GET** `https://localhost:4433/wordpress-6.8.1/wordpress/wp-json/wc/v3/orders`
  - Alternative: `https://localhost:4433/wordpress-6.8.1/wordpress/index.php?rest_route=/wc/v3/orders`
  - List orders

- **GET** `https://localhost:4433/wordpress-6.8.1/wordpress/wp-json/wc/v3/orders/{order_id}`
  - Alternative: `https://localhost:4433/wordpress-6.8.1/wordpress/index.php?rest_route=/wc/v3/orders/{order_id}`
  - Get specific order details

- **POST** `https://localhost:4433/wordpress-6.8.1/wordpress/wp-json/wc/v3/orders/{order_id}`
  - Alternative: `https://localhost:4433/wordpress-6.8.1/wordpress/index.php?rest_route=/wc/v3/orders/{order_id}`
  - Update order status

- **POST** `https://localhost:4433/wordpress-6.8.1/wordpress/wp-json/wc/v3/orders/{order_id}/refunds`
  - Alternative: `https://localhost:4433/wordpress-6.8.1/wordpress/index.php?rest_route=/wc/v3/orders/{order_id}/refunds`
  - Create refunds

### Omise Plugin Webhook Endpoints
- **POST** `https://localhost:4433/wordpress-6.8.1/wordpress/?wc-api=omise_webhook`
  - Main webhook endpoint for Omise notifications (legacy format)

- **POST** `https://localhost:4433/wordpress-6.8.1/wordpress/wc-api/omise_webhook`
  - Alternative webhook endpoint format

### Payment Return/Callback URLs
- **GET** `https://localhost:4433/wordpress-6.8.1/wordpress/?wc-api=omise_callback&order_id={order_id}`
  - Return URL after 3DS authentication or redirect payments

- **GET** `https://localhost:4433/wordpress-6.8.1/wordpress/checkout/order-received/{order_id}/?key={order_key}`
  - WooCommerce order confirmation page

### Omise Payment Processing (AJAX)
- **POST** `https://localhost:4433/wordpress-6.8.1/wordpress/wp-admin/admin-ajax.php`
  - Action: `omise_create_token` - Create secure token
  - Action: `omise_process_payment` - Process payment
  - Action: `omise_create_source` - Create payment source

### Order Status and Notes
- **POST** `https://localhost:4433/wordpress-6.8.1/wordpress/wp-admin/admin-ajax.php`
  - Action: `omise_sync_order_status` - Sync payment status
  - Action: `omise_manual_sync` - Manual payment sync

### WooCommerce Checkout Endpoints
- **POST** `https://localhost:4433/wordpress-6.8.1/wordpress/?wc-ajax=checkout`
  - Process checkout form submission

- **POST** `https://localhost:4433/wordpress-6.8.1/wordpress/?wc-ajax=update_order_review`
  - Update order review during checkout

---

## 15. Common Payment Method Endpoints

### Credit/Debit Cards
- Uses token-based or customer-based charges
- Supports 3DS authentication

### Internet Banking
- **POST** `https://api.omise.co/charges` with source type:
  - `internet_banking_scb`
  - `internet_banking_bbl`
  - `internet_banking_ktb`
  - `internet_banking_bay`

### E-Wallets
- **POST** `https://api.omise.co/charges` with source type:
  - `truemoney`
  - `rabbit_linepay`
  - `grabpay`
  - `shopeepay`

### QR Payments
- **POST** `https://api.omise.co/charges` with source type:
  - `promptpay`
  - `paynow`

### Installments
- **POST** `https://api.omise.co/charges` with source type:
  - `installment_kbank`
  - `installment_bay`
  - `installment_scb`

---

## 16. Authentication Headers

### Omise API Authentication
All API requests to `https://api.omise.co` require:

```http
Authorization: Basic {base64(secret_key:)}
Content-Type: application/json
Omise-Version: 2019-05-29
```

For vault requests to `https://vault.omise.co`:

```http
Authorization: Basic {base64(public_key:)}
Content-Type: application/json
```

### WooCommerce REST API Authentication
For WooCommerce REST API endpoints, you need:

1. **Consumer Key and Consumer Secret** (generated in WooCommerce > Settings > Advanced > REST API)

```http
Authorization: Basic {base64(consumer_key:consumer_secret)}
Content-Type: application/json
```

2. **Alternative Query Parameters:**
```
https://localhost:4433/wordpress-6.8.1/wordpress/wp-json/wc/v3/orders?consumer_key=ck_xxx&consumer_secret=cs_xxx
```

### WordPress AJAX Authentication
For AJAX requests to `admin-ajax.php`:

```http
Content-Type: application/x-www-form-urlencoded
X-Requested-With: XMLHttpRequest
```

Include nonce for security:
```
action=omise_process_payment&nonce={wp_nonce}
```

---

## 17. Common Response Codes

- **200 OK**: Successful request
- **201 Created**: Resource created successfully
- **400 Bad Request**: Invalid request parameters
- **401 Unauthorized**: Invalid API key
- **403 Forbidden**: Insufficient permissions
- **404 Not Found**: Resource not found
- **422 Unprocessable Entity**: Validation errors
- **429 Too Many Requests**: Rate limit exceeded
- **500 Internal Server Error**: Server error

---

## 18. Webhook Events

Your webhook endpoint will receive these events:

### Charge Events
- `charge.create`
- `charge.complete`
- `charge.capture`
- `charge.expire`
- `charge.reverse`
- `charge.update`

### Customer Events
- `customer.create`
- `customer.update`
- `customer.destroy`

### Card Events
- `card.update`
- `card.destroy`

### Refund Events
- `refund.create`

### Dispute Events
- `dispute.create`
- `dispute.update`
- `dispute.close`

---

## 19. Testing

### Test Mode URLs
All endpoints remain the same, but use test API keys:
- Public key: `pkey_test_...`
- Secret key: `skey_test_...`

### Test Cards
Use Omise test card numbers for development:
- **4242424242424242** - Successful payment
- **4000000000000002** - Card declined
- **4000000000000341** - Charge disputed

---

## 20. Troubleshooting & Setup Guide

### Fixing 500 Internal Server Errors

1. **Check Pretty Permalinks:**
   - Go to WordPress Admin > Settings > Permalinks
   - Ensure permalinks are set to "Post name" or custom structure
   - If disabled, use `index.php?rest_route=` format

2. **Enable WooCommerce REST API:**
   - Go to WooCommerce > Settings > Advanced > REST API
   - Add New API Key
   - Generate Consumer Key and Consumer Secret

3. **Verify Omise Plugin Installation:**
   - Ensure Omise WooCommerce plugin is installed and activated
   - Check plugin version (use latest v6.2.1 or newer)
   - Verify Omise API keys are configured

4. **Test Endpoints:**
   ```bash
   # Test WooCommerce API
   curl -u consumer_key:consumer_secret \
     https://localhost:4433/wordpress-6.8.1/wordpress/wp-json/wc/v3/orders
   
   # Alternative format
   curl https://localhost:4433/wordpress-6.8.1/wordpress/index.php?rest_route=/wc/v3/orders \
     -u consumer_key:consumer_secret
   ```

5. **Check WordPress REST API:**
   ```bash
   # Basic WordPress API test
   curl https://localhost:4433/wordpress-6.8.1/wordpress/wp-json/
   ```

6. **Debug Mode:**
   - Add to `wp-config.php`:
   ```php
   define('WP_DEBUG', true);
   define('WP_DEBUG_LOG', true);
   ```
   - Check `/wp-content/debug.log` for errors

### Webhook Setup for Omise

1. **Configure in Omise Dashboard:**
   - Test Mode: `https://localhost:4433/wordpress-6.8.1/wordpress/?wc-api=omise_webhook`
   - Live Mode: `https://yourdomain.com/?wc-api=omise_webhook`

2. **Verify Webhook Endpoint:**
   ```bash
   curl -X POST https://localhost:4433/wordpress-6.8.1/wordpress/?wc-api=omise_webhook \
     -H "Content-Type: application/json" \
     -d '{"test": "webhook"}'
   ```

---

## Notes

1. Always use HTTPS for all API communications
2. Implement proper error handling for all endpoints
3. Store API keys securely (never in client-side code)
4. Use webhooks for real-time payment status updates
5. Implement idempotency for critical operations
6. Follow PCI DSS guidelines when handling card data
7. Test thoroughly in sandbox mode before going live
8. **For latest WordPress/WooCommerce**: Always check if pretty permalinks are enabled
9. **Use `index.php?rest_route=` format** if pretty permalinks are disabled
10. **Generate WooCommerce API keys** in WooCommerce > Settings > Advanced > REST API

This comprehensive list covers all the major API endpoints used by Omise in WooCommerce integration. The endpoints are updated for the latest WordPress/WooCommerce versions and include troubleshooting guidance.