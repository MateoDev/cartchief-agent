# ANALYTICS.md - SAC Analytics & Monitoring

## Google Analytics Integration

### Key Metrics to Pull
- **Traffic Volume** - Daily/weekly visitors
- **Conversion Rate** - Visitors to cart creation
- **Top Referrers** - Where traffic originates
- **Page Performance** - Cart creation funnel analysis
- **Geographic Data** - User locations and behavior
- **Device Breakdown** - Mobile vs desktop usage

### Connection Requirements
- **GA4 Property ID** - [Stored in secure config]
- **Service Account Credentials** - [JSON key file]
- **API Access** - Analytics Reporting API v4
- **Scopes Required** - `https://www.googleapis.com/auth/analytics.readonly`

### Daily Pull Schedule
- **9:00 AM UTC** - Previous day's complete data
- **Real-time checks** - Every 4 hours for anomaly detection
- **Weekly summaries** - Mondays for previous week trends

## Shopify Analytics Integration

### Key Metrics to Pull
- **Order Volume** - Daily orders and trends
- **Revenue** - Gross sales, net revenue, average order value
- **Top Products** - Best sellers by volume and revenue
- **Customer Data** - New vs returning customers
- **Cart Abandonment** - Checkout funnel analysis
- **Geographic Sales** - Sales by region/country

### Connection Requirements
- **Shopify Store URL** - [store-name].myshopify.com
- **Admin API Access Token** - [Stored securely]
- **API Version** - 2024-01 (latest stable)
- **Required Scopes** - `read_analytics`, `read_orders`, `read_products`

### Data Points
```json
{
  "orders": {
    "total_orders": 123,
    "total_revenue": 45678.90,
    "average_order_value": 89.12
  },
  "traffic": {
    "visitors": 5432,
    "conversion_rate": 2.85
  },
  "products": [
    {"name": "Product Name", "orders": 45, "revenue": 1234.56}
  ]
}
```

## 200+ Retailer Cart Activity Monitoring

### Supported Retailers
- **Major Platforms** - Amazon, Shopify, WooCommerce, BigCommerce
- **Department Stores** - Target, Walmart, Macy's, Nordstrom
- **Specialty Retail** - Best Buy, Home Depot, Petco, etc.
- **International** - Amazon UK/DE/JP, Shopify global stores

### Monitoring Metrics
- **Cart Creation Volume** - Per retailer, per day
- **Success Rate** - Successful cart shares vs attempts  
- **Error Rates** - API failures, invalid products, etc.
- **Response Times** - Cart creation performance by retailer
- **Popular Products** - Most frequently shared items

### Data Collection
```json
{
  "retailer": "amazon",
  "date": "2024-01-15",
  "metrics": {
    "carts_created": 234,
    "success_rate": 94.2,
    "avg_response_time": 1.2,
    "errors": {
      "invalid_asin": 8,
      "out_of_stock": 4,
      "api_timeout": 2
    }
  }
}
```

## Anomaly Detection Rules

### Traffic Anomalies
**Trigger alerts when:**
- **Traffic drop** >30% vs 7-day average
- **Traffic spike** >200% vs 7-day average (possible bot attack)
- **Conversion rate drop** >40% vs 7-day average
- **Zero traffic** for >2 hours during business hours

### Revenue Anomalies  
**Trigger alerts when:**
- **Revenue drop** >25% vs 7-day average
- **Order volume drop** >35% vs 7-day average
- **Average order value** changes >50% vs 7-day average
- **Refund rate spike** >15% above normal

### System Anomalies
**Trigger alerts when:**
- **API error rate** >10% for any retailer
- **Cart creation failures** >15% for >1 hour
- **Response time degradation** >5 seconds average
- **Complete service outage** for any monitored retailer

### Alert Format
```
🚨 **Anomaly Alert - [Type]**

**Metric:** [What's anomalous]
**Current Value:** [X] 
**Expected Range:** [Y-Z]
**Variance:** [+/-X%]
**Duration:** [How long this has been happening]

**Potential Causes:**
• [Hypothesis 1]
• [Hypothesis 2]

**Recommended Actions:**
• [Action 1]
• [Action 2]

**Auto-assigned to:** [@team-member]
```

## Reporting Schedules

### Daily (9:00 AM UTC)
- Traffic summary to `#all-sac`
- Revenue summary to `#priv-exec`  
- Error rate check to `#priv-engineering`

### Weekly (Mondays, 9:00 AM UTC)
- Comprehensive week-over-week analysis
- Top performing products/retailers
- Trend analysis and recommendations
- Posted to `#priv-exec` and `#all-sac`

### Monthly (1st of month, 9:00 AM UTC)
- Full business intelligence report
- Year-over-year comparisons
- Retailer performance rankings
- Strategic recommendations
- Posted to `#priv-exec` only

## Data Storage & Privacy

### Retention Policy
- **Raw analytics data** - 2 years
- **Aggregated reports** - 5 years  
- **Personal customer data** - Follow GDPR/CCPA requirements
- **Error logs** - 90 days

### Security Requirements
- **API credentials** stored in secure vault
- **Data encryption** at rest and in transit
- **Access logging** for all analytics queries
- **Regular credential rotation** (quarterly)

### Compliance
- **GDPR compliance** for EU customer data
- **CCPA compliance** for CA residents
- **SOC 2** requirements for data handling
- **Regular audits** of data access and usage