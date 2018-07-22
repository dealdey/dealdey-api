# DEALDEY THIRD-PARTY API DOCUMENTATION

## Authentication
All API requests are authenticated by an access key. Thus access token will be assigned to you.

### HTTP Request

`GET /deals`

### Query Params

params | type |required | description
--------- | ------- | ------- | -------
acess_key | string | true | Client access key for authenticating all API requests

### Sample Response for Failed Authentication

> 401 Unauthorized
```json
{
  "success": false,
  "message": "Invalid Access Key",
  "code": 101
}
```

## Deal Listings

### HTTP Request

`GET /deals`

### Query Parameters

param | type | default | required | description
----- | ---- | ------- | -------- | ------
acess_key | string | - | true | Client access key for authenticating all API requests
page | integer | 1 | false | The page number
per_page | integer | 10 | false | Maximum number of deals per page
state_id | integer | 8 | false | ID of the state where the deal is available


### Sample Response

> 200 OK

```json
{
  "total_entries": 2549,
  "current_page": 1,
  "per_page": 10,
  "total_pages": 255,
  "deals": [
    {
      "id": 142454,
      "short_title": "Microsoft Office Project Courses",
      "display_sold_out?": false,
      "hover_location": "Lagos Mainland, Lagos",
      "is_new_deal?": false,
      "presale?": false,
      "title": "Microsoft Office Project Courses",
      "keywords": null,
      "end_date": "2018-12-31",
      "permalink": "microsoft-office-project-courses-4",
      "adult_content": false,
      "is_added_to_wishlist": false,
      "average_rating": 5,
      "image": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/listing_images/142454/S234x146/project.jpg?1462964664",
      "mobile_banner_image": null,
      "web_banner_image": null,
      "least_priced_variant": {
        "id": 376385,
        "discounted_price": 11999,
        "list_price": 30000,
        "variants_have_same_price": 0
      },
      "merchant": {
        "merchant_id": 6994,
        "merchant_name": "SGL Technologies"
      }
    }
  ],
  "cart_items_count": 1,
  "success": true
}
```

params | type | description
------ | ---- | -----------
success | boolean | Status of the response
cart_items_count | integer | Number of items in the current cart
deals | array[deal] | List of deals
deals.id | string | ID of the deal
deals.short_title | string | Short title of the deal
deals.display_sold_out? | boolean | Indicates if the sold out or not
deals.hover_location | string | Location where the deal is available
deals.is_new_deal? | boolean | Indicates id the deal is a new deal (true) or not (false)
deals.presale? | boolean | Indicates id the deal is a presale deal (true) or not (false)
deals.title | string | Title of the deal
deals.end_date | date | Date the deal ends
deals.permalink | string | Permalink of the deal
deals.adult_content | boolean | Indicates the deal is for people from 18years upward.
deals.average_rating | integer | Average rating of the deal
deals.least_priced_variant | object | The option with the least price
deals.least_priced_variant.id | integer | ID of the option
deals.least_priced_variant.discounted_price | decimal | Image URL of the deal
deals.least_priced_variant.list_price | decimal | Image URL of the deal
deals.least_priced_variant.variants_have_same_price | integer | Image URL of the deal
deals.merchant | object | Deal seller
deals.merchant.merchant_id | integer | ID of the seller
deals.merchant.merchant_name | string | Seller's name

## Deal Listings per Category

Returns a list of deals per category.

### HTTP Request

`GET /categories/<category_id>/deals`

### URL Parameters

param | type | description
----- | ---- | -----------
category_id | integer | ID of the categoy

### Query Parameters

param | type | default | required | description
----- | ---- | ------- | -------- | ------
acess_key | string | - | true | Client access key for authenticating all API requests
page | integer | 1 | false | The page number
per_page | integer | 10 | false | Maximum number of deals per page
state_id | integer | 8 | false | ID of the state where the deal is available. Default is Lagos

### Sample Response

> 200 OK

