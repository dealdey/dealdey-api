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
deals.display_sold_out? | booleanboolean |
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
deals.merchant.id | integer | ID of the seller
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

- deal_id

### Query Parameters

param | type | default | required | description
----- | ---- | ------- | -------- | ------
acess_key | string | - | true | Client access key for authenticating all API requests

### Sample Response

#### Deal with multiple options

> Success 200 OK

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

#### Deal with no multiple options

> 200 OK

```json
{
  "deal": {
    "id": 142453,
    "short_title": "Microsoft Server 2012 MCSA Course",
    "permalink": "microsoft-server-2012-mcsa-course-4",
    "is_product_deal": false,
    "shippable": false,
    "address_line1": "10, Akinremi Street, Anifowoshe, Off Awolowo Way, Ikeja, Lagos",
    "address_line2": "",
    "discounted_price": 20999,
    "variants_have_same_price": true,
    "list_price": 180000,
    "percent_discount": "88",
    "shipping_charge_message": "Fedex does not ship to your address: 8 Bode Thomas, Surulere, Ikeja, Lagos",
    "saving": 159001,
    "display_sold_quantity": false,
    "bought_count": 0,
    "display_remaining_quantity": false,
    "remaining_quantity": 100,
    "display_sold_percentage": false,
    "percent_sold": 0,
    "show_timer": false,
    "time_left": 14875119,
    "offline_deal": false,
    "available": true,
    "cancelled": false,
    "variants_enabled": false,
    "master_variant_id": 376384,
    "average_rating": 0,
    "can_add_feedback": false,
    "sold_out": false,
    "cod_available": false,
    "highlights": "<p>Sold by <b>Sgl technologies</b></p>",
    "fine_prints": "<li>Terms and conditions apply</li>",
    "description": "deal description",
    "main_image": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/images/142453/main_mobile/mcsa_windowsserver2012.jpg?1462964627",
    "variant_images": [],
    "additional_images": [
        "https://s3.amazonaws.com/rails3.dealdey.com/system/photos/files/181184/main_mobile/open-uri20160509-10727-1rwzibw"
    ],
    "carry_go": false,
    "has_feedbacks": false,
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

## Variants List

This is for deals that have multiple options. Returns a list of options available for the deal.

### HTTP Request

`GET /deals/<deal_id>/variants`

### URL Parameter

- deal_id

### Query Parameters
- access_key
- auth_token

### Sample Response

If deal has multiple options

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
    },
    {
      "id": 376387,
      "percent_discount": 60.0033333333333333,
      "saving": 18001,
      "discounted_price": 11999,
      "list_price": 30000,
      "bought_count": 0,
      "remaining_quantity": 200,
      "percent_sold": 0,
      "sold_out": false,
      "options_text": "Option: Option 2",
      "image": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/images/142454/S670x414/project.jpg?1462964662",
      "options": [
        {
          "option_type": "Option",
          "option_value": "Option 2"
        }
      ],
      "image_id": null
    }
  ]
}
```

If deal has no options. _You would not have to make this type of request. It's just been added for information purpose._
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

## Cart Details

### HTTP REQUEST

`GET /carts`

### Query Parameters

- access_key
- auth_token

### Sample Response

Cart with Items

> Success 200 OK

