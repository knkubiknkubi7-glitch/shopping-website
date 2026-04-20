# Seller Features

This marketplace supports seller functionality allowing users to register as sellers and manage their products.

## Seller Registration

- Users can register as sellers via `/seller/register`
- Sellers have access to dedicated dashboard and management tools
- Regular users can upgrade to seller accounts

## Seller Dashboard (`/seller/dashboard`)

Comprehensive overview including:
- **Total Revenue**: All-time earnings from sales
- **Total Orders**: Number of orders containing seller products
- **Total Products**: Count of listed products
- **Items Sold**: Total quantity of items sold
- **Recent Orders**: Last 10 orders
- **Top Selling Products**: Top 5 products by sales

## Product Management (`/seller/products`)

### Create Products (`/seller/products/new`)
- Add product name, description, price, stock
- Upload up to 5 product images (URLs)
- Select category and brand
- Set specifications (color, size, weight)
- Configure shipping (free shipping, estimated days)

### Manage Products
- View all seller products in table format
- Edit product details
- Delete products
- Toggle product active/inactive status
- Monitor stock levels

## Sales Reports (`/seller/reports`)

### Date Range Filtering
- Filter sales by custom date ranges
- Default view: Last 30 days

### Report Metrics
- **Summary Cards**: Total revenue, orders, items sold, avg order value
- **Sales Timeline**: Visual chart showing daily revenue trends
- **Category Sales**: Breakdown of sales by product category
- **Top Products**: Best performing products (top 20)

### Data Visualization
- Simple bar chart for sales timeline
- Sortable tables for categories and products
- Revenue and quantity metrics

## API Endpoints

### Dashboard
```
GET /api/seller/dashboard
```
Returns stats, recent orders, and top products

### Products
```
GET    /api/seller/products?page=1&limit=20
POST   /api/seller/products
PUT    /api/seller/products/:id
DELETE /api/seller/products/:id
```

### Sales Report
```
GET /api/seller/sales-report?startDate=YYYY-MM-DD&endDate=YYYY-MM-DD
```

### Orders
```
GET /api/seller/orders?page=1&limit=20
```
Returns orders containing seller's products

## Security

- All seller routes require authentication
- JWT token verification via middleware
- Role-based access control (seller or admin only)
- Product ownership verification for edit/delete operations

## User Interface

### Navigation
- Seller menu appears in user dropdown (navbar)
- Links to Dashboard, Products, and Reports
- "Become a Seller" link in footer

### Responsive Design
- Mobile-friendly layouts
- Collapsible tables and grids
- Touch-optimized buttons

## Backend Models

### User Model
```javascript
role: {
  type: String,
  enum: ['user', 'seller', 'admin'],
  default: 'user'
}
```

### Product Model
```javascript
seller: {
  type: mongoose.Schema.Types.ObjectId,
  ref: 'User'
}
```

Products are linked to sellers for tracking and management.

## Getting Started as Seller

1. **Register**: Visit `/seller/register` and create seller account
2. **Login**: Use credentials to login
3. **Add Products**: Navigate to Dashboard → Add New Product
4. **Manage**: Monitor sales in Dashboard and view detailed reports
5. **Track Orders**: View all orders containing your products

## Features Summary

✅ Seller Registration with role-based access
✅ Product Upload with images and specifications  
✅ Product Management (CRUD operations)
✅ Sales Dashboard with key metrics
✅ Detailed Sales Reports with filtering
✅ Order Management view
✅ Revenue tracking and analytics
✅ Category-wise sales breakdown
✅ Top products analytics
✅ Stock management
✅ Product status toggle (active/inactive)

## Future Enhancements

- Product analytics (views, clicks, conversion)
- Bulk product upload (CSV)
- Product variations (size, color options)
- Seller ratings and reviews
- Commission/fee management
- Payout tracking
- Inventory alerts
- Promotional tools
- Seller messaging system