```json
{
  "total_entries": 876,
  "current_page": 1,
  "per_page": 10,
  "total_pages": 88,
  "deals": [
    {
      "id": 142759,
      "short_title": "Baby's Knee Pad | 2pcs",
      "display_sold_out?": false,
      "hover_location": "Nationwide Delivery",
      "is_new_deal?": false,
      "presale?": false,
      "title": "Baby's Knee Pad | 2pcs Baby's Knee Pad | 2pcs Baby's Knee Pad | 2pcs Baby's Knee Pad | 2pcs Baby's Knee Pad | 2pcs Baby's Knee Pad | 2pcs Baby's Knee Pad | 2pcs",
      "keywords": "",
      "end_date": "2018-12-31",
      "permalink": "babys-knee-pad-2pcs-5",
      "adult_content": false,
      "is_added_to_wishlist": false,
      "average_rating": 0,
      "image": "/assets/default/deals/listing_images/S234x146/no-image-deal.png",
      "mobile_banner_image": null,
      "web_banner_image": null,
      "least_priced_variant": {
          "id": 376872,
          "discounted_price": 1099,
          "list_price": 2500,
          "variants_have_same_price": 1
      },
      "merchant": {
          "merchant_id": 5160,
          "merchant_name": "Queenjee Graphics Ventures"
      }
    }
  ],
  "cart_items_count": 2,
  "success": true
}
```

## Deal Details

### Request

`GET /deals/<deal_id>`

### URL Parameter

param | type | description
----- | ---- | -----------
deal_id | integer | ID of the deal

### Query Parameters

param | type | default | required | description
----- | ---- | ------- | -------- | ------
acess_key | string | - | true | Client access key for authenticating all API requests

### Sample Response

#### Deal with multiple options

> 200 OK

```json
{
  "deal": {
    "id": 142454,
    "short_title": "Microsoft Office Project Courses",
    "permalink": "microsoft-office-project-courses-4",
    "is_product_deal": false,
    "shippable": false,
    "address_line1": "10, Akinremi Street, Anifowoshe, Off Awolowo Way, Ikeja, Lagos",
    "address_line2": "",
    "discounted_price": 11999,
    "variants_have_same_price": false,
    "list_price": 30000,
    "percent_discount": "60",
    "shipping_charge_message": "Fedex does not ship to your address: 8 Bode Thomas, Surulere, Ikeja, Lagos",
    "saving": 18001,
    "display_sold_quantity": true,
    "bought_count": 2,
    "display_remaining_quantity": false,
    "remaining_quantity": 398,
    "display_sold_percentage": false,
    "percent_sold": 0,
    "show_timer": false,
    "time_left": 14910415,
    "offline_deal": false,
    "available": true,
    "cancelled": false,
    "variants_enabled": true,
    "master_variant_id": 376385,
    "average_rating": 5,
    "can_add_feedback": false,
    "sold_out": false,
    "cod_available": false,
    "highlights": "<p>Sold by <b>Sgl technologies</b></p><p><strong>Microsoft Office Project &nbsp;Level I &amp; II</strong></p>\r\n",
    "main_image": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/images/142454/main_mobile/project.jpg?1462964662",
    "variant_images": [],
    "additional_images": [
      "https://s3.amazonaws.com/rails3.dealdey.com/system/photos/files/181185/main_mobile/open-uri20160505-10727-1mqzpum"
    ],
    "carry_go": false,
    "has_feedbacks": true,
    "is_added_to_wishlist": false,
    "store_ribbon": null,
    "longitude": "3.3842473",
    "latitude": "6.5083701",
    "business_name": "SGL Technologies",
    "phone": "07032830556, 08033064827",
    "website": "",
    "merchant": {
      "merchant_id": 6994,
      "total_feedbacks": 1,
      "merchant_name": "SGL Technologies",
      "merchant_rating": 90.9,
      "merchant_rating_description": "Excellent",
      "followers_count": 5,
      "is_following": false
    }
  },
  "success": true,
  "error_message": null
}
```

