{
  "$schema": "[json-schema.org](http://json-schema.org/draft-07/schema#)",
  "title": "Mountain Dew Product Catalog",
  "description": "Schema for Mountain Dew products, including details for flavor profiles and retail availability.",
  "type": "array",
  "items": {
    "type": "object",
    "required": [
      "productId",
      "name",
      "type",
      "flavorProfile",
      "description",
      "imageURL"
    ],
    "properties": {
      "productId": {
        "type": "string",
        "description": "Unique identifier for the product."
      },
      "name": {
        "type": "string",
        "description": "Marketing name of the product (e.g., 'Baja Blast', 'Dirty Soda Syrup')."
      },
      "type": {
        "type": "string",
        "enum": ["beverage", "syrup-component", "additive-component"],
        "description": "Category of the product, indicating if it's a standalone beverage or a component for Dirty Soda."
      },
      "flavorProfile": {
        "type": "array",
        "description": "Key flavor characteristics of the product.",
        "items": {
          "type": "string",
          "enum": ["citrus", "tropical", "berry", "cream", "vanilla", "coconut", "chocolate", "fruit", "energizing", "original"]
        },
        "minItems": 1
      },
      "description": {
        "type": "string",
        "description": "Brief marketing description of the product."
      },
      "imageURL": {
        "type": "string",
        "format": "uri",
        "description": "URL to the primary image of the product."
      },
      "campaigns": {
        "type": "array",
        "description": "Relevant marketing campaigns associated with this product.",
        "items": {
          "type": "string"
        }
      },
      "packaging": {
        "type": "array",
        "description": "Available packaging types (e.g., can, bottle, 12-pack).",
        "items": {
          "type": "string"
        }
      },
      "nutritionalInfo": {
        "type": "object",
        "description": "Summary of key nutritional facts.",
        "properties": {
          "calories": { "type": "integer" },
          "sugar": { "type": "number" },
          "caffeine": { "type": "number" }
        }
      },
      "retailAvailability": {
        "type": "array",
        "description": "Information about where the product can be purchased, especially for 'Dirty Mountain Dew'.",
        "items": {
          "type": "object",
          "required": ["retailerName", "storeType"],
          "properties": {
            "retailerName": { "type": "string" },
            "storeType": { "type": "string", "enum": ["DashMart", "supermarket", "convenience-store", "restaurant"] },
            "geoCoordinates": {
              "type": "object",
              "properties": {
                "latitude": { "type": "number" },
                "longitude": { "type": "number" }
              }
            },
            "stockStatus": { "type": "string", "enum": ["in-stock", "low-stock", "out-of-stock"] }
          }
        }
      },
      "socialShareTextTemplate": {
        "type": "string",
        "description": "Template for social media sharing text, e.g., 'My custom Dirty Dew is {DewCode}!'"
      }
    }
  }
}
