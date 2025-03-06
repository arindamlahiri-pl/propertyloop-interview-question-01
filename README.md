# Multi-API Data Aggregation Challenge

## Problem Statement
You are building a dashboard for an e-commerce analytics platform. The dashboard needs to display consolidated product performance data that comes from multiple API endpoints. Your task is to create a function that fetches data from these endpoints, combines the information, and transforms it into a standardized format for the frontend to consume.

## Requirements
1. Fetch data from three different API endpoints (details below)
2. Handle API request errors appropriately
3. Combine and transform the data into a unified format
5. Create a search/filter function to query the aggregated data
6. Implement caching to prevent redundant API calls (optional)

## API Endpoints

```typescript
// You can simulate these endpoints with these placeholder functions
function fetchProductDetails() {
  return Promise.resolve([
    { id: "P1", name: "Wireless Headphones", category: "Electronics", price: 89.99 },
    { id: "P2", name: "Running Shoes", category: "Footwear", price: 129.95 },
    { id: "P3", name: "Coffee Maker", category: "Kitchen", price: 149.99 },
    { id: "P4", name: "Yoga Mat", category: "Fitness", price: 45.50 }
  ]);
}

function fetchProductInventory() {
  return Promise.resolve([
    { productId: "P1", warehouseStock: 230, storeStock: 34, reserved: 12, status: "in_stock" },
    { productId: "P2", warehouseStock: 120, storeStock: 22, reserved: 5, status: "low_stock" },
    { productId: "P3", warehouseStock: 0, storeStock: 0, reserved: 0, status: "out_of_stock" },
    { productId: "P4", warehouseStock: 67, storeStock: 15, reserved: 2, status: "in_stock" }
  ]);
}

function fetchProductAnalytics() {
  return Promise.resolve([
    { product_id: "P1", views: 1204, conversion_rate: 0.12, revenue_mtd: 5620.32 },
    { product_id: "P2", views: 876, conversion_rate: 0.08, revenue_mtd: 2154.99 },
    { product_id: "P4", views: 315, conversion_rate: 0.04, revenue_mtd: 982.45 }
    // Note: P3 data is missing from this endpoint
  ]);
}
```

## Output Format
Your function should transform the data into the following format:

```typescript
[
  {
    "productId": "P1",
    "name": "Wireless Headphones",
    "category": "Electronics",
    "price": 89.99,
    "inventory": {
      "total": 264,  // warehouseStock + storeStock
      "available": 252,  // total - reserved
      "status": "in_stock"
    },
    "performance": {
      "views": 1204,
      "conversionRate": 0.12,
      "revenue": 5620.32
    }
  },
  // similar objects for other products
]
```

## Implementation Requirements
1. Create a function `aggregateProductData()` that fetches and combines the data from all three endpoints.
2. Implement error handling for API requests.
3. Handle missing data (like P3 missing from analytics) gracefully.
4. Create a `searchProducts(aggregatedData, searchTerm, filters)` function that can:
   - Search by product name (case-insensitive partial match)
   - Filter by category, inventory status, or price range
5. Implement a simple cache mechanism to avoid redundant API calls. (optional)

## Additional information
1. You will have a total of 25 minutes for this question.
2. Code your solution in the Typescript sandbox [here](https://codesandbox.io/p/devbox/typescript-playground-export-forked-6z8mmw?workspaceId=ws_Qd8Yq13nXDQ8o28PXL3wys)
   - Sign in using Github and fork this sandbox

## Evaluation Criteria
1. Proper handling of asynchronous operations
2. Error handling and edge cases (missing data)
3. Code organization and clarity
4. Maintainable code
5. Efficiency of the data transformation
6. Correct implementation of search/filter functionality
7. Implementation of caching mechanism