params | type | description
------ | ---- | -----------
success | boolean | Status of the response
deal.id | integer | The deal's unique ID
deal.short_title | string | Short title of the deal
deal.permalink | string | Permalink of the deal
deal.is_product_deal | boolean | Indicates if the item is a product (true) or service (false) deal
deal.shippable | boolean | Indicates if the item is shippable or not
deal.address_line1 | string | Line 1 of the deal address
deal.address_line2 | string | Line 2 of the deal address
deal.discounted_price | decimal | The deal's discounted price
deal.variants_have_same_price | boolean | Indicates if the deal has multiple options (false) or not (true)
deal.list_price | decimal | The deal's original price
deal.percent_discount | integer | The deal's percentage discount
deal.saving | decimal | The amount being saved. This is the difference between the list price and the discounted proce
deal.display_sold_quantity | boolean | Indicates if sold quantity should be displayed (true) or not (false)
deal.bought_count | integer | The total sold quantity
deal.display_remaining_quantity | boolean | Indicates if remaining quantity should be displayed (true) or not (false)
deal.remaining_quantity | integer | The total quantity left
deal.display_sold_percentage | boolean | Indicates if percentage of deal sold should be displayed (true) or not (false)
deal.percent_sold | integer | The percentage of deal sold
deal.show_timer | boolean | Indicates if deal timer should be displayed (true) or not (false)
deal.time_left | integer | The time left, in seconds, for which the deal would be live and available.
deal.available | boolean | Indicates if the deal is available (true) or not (false). Only available deals can be purchased
deal.cancelled | boolean | Indicates if the deal is cancelled (true) or not (false). Cancelled deals cannot be purchased
deal.variants_enabled | boolean | Indicates if any of the different options for the deal is enabled. Only enabled variants can be bought.<br>Note that it will always be `false` for a deal without multiple options, i.e a deal with `variants_have_same_price = true`
deal.master_variant_id | integer | The deal's master variant's unique ID
deal.average_rating | integer | Average rating of the deal
deal.can_add_feedback | boolean | Indicates if the user can give feedback for the deal (true) or not (false)
deal.sold_out | boolean | Indicates if the deal is sold out (true) or not (false)
deal.highlights | string | The deal highlight
deal.main_image | string | The deal's main image
deal.additional_images | array[string] | The deal's additional images
deal.has_feedbacks | boolean | Indicates if the deal has feedback (true) or not (false)
deal.longitude | float | Longitude of the deal location
deal.latitude | float | Latitude of the deal location
deal.business_name | string | The seller's name
deal.phone | string | The seller's phone number
deal.website | boolean | The seller's website
deal.merchant.merchant_id | integer | The seller's unique ID
deal.merchant.merchant_name | string | The seller's name
deal.merchant.merchant_rating | boolean | The seller's average rating
deal.merchant.merchant_rating_description | boolean | The description for the seller's average rating

## Variants List

This is for deals that have multiple options. Returns a list of options available for the deal.

### HTTP Request

`GET /deals/<deal_id>/variants`

### URL Parameter

param | type | description
----- | ---- | -----------
deal_id | integer | ID of the deal

### Query Parameters

param | type | default | required | description
----- | ---- | ------- | -------- | ------
acess_key | string | - | true | Client access key for authenticating all API requests

### Sample Response

For a deal has multiple options

> Success 200 OK

```json
{
  "deal": {
    "id": 142454,
    "permalink": "microsoft-office-project-courses-4",
    "limit_quantity_from_deal": false,
    "is_product_deal": false,
    "display_sold_quantity": true,
    "display_remaining_quantity": false,
    "display_sold_percentage": false,
    "variants_have_same_price": false
  },
  "success": true,
  "error_message": null,
  "variants": [
    {
      "id": 376386,
      "percent_discount": 60.0033333333333333,
      "saving": 18001,
      "discounted_price": 11999,
      "list_price": 30000,
      "bought_count": 2,
      "remaining_quantity": 198,
      "percent_sold": 1,
      "sold_out": false,
      "options_text": "Option: Option 1",
      "image": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/images/142454/S670x414/project.jpg?1462964662",
      "options": [
        {
          "option_type": "Option",
          "option_value": "Option 1"
        }
      ],
      "image_id": null
    }
  ]
}
```

For deal without multiple options. _You would not have to make this type of request. It's just been added for information purpose._
> Success 200 OK
```json
{
  "deal": {
    "id": 142453,
    "permalink": "microsoft-server-2012-mcsa-course-4",
    "limit_quantity_from_deal": false,
    "is_product_deal": false,
    "display_sold_quantity": false,
    "display_remaining_quantity": false,
    "display_sold_percentage": false,
    "variants_have_same_price": true
  },
  "success": false,
  "error_message": "No variants found",
  "variants": null
}
```

### Response Description

params | type | description
------ | ---- | -----------
success | boolean | Status of the response. `true` if there's no error, `false` otherwise.
error_message | null,string | Error message. `null` if there's no error
deal.id | integer | The deal's unique ID
deal.permalink | string | Permalink of the deal
deal.limit_quantity_from_deal | boolean |
deal.is_product_deal | boolean | Indicates if the item is a product (true) or service (false) deal
deal.display_sold_quantity | boolean | Indicates if sold quantity should be displayed (true) or not (false)
deal.display_remaining_quantity | boolean | Indicates if remaining quantity should be displayed (true) or not (false)
deal.display_sold_percentage | boolean | Indicates if percentage of deal sold should be displayed (true) or not (false)
deal.variants_have_same_price | boolean | Indicates if the deal has multiple options (false) or not (true)
variants | array[variant] | List of deal options
variant.id | integer | The variants' unique ID
variant.percent_discount | float | The variant's percentage discount
variant.saving | float | The amount being saved. This is the difference between the list price and the discounted proce
variant.list_price | float | The variant's original price
variant.bought_count | integer | The total sold quantity
variant.remaining_quantity | integer | The total quantity left
variant.percent_sold | integer | The percentage of variant sold
variant.sold_out | boolean | Indicates if the variant is sold out (true) or not (false)
variant.options_text | string | The descriptive name of the variant
variant.image | string | The variant's image url
variant.options | array[option] | The options for the variant
option.option_type | string | The type of option for the variant, e.g. Color, Size, Weight, Option etc
option.option_value | string | The value of the type of option. For example<br> - Color could have option value of black, red, blue, white etc <br> - Size could have option value of L, XL, 42, 44, 8 etc <br> - Option could have option value of Option 1, Option 2, Option 3

