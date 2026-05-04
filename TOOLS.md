# TOOLS.md - SAC Environment Configuration

## MCP Connection
- **Endpoint:** `https://cart-a-share-xo-keqn98y.hello-xo.nl/sse`
- **Environment:** Production
- **Staging URL:** `https://cart-a-share.com` (for testing)

## Shopify Integration
- **Store URL:** `[STORE_NAME].myshopify.com`
- **Admin API Token:** `[STORED_IN_SECURE_CONFIG]`
- **API Version:** `2024-01`
- **Required Scopes:** `read_analytics, read_orders, read_products`

## Google Analytics
- **GA4 Property ID:** `[STORED_IN_SECURE_CONFIG]`
- **Service Account:** `[JSON_KEY_FILE_PATH]`
- **API Version:** Analytics Reporting API v4
- **Required Scopes:** `https://www.googleapis.com/auth/analytics.readonly`

## Email Provider
- **SMTP Server:** `[PROVIDER_SMTP_HOST]`
- **Port:** `587` (TLS) or `465` (SSL)
- **Authentication:** `[USERNAME/PASSWORD_IN_SECURE_CONFIG]`
- **Rate Limit:** `100 emails/hour` (adjust per provider)

## Slack Integration
- **Workspace:** Share-a-Cart Team
- **Bot Token:** `xoxb-[TOKEN_IN_SECURE_CONFIG]`
- **App Token:** `xapp-[TOKEN_IN_SECURE_CONFIG]`
- **Key Channels:** `#all-sac`, `#priv-exec`, `#priv-engineering`, `#priv-gtm`

## API Credentials Storage

**Never commit these to repos:**
```bash
# Environment variables or secure vault
SAC_MCP_ENDPOINT=https://cart-a-share-xo-keqn98y.hello-xo.nl/sse
SHOPIFY_STORE_URL=[store].myshopify.com
SHOPIFY_API_TOKEN=[secure_token]
GA4_PROPERTY_ID=[property_id]
GA4_SERVICE_ACCOUNT_KEY=[path_to_json]
EMAIL_SMTP_HOST=[provider_smtp]
EMAIL_USERNAME=[email_user]
EMAIL_PASSWORD=[email_pass]
```

## Monitoring Endpoints
- **Health Check:** `[MCP_ENDPOINT]/health`
- **Status Dashboard:** `[INTERNAL_DASHBOARD_URL]`
- **Error Logging:** `[LOG_AGGREGATION_SERVICE]`

## Development vs Production
- **Dev MCP:** Use staging URLs for testing
- **Prod MCP:** Live cart creation, real customer impact
- **Always verify** environment before executing cart operations