```json
{
    "success": true,
    "cart": {
        "id": 63643,
        "cart_sub_total": 14789,
        "error_messages": "",
        "includes_shipping_item": true, // true if deal has shippable items, otherwise false>
        "discounted_amount": 0,
        "cart_items_count": 2,
        "shipping_address": {
            "address_line": "8 Bode Thomas, Surulere",
            "area": "Ikeja",
            "global": false,
            "id": 2048006,
            "landmark": "Lagos",
            "name": "Adebayo Akinlaja",
            "state": "Lagos"
        },
        "user": {
            "email": "damilola.ade@dealdey.com",
            "mobile": "08155917030",
            "mobile_verified": true
        },
        "cart_items": [
            {
                "id": 4442075,
                "deal_id": 142770,
                "variant_id": 376896,
                "end_date": "2018-12-31",
                "quantity": 1,
                "delivery_option": false,
                "unit_price": 2790,
                "total_price": 2790,
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

Empty Cart

> Success 200 OK

```json
{
  "success": true,
  "cart": {
    "id": 63746,
    "cart_sub_total": 0,
    "error_messages": "",
    "includes_shipping_item": false,
    "discounted_amount": 0,
    "cart_items_count": null,
    "shipping_address": null,
    "user": {
      "email": "damilola.ade@dealdey.com",
      "mobile": "08155917030",
      "mobile_verified": true
    },
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
    },
    {
        "id": 136742,
        "short_title": "HoT Spa Double Delight Treat",
        "display_sold_out?": false,
        "hover_location": "Ikeja, Lagos",
        "is_new_deal?": false,
        "presale?": false,
        "title": "HoT Spa Double Delight Treat",
        "keywords": null,
        "end_date": "2018-12-31",
        "permalink": "hot-spa-double-delight-treat",
        "adult_content": false,
        "is_added_to_wishlist": false,
        "average_rating": 5,
        "image": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/listing_images/136742/S234x146/House_of_Tay_Image_2.jpg?1461064032",
        "mobile_banner_image": null,
        "web_banner_image": null,
        "least_priced_variant": {
            "id": 367407,
            "discounted_price": 1999,
            "list_price": 10000,
            "variants_have_same_price": 0
        },
        "merchant": {
            "merchant_id": 1378,
            "merchant_name": "House of Tay (Hot Spa)"
        }
    },
    {
        "id": 134504,
        "short_title": "Premium Dental Scaling & Polishing",
        "display_sold_out?": false,
        "hover_location": "Ikosi, Lagos",
        "is_new_deal?": false,
        "presale?": false,
        "title": "Premium Dental Scaling & Polishing",
        "keywords": null,
        "end_date": "2018-12-31",
        "permalink": "premium-dental-scaling-polishing-10",
        "adult_content": false,
        "is_added_to_wishlist": false,
        "average_rating": 0,
        "image": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/listing_images/134504/S234x146/C__281_29.jpg?1460379576",
        "mobile_banner_image": null,
        "web_banner_image": null,
        "least_priced_variant": {
            "id": 363615,
            "discounted_price": 799,
            "list_price": 6000,
            "variants_have_same_price": 1
        },
        "merchant": {
            "merchant_id": 652,
            "merchant_name": "Platinum Dental Surgery Clinic"
        }
    },
    {
        "id": 137812,
        "short_title": "Luxury Spa Day Pampering Package",
        "display_sold_out?": false,
        "hover_location": "Victoria Island, Lagos",
        "is_new_deal?": false,
        "presale?": false,
        "title": "Luxury Spa Day Pampering Package",
        "keywords": "",
        "end_date": "2018-12-31",
        "permalink": "luxury-spa-day-pampering-package",
        "adult_content": false,
        "is_added_to_wishlist": false,
        "average_rating": 4,
        "image": "https://s3.amazonaws.com/rails3.dealdey.com/system/deals/listing_images/137812/S234x146/Indy_Spa.jpg?1461455623",
        "mobile_banner_image": "https://s3.amazonaws.com/rails3.dealdey.com/system/stores/deal_banners/103/S19x35/7.jpg?1489575077",
        "web_banner_image": "https://s3.amazonaws.com/rails3.dealdey.com/system/stores/deal_banners/103/S36x67/7.jpg?1489575077",
        "least_priced_variant": {
            "id": 368928,
            "discounted_price": 4500,
            "list_price": 25000,
            "variants_have_same_price": 0
        },
        "merchant": {
            "merchant_id": 3260,
            "merchant_name": "Indy Salon & Spa"
        }
    }
  ]
}
```

## Increase/Decrease Cart Item Quantity

### HTTP Request
`POST /cart_items/<cart_item_id>/change_quantity`

### URL Parameter
- cart_item_id

### Query Parameter

- auth_token
- access_key

### Body Parameter

- quantity. The new quantity of the cart item. It must be greater then 0 and not greater then the maximum available quantity

### Sample Responses

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
        "shipping_address": {
            "address_line": "8 Bode Thomas, Surulere",
            "area": "Ikeja",
            "global": false,
            "id": 2048006,
            "landmark": "Lagos",
            "name": "Adebayo Akinlaja",
            "state": "Lagos"
        },
        "user": {
            "email": "damilola.ade@dealdey.com",
            "mobile": "08155917030",
            "mobile_verified": true
        },
        "cart_items": [
            {
                "id": 4442075,
                "deal_id": 142770,
                "variant_id": 376896,
                "end_date": "2018-12-31",
                "quantity": 5, // quantity has been updated to 5
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

When new quantity is more than the available quantity

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
        "shipping_address": {
            "address_line": "8 Bode Thomas, Surulere",
            "area": "Ikeja",
            "global": false,
            "id": 2048006,
            "landmark": "Lagos",
            "name": "Adebayo Akinlaja",
            "state": "Lagos"
        },
        "user": {
            "email": "damilola.ade@dealdey.com",
            "mobile": "08155917030",
            "mobile_verified": true
        },
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

When cart item is not in the cart

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
        "shipping_address": {
            "address_line": "8 Bode Thomas, Surulere",
            "area": "Ikeja",
            "global": false,
            "id": 2048006,
            "landmark": "Lagos",
            "name": "Adebayo Akinlaja",
            "state": "Lagos"
        },
        "user": {
            "email": "damilola.ade@dealdey.com",
            "mobile": "08155917030",
            "mobile_verified": true
        },
        "cart_items": [<cart_items>]
    },
    "deals_removed": [],
    "bestseller_deals": null
}
```

## Remove item from Cart

### HTTP Request
`POST /cart_items/<cart_item_id>/remove`

### URL Params
- cart_item_id

### Query Params
- auth_token
- access_key

### Sample Responses

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
        "shipping_address": {
            "address_line": "8 Bode Thomas, Surulere",
            "area": "Ikeja",
            "global": false,
            "id": 2048006,
            "landmark": "Lagos",
            "name": "Adebayo Akinlaja",
            "state": "Lagos"
        },
        "user": {
            "email": "damilola.ade@dealdey.com",
            "mobile": "08155917030",
            "mobile_verified": true
        },
        "cart_items": [
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