## Create Cart

### HTTP REQUEST

`GET /carts`

### Query Parameters

param | type | default | required | description
----- | ---- | ------- | -------- | ------
acess_key | string | - | true | Client access key for authenticating all API requests

### Sample Response

> 200 OK

```json
{
  "success": true,
  "cart": {
    "id": 64286,
    "cart_sub_total": 0,
    "error_messages": "",
    "includes_shipping_item": false,
    "discounted_amount": 0,
    "cart_items_count": null,
    "shipping_address": null,
    "user": null,
    "cart_items": []
  },
  "deals_removed": [],
  "bestseller_deals": [
    {
      "id": 140414,
      "short_title": "Intensive SAP User Training",
      "display_sold_out?": false,
      "hover_location": "Multiple Locations",
      "is_new_deal?": false,
      "presale?": false,
      "title": "Intensive SAP User Training",
      "keywords": null,
      "end_date": "2018-12-31",
      "permalink": "intensive-sap-user-training-9",
      "adult_content": false,
      "is_added_to_wishlist": false,
      "average_rating": 0,
      "image": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/listing_images/140414/S234x146/SAPP.jpg?1462296522",
      "mobile_banner_image": null,
      "web_banner_image": null,
      "least_priced_variant": {
        "id": 373136,
        "discounted_price": 69999,
        "list_price": 300000,
        "variants_have_same_price": 1
      },
      "merchant": {
        "merchant_id": 3663,
        "merchant_name": "Clarionttech Services"
      }
    }
  ]
}
```

### Response Description

params | type | description
------ | ---- | -----------
success | boolean | Status of the response. `true` if there's no error, `false` otherwise.
cart.id | integer | The cart's unique ID
cart.cart_sub_total | integer | The total value of the items in the cart. `0` for empty cart.
cart.error_messages | null,string | Error messages. `null` if there's no error
cart.includes_shipping_item | integer | Indicates if the cart contains a shippable item (true) or not (false). If `true`, the user would be required to provide a shipping address.
cart.discounted_amount | integer | The discount on the cart gotten from using a promo code.
cart.cart_items_count | null | The number of items in the cart
cart.shipping_address | null | The cart shipping address provided by the user.
cart.user | null | The user assigned to the cart
cart.cart_items | array[cart_item] | List of items in the cart. `[]` for a newly created cart.
deals_removed | array[string] | List of items automtically removed from the cart. An item that is no longer available would be automatically removed from the cart
best_sellers | array[deal] | List of best selling deals


## Add Item to Cart

Adding an item (or deal) to the cart.
> Adding an item already in the cart only increments the quantity by 1

### HTTP Request

`POST carts/<cart_id>/cart_items`

### URL Parameter

param | type | description
----- | ---- | -----------
cart_id | integer | The cart's unique ID

### Query Parameters

param | type | default | required | description
----- | ---- | ------- | -------- | ------
acess_key | string | - | true | Client access key for authenticating all API requests

### Sample Response

```json
{
  "success": true,
  "error_message": null,
  "cart": {
    "id": 270,
    "cart_sub_total": 50,
    "error_messages": "",
    "includes_shipping_item": true,
    "discounted_amount": 0,
    "cart_items_count": 1,
    "shipping_address": null,
    "user": null,
    "cart_items": [
      {
        "id": 22,
        "deal_id": 32,
        "variant_id": 31,
        "end_date": "2018-11-30",
        "quantity": 1,
        "delivery_option": false,
        "unit_price": 50,
        "total_price": 50,
        "image_for_cart": "https://s3.amazonaws.com/dev.dealdey.com/system/deals/images/32/S270x168/vim_pikender.png?1453818890",
        "available_quantity": 61,
        "deal": {
          "id": 32,
          "short_title": "Test Deal Position",
          "permalink": "test-deal-position",
          "is_product_deal": true,
          "pickup_locations": []
        },
        "variant": {
          "option_value_text": ""
        },
        "pickup_location": null,
        "size": null,
        "error_messages": ""
      }
    ]
  },
  "deals_removed": [],
  "bestseller_deals": null
}
```

