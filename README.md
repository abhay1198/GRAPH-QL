# GRAPH-QL

# 1. Generate Customer Token

```
mutation {
  generateCustomerToken(email: "test@gmail.com", password: "test@123") {
    token
  }
}
```

# 2. Customer Cart Id

```
{
  customerCart{
    id
  }
}
```

# 3. Add Product to cart

```
mutation {
  addSimpleProductsToCart(
    input: {
      cart_id: "81vaAZqiuNMJACEtcnulGXsFCzENS7ws"
      cart_items: [
        {
          data: {
            quantity: 1
            sku: "test-product-sku"
          }
        }
      ]
    }
  ) {
    cart {
      items {
        id
        product {
          sku
          stock_status
        }
        quantity
      }
    }
  }
}
```

# 4. Add Shipping Address 

```
mutation {
  setShippingAddressesOnCart(
    input: {
      cart_id: "81vaAZqiuNMJACEtcnulGXsFCzENS7ws"
      shipping_addresses: [
        {
          address: {
            firstname: "Customer First Name"
            lastname: "Customer Last Name"
            company: "XYZ"
            street: ["3320 N Crescent Dr", "Beverly Hills"]
            city: "Los Angeles"
            region: "CA"
            region_id: 12
            postcode: "000000"
            country_code: "US"
            telephone: "7878787878"
            save_in_address_book: false

          }          
        }
      ]
    }
  ) {
    cart {
      shipping_addresses {
        firstname
        lastname
        company
        street
        city
        region {
          code
          label
        }
        postcode
        telephone
        country {
          code
          label
        }        
      }
    }
  }
}
```

# 5. Add Billing Address

```
mutation {
  setBillingAddressOnCart(
    input: {
      cart_id: "81vaAZqiuNMJACEtcnulGXsFCzENS7ws"
      billing_address: {
        address: {
          firstname: "Customer First Name"
          lastname: "Customer Last Name"
          company: "XYZ"
          street: ["3320 N Crescent Dr", "Beverly Hills"]
          city: "Los Angeles"
          region: "CA"
          region_id: 12
          postcode: "000000"
          country_code: "US"
          telephone: "7878787878"
          save_in_address_book: true
        }
      }
    }
  ) {
    cart {
      billing_address {
        firstname
        lastname
        company
        street
        city
        region{
          code
          label
        }
        postcode
        telephone
        country {
          code
          label
        }
      }
    }
  }
}
```

# 6. Set Payment Method

```
mutation {
  setPaymentMethodOnCart(input: {
      cart_id: "81vaAZqiuNMJACEtcnulGXsFCzENS7ws"
      payment_method: {
          code: "checkmo"
      }
  }) {
    cart {
      selected_payment_method {
        code
      }
    }
  }
}
```

# 7. Place an order

```
mutation {
  placeOrder(input: {cart_id: "81vaAZqiuNMJACEtcnulGXsFCzENS7ws"}) {
    order {
      order_number
    }
  }
}
```
