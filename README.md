[![MseeP.ai Security Assessment Badge](https://mseep.net/mseep-audited.png)](https://mseep.ai/app/techspawn-woocommerce-mcp-server)

# WooCommerce MCP Server

A Model Context Protocol (MCP) server for WooCommerce integration, compatible with Windows, macOS, and Linux.

## Overview

This MCP server enables interaction with WooCommerce stores through the WordPress REST API. It provides comprehensive tools for managing all aspects of products, orders, customers, shipping, taxes, discounts, and store configuration using JSON-RPC 2.0 protocol.

## Installation

1. Clone the repository
2. Install dependencies:
```bash
npm install
```
3. Build the project:
```bash
npm run build
```

## Configuration

Add the server to your MCP settings file with environment variables for credentials:

```json
{
  "mcpServers": {
    "woocommerce": {
      "command": "node",
      "args": ["path/to/build/index.js"],
      "env": {
        "WORDPRESS_SITE_URL": "https://your-wordpress-site.com",
        "WOOCOMMERCE_CONSUMER_KEY": "your-woocommerce-consumer-key",
        "WOOCOMMERCE_CONSUMER_SECRET": "your-woocommerce-consumer-secret",
        "WORDPRESS_USERNAME": "your-wordpress-username",
        "WORDPRESS_PASSWORD": "your-wordpress-password"
      }
    }
  }
}
```

### Environment Variables

#### Required for WooCommerce API access:
- `WORDPRESS_SITE_URL`: Your WordPress site URL (WooCommerce is a WordPress plugin)
- `WOOCOMMERCE_CONSUMER_KEY`: WooCommerce REST API consumer key
- `WOOCOMMERCE_CONSUMER_SECRET`: WooCommerce REST API consumer secret

#### Required only for WordPress API methods:
- `WORDPRESS_USERNAME`: WordPress username with appropriate permissions
- `WORDPRESS_PASSWORD`: WordPress password for authentication

You can also provide these credentials in the request parameters if you prefer not to use environment variables.

## Authentication Options

### WooCommerce Authentication
WooCommerce API access requires consumer keys that you can generate in your WordPress dashboard under WooCommerce → Settings → Advanced → REST API.

### WordPress Authentication
For WordPress-specific methods (like managing posts), you need to provide:
- Username/password credentials for basic authentication
- The WordPress REST API must be enabled on your site

## API Methods

The server supports both WordPress and WooCommerce API methods. Here's a list of available methods grouped by category:

### WordPress Content Management

These methods require WordPress username/password credentials and are independent of the WooCommerce API.

| Method | Description |
|--------|-------------|
| `create_post` | Create a new WordPress post |
| `get_posts` | Retrieve WordPress posts |
| `update_post` | Update an existing WordPress post |
| `get_post_meta` | Get post metadata |
| `update_post_meta` | Update post metadata |
| `create_post_meta` | Create post metadata |
| `delete_post_meta` | Delete post metadata |

### WooCommerce Products

| Method | Description |
|--------|-------------|
| `get_products` | Retrieve a list of products |
| `get_product` | Get a single product by ID |
| `create_product` | Create a new product |
| `update_product` | Update an existing product |
| `delete_product` | Delete a product |
| `get_product_meta` | Get product metadata |
| `create_product_meta` | Create/update product metadata |
| `update_product_meta` | Update product metadata (alias for create) |
| `delete_product_meta` | Delete product metadata |

### Product Categories

| Method | Description |
|--------|-------------|
| `get_product_categories` | Retrieve product categories |
| `get_product_category` | Get a single product category |
| `create_product_category` | Create a new product category |
| `update_product_category` | Update a product category |
| `delete_product_category` | Delete a product category |

### Product Tags

| Method | Description |
|--------|-------------|
| `get_product_tags` | Retrieve product tags |
| `get_product_tag` | Get a single product tag |
| `create_product_tag` | Create a new product tag |
| `update_product_tag` | Update a product tag |
| `delete_product_tag` | Delete a product tag |

### Product Attributes

| Method | Description |
|--------|-------------|
| `get_product_attributes` | Retrieve product attributes |
| `get_product_attribute` | Get a single product attribute |
| `create_product_attribute` | Create a new product attribute |
| `update_product_attribute` | Update a product attribute |
| `delete_product_attribute` | Delete a product attribute |
| `get_attribute_terms` | Retrieve attribute terms |
| `get_attribute_term` | Get a single attribute term |
| `create_attribute_term` | Create a new attribute term |
| `update_attribute_term` | Update an attribute term |
| `delete_attribute_term` | Delete an attribute term |

### Product Variations

| Method | Description |
|--------|-------------|
| `get_product_variations` | Retrieve product variations |
| `get_product_variation` | Get a single product variation |
| `create_product_variation` | Create a new product variation |
| `update_product_variation` | Update a product variation |
| `delete_product_variation` | Delete a product variation |

### Product Reviews

| Method | Description |
|--------|-------------|
| `get_product_reviews` | Retrieve product reviews |
| `get_product_review` | Get a single product review |
| `create_product_review` | Create a new product review |
| `update_product_review` | Update a product review |
| `delete_product_review` | Delete a product review |

### WooCommerce Orders

| Method | Description |
|--------|-------------|
| `get_orders` | Retrieve a list of orders |
| `get_order` | Get a single order by ID |
| `create_order` | Create a new order |
| `update_order` | Update an existing order |
| `delete_order` | Delete an order |
| `get_order_meta` | Get order metadata |
| `create_order_meta` | Create/update order metadata |
| `update_order_meta` | Update order metadata (alias for create) |
| `delete_order_meta` | Delete order metadata |

### Order Notes

| Method | Description |
|--------|-------------|
| `get_order_notes` | Retrieve order notes |
| `get_order_note` | Get a single order note |
| `create_order_note` | Create a new order note |
| `delete_order_note` | Delete an order note |

### Order Refunds

| Method | Description |
|--------|-------------|
| `get_order_refunds` | Retrieve order refunds |
| `get_order_refund` | Get a single order refund |
| `create_order_refund` | Create a new order refund |
| `delete_order_refund` | Delete an order refund |

### WooCommerce Customers

| Method | Description |
|--------|-------------|
| `get_customers` | Retrieve a list of customers |
| `get_customer` | Get a single customer by ID |
| `create_customer` | Create a new customer |
| `update_customer` | Update an existing customer |
| `delete_customer` | Delete a customer |
| `get_customer_meta` | Get customer metadata |
| `create_customer_meta` | Create/update customer metadata |
| `update_customer_meta` | Update customer metadata (alias for create) |
| `delete_customer_meta` | Delete customer metadata |

### Shipping

| Method | Description |
|--------|-------------|
| `get_shipping_zones` | Retrieve shipping zones |
| `get_shipping_zone` | Get a single shipping zone |
| `create_shipping_zone` | Create a new shipping zone |
| `update_shipping_zone` | Update a shipping zone |
| `delete_shipping_zone` | Delete a shipping zone |
| `get_shipping_methods` | Retrieve shipping methods |
| `get_shipping_zone_methods` | Get shipping methods for a zone |
| `create_shipping_zone_method` | Create a new shipping method for a zone |
| `update_shipping_zone_method` | Update a shipping method for a zone |
| `delete_shipping_zone_method` | Delete a shipping method from a zone |
| `get_shipping_zone_locations` | Get locations for a shipping zone |
| `update_shipping_zone_locations` | Update locations for a shipping zone |

### Taxes

| Method | Description |
|--------|-------------|
| `get_tax_classes` | Retrieve tax classes |
| `create_tax_class` | Create a new tax class |
| `delete_tax_class` | Delete a tax class |
| `get_tax_rates` | Retrieve tax rates |
| `get_tax_rate` | Get a single tax rate |
| `create_tax_rate` | Create a new tax rate |
| `update_tax_rate` | Update a tax rate |
| `delete_tax_rate` | Delete a tax rate |

### Discounts/Coupons

| Method | Description |
|--------|-------------|
| `get_coupons` | Retrieve coupons |
| `get_coupon` | Get a single coupon |
| `create_coupon` | Create a new coupon |
| `update_coupon` | Update a coupon |
| `delete_coupon` | Delete a coupon |

### Payment Gateways

| Method | Description |
|--------|-------------|
| `get_payment_gateways` | Retrieve payment gateways |
| `get_payment_gateway` | Get a single payment gateway |
| `update_payment_gateway` | Update a payment gateway |

### Reports

| Method | Description |
|--------|-------------|
| `get_sales_report` | Retrieve sales reports |
| `get_products_report` | Retrieve products reports |
| `get_orders_report` | Retrieve orders reports |
| `get_categories_report` | Retrieve categories reports |
| `get_customers_report` | Retrieve customers reports |
| `get_stock_report` | Retrieve stock reports |
| `get_coupons_report` | Retrieve coupons reports |
| `get_taxes_report` | Retrieve taxes reports |

### Settings

| Method | Description |
|--------|-------------|
| `get_settings` | Retrieve all settings |
| `get_setting_options` | Retrieve options for a setting |
| `update_setting_option` | Update a setting option |

### System Status

| Method | Description |
|--------|-------------|
| `get_system_status` | Retrieve system status |
| `get_system_status_tools` | Retrieve system status tools |
| `run_system_status_tool` | Run a system status tool |

### Data

| Method | Description |
|--------|-------------|
| `get_data` | Retrieve store data |
| `get_continents` | Retrieve continents data |
| `get_countries` | Retrieve countries data |
| `get_currencies` | Retrieve currencies data |
| `get_current_currency` | Get the current currency |

## Method Parameters

All methods follow a similar parameter structure. Here are some examples:

### Common Parameters for All Methods

- `siteUrl`: (optional if set in env) WordPress site URL

### Additional Parameters for WooCommerce Methods

- `consumerKey`: (optional if set in env) WooCommerce consumer key
- `consumerSecret`: (optional if set in env) WooCommerce consumer secret

### Additional Parameters for WordPress Methods

- `username`: (optional if set in env) WordPress username
- `password`: (optional if set in env) WordPress password

## Example Usage

### WordPress API Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "create_post",
  "params": {
    "siteUrl": "https://your-wordpress-site.com",
    "username": "your-wordpress-username",
    "password": "your-wordpress-password",
    "title": "My New Blog Post",
    "content": "This is the content of my new blog post.",
    "status": "publish"
  }
}
```

### WooCommerce Products Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "get_products",
  "params": {
    "perPage": 20,
    "page": 1,
    "filters": {
      "category": 19,
      "status": "publish"
    }
  }
}
```

### Create Product Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "create_product",
  "params": {
    "productData": {
      "name": "Premium T-Shirt",
      "type": "simple",
      "regular_price": "29.99",
      "description": "Comfortable cotton t-shirt, available in various sizes.",
      "short_description": "Premium quality t-shirt.",
      "categories": [
        {
          "id": 19
        }
      ],
      "images": [
        {
          "src": "http://example.com/wp-content/uploads/2022/06/t-shirt.jpg"
        }
      ]
    }
  }
}
```

### Product Metadata Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "create_product_meta",
  "params": {
    "productId": 456,
    "metaKey": "_custom_product_field",
    "metaValue": {
      "special_attribute": "value",
      "another_attribute": 42
    }
  }
}
```

### Order Metadata Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "create_order_meta",
  "params": {
    "orderId": 789,
    "metaKey": "_delivery_instructions",
    "metaValue": "Leave package at the back door"
  }
}
```

## Security Note

For WooCommerce REST API access, you need to generate API keys. You can create them in your WordPress dashboard under WooCommerce → Settings → Advanced → REST API.

## Requirements

- Node.js 20.0.0 or higher
- WordPress site with WooCommerce plugin installed
- WooCommerce REST API keys

## License

MIT License - See LICENSE file for details