params | type | description
------ | ---- | -----------
success | boolean | Status of the response. `true` if there's no error, `false` otherwise.
cart.error_messages | null,string | Error message. `null` if there's no error
cart.id | integer | The cart's unique ID
cart.cart_sub_total | integer | The total value of the items in the cart. `0` for empty cart.
cart.error_messages | null,string | Error messages. `null` if there's no error
cart.includes_shipping_item | integer | Indicates if the cart contains a shippable item (true) or not (false). If `true`, the user would be required to provide a shipping address.
cart.discounted_amount | integer | The discount on the cart gotten from using a promo code.
cart.cart_items_count | integer | The number of items in the cart
cart.shipping_address | null | The cart shipping address provided by the user.
cart.user | null | The user assigned to the cart
cart.cart_items | array[cart_item] | A list of items in the cart
cart_item.id | integer | The cart item's unique ID
cart_item.deal_id | integer | The ID of the deal in the cart
cart_item.variant_id | integer | The ID of the variant of the deal in the cart
cart_item.end_date | date | The end date of the deal
cart_item.quantity | integer | The quantity of the cart item
cart_item.delivery_option | boolean |
cart_item.unit_price | float | The price of one cart item
cart_item.total_price | float | The total price of the all the quantity of the cart item
cart_item.image_for_cart | string | The image url of the deal in the cart
cart_item.available_quantity | integer | The available quantity.
cart_item.pickup_location | string | The selected redemption location for the cart item
cart_item.error_messages | integer | The errors associated with the cart item
cart_item.deal.pickup_locations | array[pickup_location] | A list of all possible redemption locations for the deal
cart_item.variant.option_value_text | string | The descriptive name of the variant of the deal in the cart
deals_removed | array[string] | List of items automtically removed from the cart. An item that is no longer available would be automatically removed from the cart
best_sellers | null,array[deal] | List of best selling deals. `null` if there are items in the cart.


## Increase/Decrease Cart Item Quantity

### HTTP Request

`POST /cart_items/<cart_item_id>/change_quantity`

### URL Parameter

param | type | description
----- | ---- | -----------
cart_id | integer | The cart's unique ID

### Query Parameter

param | type | default | required | description
----- | ---- | ------- | -------- | ------
acess_key | string | - | true | Client access key for authenticating all API requests

### Body Parameter

param | type | default | required | description
----- | ---- | ------- | -------- | ------
quantity | integer | - | true | The new quantity of the cart item. It must be greater then 0 and not greater then the maximum available quantity

### Sample Responses

For `quantity = 5` and `cart_id = 4442076`, The quantity will be updated to 5. Check `cart_item.quantity`.

``` json
{
  "success": true,
  "cart": {
    "id": 63643,
    "cart_sub_total": 25949,
    "error_messages": "",
    "includes_shipping_item": true,
    "discounted_amount": 0,
    "cart_items_count": 2,
    "shipping_address": null,
    "user": null,
    "cart_items": [
      {
        "id": 4442075,
        "deal_id": 142770,
        "variant_id": 376896,
        "end_date": "2018-12-31",
        "quantity": 5,
        "delivery_option": false,
        "unit_price": 2790,
        "total_price": 13950,
        "image_for_cart": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/images/142770/S270x168/test_image_main.jpg?1464965132",
        "available_quantity": 183,
        "deal": {
          "id": 142770,
          "short_title": "Test - Stainless Quartz Men's Wristwatch",
          "permalink": "test-stainless-quartz-mens-wristwatch",
          "is_product_deal": true,
          "pickup_locations": []
        },
        "variant": {
          "option_value_text": ""
        },
        "pickup_location": null,
        "size": null,
        "error_messages": ""
      },
      {
        "id": 4442076,
        "deal_id": 142454,
        "variant_id": 376386,
        "end_date": "2018-12-31",
        "quantity": 1,
        "delivery_option": false,
        "unit_price": 11999,
        "total_price": 11999,
        "image_for_cart": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/images/142454/S264x139/project.jpg?1462964662",
        "available_quantity": 198,
        "deal": {
          "id": 142454,
          "short_title": "Microsoft Office Project Courses",
          "permalink": "microsoft-office-project-courses-4",
          "is_product_deal": false,
          "pickup_locations": []
        },
        "variant": {
          "option_value_text": "Option: Option 1"
        },
        "pickup_location": null,
        "size": null,
        "error_messages": ""
      }
    ]
  },
  "deals_removed": [],
  "bestseller_deals": null
}
```

When new quantity is more than the available quantity.
See error at `cart_item.error_messages`

```json
{
  "success": false,
  "cart": {
    "id": 63643,
    "cart_sub_total": 20369,
    "error_messages": "",
    "includes_shipping_item": true,
    "discounted_amount": 0,
    "cart_items_count": 2,
    "shipping_address":null,
    "user": null,
    "cart_items": [
      {
        "id": 4442075,
        "deal_id": 142770,
        "variant_id": 376896,
        "end_date": "2018-12-31",
        "quantity": 3,
        "delivery_option": false,
        "unit_price": 2790,
        "total_price": 8370,
        "image_for_cart": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/images/142770/S270x168/test_image_main.jpg?1464965132",
        "available_quantity": 183,
        "deal": {
          "id": 142770,
          "short_title": "Test - Stainless Quartz Men's Wristwatch",
          "permalink": "test-stainless-quartz-mens-wristwatch",
          "is_product_deal": true,
          "pickup_locations": []
        },
        "variant": {
          "option_value_text": ""
        },
        "pickup_location": null,
        "size": null,
        "error_messages": "Quantity for Test - Stainless Quartz Men's Wristwatch should not exceed 183."
      },
      {
        "id": 4442076,
        "deal_id": 142454,
        "variant_id": 376386,
        "end_date": "2018-12-31",
        "quantity": 1,
        "delivery_option": false,
        "unit_price": 11999,
        "total_price": 11999,
        "image_for_cart": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/images/142454/S264x139/project.jpg?1462964662",
        "available_quantity": 198,
        "deal": {
          "id": 142454,
          "short_title": "Microsoft Office Project Courses",
          "permalink": "microsoft-office-project-courses-4",
          "is_product_deal": false,
          "pickup_locations": []
        },
        "variant": {
          "option_value_text": "Option: Option 1"
        },
        "pickup_location": null,
        "size": null,
        "error_messages": ""
      }
    ]
  },
  "deals_removed": [],
  "bestseller_deals": null
}
```

When cart item is not in the cart.
See error at `cart.error_messages`

> 404 Not Found

```json
{
  "success": false,
  "cart": {
    "id": 63643,
    "cart_sub_total": 14789,
    "error_messages": "Cart Item not found",
    "includes_shipping_item": true,
    "discounted_amount": 0,
    "cart_items_count": 2,
    "shipping_address": null,
    "user": null,
    "cart_items": [<cart_items>]
  },
  "deals_removed": [],
  "bestseller_deals": null
}
```


## Remove Item from Cart

### HTTP Request

`POST /cart_items/<cart_item_id>/remove`

### URL Params

param | type | description
----- | ---- | -----------
cart_id | integer | The cart's unique ID

### Query Params

param | type | default | required | description
----- | ---- | ------- | -------- | ------
acess_key | string | - | true | Client access key for authenticating all API requests

The response is similar to the same response for Add to Cart but the cart item will no longer be in the list of cart items

### Sample Response

If the item is not in the cart.

> 404 Not Found

```json
{
  "success": false,
  "cart": {
    "id": 63643,
    "cart_sub_total": 11999,
    "error_messages": "Cart Item not found",
    "includes_shipping_item": false,
    "discounted_amount": 0,
    "cart_items_count": 1,
    "shipping_address": null,
    "user": null,
    "cart_items": [<cart_items>]
  },
  "deals_removed": [],
  "bestseller_deals": null
}
```

## Cart Details

### HTTP Request

`GET /carts/<cart_id>`

### URL Params

param | type | description
----- | ---- | -----------
cart_id | integer | The cart's unique ID

### Query Params

param | type | default | required | description
----- | ---- | ------- | -------- | ------
acess_key | string | - | true | Client access key for authenticating all API requests

### Sample Response

> 200 OK

```json
{
  "success": true,
  "cart": {
    "id": 63643,
    "cart_sub_total": 14789,
    "error_messages": "",
    "includes_shipping_item": true,
    "discounted_amount": 0,
    "cart_items_count": 2,
    "shipping_address": null,
    "user": null,
    "cart_items": [<cart_items>]
  },
  "deals_removed": [],
  "bestseller_deals": null
}
```


## Change Pickup Location

For service deals with multiple redemption locations, you will be required to pick one pickup location.

Before choosing a pickup location, the `cart_item.pickup_location` is `null`

### HTTP REQUEST

Use this request to choose a pickup location for the cart item

`POST /carts/<cart_id>/cart_items/<cart_item_id>/change_pickup_location`

### URL Params

param | type | description
----- | ---- | -----------
cart_id | integer | The cart's unique ID
cart_item_id | integer | The cart item's unique ID

### Query Param

param | type | default | required | description
----- | ---- | ------- | -------- | ------
acess_key | string | - | true | Client access key for authenticating all API requests

### Body Param

param | type | reqiured | description
----- | ---- | -------- | -----------
pickup_location_id | integer | true | The pickup location's unique ID

### Sample Responses

> 200 OK

```json
{
  "success": true,
  "cart": {
    "id": 64286,
    "cart_sub_total": 8500,
    "error_messages": "",
    "includes_shipping_item": false,
    "discounted_amount": 0,
    "cart_items_count": 1,
    "shipping_address": null,
    "user": null,
    "cart_items": [
      {
        "id": 4442092,
        "deal_id": 81839,
        "variant_id": 271803,
        "end_date": "2018-12-31",
        "quantity": 1,
        "delivery_option": false,
        "unit_price": 8500,
        "total_price": 8500,
        "image_for_cart": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/images/81839/S270x168/1553643_1.jpg?1444124345",
        "available_quantity": 20,
        "deal": {
          "id": 81839,
          "short_title": "David Wej Reversible D Buckle Belt",
          "permalink": "david-wej-reversible-d-buckle-belt",
          "is_product_deal": true,
          "pickup_locations": [
            {
              "id": 55819,
              "address": "27b, Idowu Martins Street, Off Adeola Odeku Street, Victoria Island, , Agbado/Oke-Odo, Lagos"
            },
            {
              "id": 55820,
              "address": "44, Opebi Road, Ikeja, Lagos"
            },
            {
              "id": 55821,
              "address": "25, Adeniran Ogunsanya Street, Surulere, Lagos."
            },
            {
              "id": 55822,
              "address": "142, Bode Thomas Street, Surulere, Lagos."
            }
          ]
        },
        "variant": {
          "option_value_text": "Colour: Silver"
        },
        "pickup_location": {
          "id": 67243,
          "address": "27b, Idowu Martins Street, Off Adeola Odeku Street, Victoria Island, , Agbado/Oke-Odo, Lagos"
        },
        "size": null,
        "error_messages": ""
      }
    ]
  },
  "deals_removed": [],
  "bestseller_deals": null
}
```

### Response Description

params | type | description
------ | ---- | -----------
cart_item.pickup_location.id | integer | The assigned pickup location's unique ID
cart_item.pickup_location.address | string | The address of the assigned pickup location
cart_item.deal.pickup_locations | array[pickup_location] | A list of all possible redemption locations for the deal
pickup_location.id | integer | The pickup location's unique ID
pickup_location.address | string | The address of the pickup location

If pickup location is not found, `cart.error_messages` will be `Pickup Location not found`

```json
{
  "success": true,
  "cart": {
    "id": 64286,
    "cart_sub_total": 8500,
    "error_messages": "Pickup Location not found",
    "includes_shipping_item": false,
    "discounted_amount": 0,
    "cart_items_count": 1,
    "shipping_address": null,
    "user": null,
    "cart_items": [
      {
        "id": 4442092,
        "deal_id": 81839,
        "variant_id": 271803,
        "end_date": "2018-12-31",
        "quantity": 1,
        "delivery_option": false,
        "unit_price": 8500,
        "total_price": 8500,
        "image_for_cart": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/images/81839/S270x168/1553643_1.jpg?1444124345",
        "available_quantity": 20,
        "deal": {
          "id": 81839,
          "short_title": "David Wej Reversible D Buckle Belt",
          "permalink": "david-wej-reversible-d-buckle-belt",
          "is_product_deal": true,
          "pickup_locations": [<pickup_locations>]
        },
        "variant": {
          "option_value_text": "Colour: Silver"
        },
        "pickup_location": null,
        "size": null,
        "error_messages": ""
      }
    ]
  },
  "deals_removed": [],
  "bestseller_deals": null
}
```

## Create Shipping Address

A shipping address is required for a cart that contains at least a shippable item.

### HTTP Request

`POST /carts/<cart_id>/shipping_address`

### Body Parameters

param | type | reqiured | description
----- | ---- | -------- | -----------
shipping_address.name | string | true | Name of the shipping address
shipping_address.address_line | string | true | The shipping address
shipping_address.state | string | true | The state where the address is located
shipping_address.area | string | true | The area within the selected state
shipping_address.landmark | string | false | The landmark for the shipping address

### Sample Response

```json
{
  "success": true,
  "errors": {},
  "shipping_address": {
    "id": 588,
    "name": "Oluwasegun",
    "address_line": "19 Taike Street",
    "landmark": "Love All Street",
    "area": "Ikeja",
    "state": "Lagos"
  },
  "cart": null,
  "deals_removed": [],
  "bestseller_deals": null
}
```

The response for request `GET /carts/<cart_id>` for a cart with a shipping address

```json
{
  "success": true,
  "cart": {
    "id": 270,
    "cart_sub_total": 250,
    "error_messages": "",
    "includes_shipping_item": true,
    "discounted_amount": 0,
    "cart_items_count": 1,
    "shipping_address": {
      "address_line": "19 Taike Street",
      "area": "Ikeja",
      "global": false,
      "id": 588,
      "landmark": "Love All Street",
      "name": "Oluwasegun",
      "state": "Lagos"
    },
    "user": null,
    "cart_items": [<cart_items>]
  },
  "deals_removed": [],
  "bestseller_deals": null
}
```

### Response Description

param | type | description
----- | ---- | -----------
shipping_address.id | integer | The shipping address' unique ID
shipping_address.name | string | Name of the shipping address
shipping_address.address_line | string | The shipping address
shipping_address.state | string | The state where the address is located
shipping_address.area | string | The area within the selected state
shipping_address.landmark | string | The landmark for the shipping address

## Create User

User information must be provided at checkout

> For a cart with shipping item, shipping address must be provided before shipping information.

### HTTP Request

`POST /carts/<cart_id>/user`

### Body Parameters

param | type | reqiured | description
----- | ---- | -------- | -----------
user.firstname | string | true | The user's name
user.mobile | string | true | The user's mobile number. Format is 0xxxxxxxxxx
user.email | string | true | The user's email address

### Sample Response

```json
{
  "success": true,
  "user": {
    "id": 346316,
    "firstname": "Anybody",
    "lastname": null,
    "mobile": "07012345678",
    "email": "test69@email.com",
    "updated_at": "2018-07-20T16:26:53.052+01:00",
    "balance": "0.0",
    "fb_id": null,
    "confirmed_at": null,
    "gender": null,
    "salary_bracket": null,
    "age_bracket": null,
    "profession": null
  }
}
```

### Response Description

params | type | description
------ | ---- | -----------
user.id | integer | The user's unique ID
user.firstname | string | The user's first name
user.mobile | integer | The user's mobile number
user.email | integer | The user's email address

The response for request `GET /carts/<cart_id>` for a cart with a user

```json
{
  "success": true,
  "cart": {
    "id": 270,
    "cart_sub_total": 250,
    "error_messages": "",
    "includes_shipping_item": true,
    "discounted_amount": 0,
    "cart_items_count": 1,
    "shipping_address": {
      "address_line": "19 Taike Street",
      "area": "Ikeja",
      "global": false,
      "id": 588,
      "landmark": "Love All Street",
      "name": "Oluwasegun",
      "state": "Lagos"
    },
    "user": {
      "email": "test69@email.com",
      "mobile": "07032630555",
      "mobile_verified": false
    },
    "cart_items": [<cart_items>]
  },
  "deals_removed": [],
  "bestseller_deals": null
}
```

## Cart Payment Summary

Returns a summary of the cart including the total value of the item, shipping charges and total amount to be paid.

### HTTP Request

`GET /carts/<cart_id>/payment_options`

### URL Params

param | type | description
----- | ---- | -----------
cart_id | integer | The cart's unique ID

### Sample Response

```json
{
  "success": true,
  "sub_total": 41984,
  "shipping_charges": 20850,
  "total_amount": 62834,
  "is_shippable": true,
  "cart": {
    "id": 50,
    "cart_sub_total": 41984,
    "error_messages": "",
    "includes_shipping_item": true,
    "discounted_amount": 0,
    "cart_items_count": 3,
    "shipping_address": null,
    "user": null,
    "cart_items": [<cart_items>]
  },
  "deals_removed": [],
  "bestseller_deals": null
}
```

### Response Description

param | type | description
----- | ---- | -----------
success | boolean |
sub_total | float | The total value of the items in the cart
shipping_charges | float | The total shipping charges for the shippable items in the cart
total_amount | float | The total amount expected to be paid. It is the sum of `sub_total` and `shipping_charges`.
is_shippable | boolean | Indicates if there's at least a shippable item in the cart. If `true`, the user is expected to provide a shipping address
