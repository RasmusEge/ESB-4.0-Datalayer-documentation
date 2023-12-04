# ESB 3.0 tracking requirement document (WEB) | Ecommerce 
This document contains datalayer tracking requirements for ecommerce events on https://stage-frontend4.europeanspermbank.com (also to be used on the live site)


## Table of content
[**1. Ecommerce tracking**](#ecommerce-tracking) <br/>
[1.1 Items array](#items-array) <br/>
[1.2 Select Item](#select-item) <br/>
[1.3 View Item](#view-item) <br/>
[1.4 Add to cart](#add-to-cart) <br/>
[1.5 View cart](#view-cart) <br/>
[1.6 Remove from cart](#remove-from-cart) <br/>
[1.7 Begin checkout](#begin-checkout) <br/>
[1.8 Add Contact info](#add-contact-info) *<br/>
[1.9 Add ZOO-event info](#add-zoo-event-info) *<br/>
[1.10 Add ZOO-card info](#add-zoo-card-info) *<br/>
[1.11 Add All info](#all-info-added) *<br/>
[1.12 Add Payment info](#add-payment-info) <br/>
[1.13 Purchase](#purchase) <br/>

## Ecommerce tracking
Detailed below are all ecommerce events and parameters for the checkout journey, from view item to purchase 

Generic Google documentation: [https://developers.google.com/analytics/devguides/collection/ga4/ecommerce?client_type=gtag](https://developers.google.com/analytics/devguides/collection/ga4/ecommerce?client_type=gtag)

## Items array
#### Items array is used throughout all ecommerce events and includes all items in a purchase for both chekout 1 and 2    
````javascript
items: [
    {
      item_id: "SKU_12345", //Example - must be uniqie ID for product
      item_name: "Jatin IUI MOTO20+", // dynamic value for name
      affiliation: "ESB",
      index: 0,
      item_category: "brown", // dynamic value for eye color
      item_category2: "strawberry blond", // dynamic value for hair color
      item_category3: "180", // dynamic value for height
      item_category4: "dutch/danish", // dynamic value for ethnicity
      item_category5: "fair", // dynamic value for skintone 
      item_category6: "libra", // dynamic value for Zodiac
      item_category7: "ISJD", // dynamic value for personality 
      price: 7312.75, // Dynamic value for price 
      quantity: 2
    },
   
    {
      item_id: "SKU_123425", // dynamic ID-value for product
      item_name: "Pregnancy slot", // dynamic value for name
      affiliation: "ESB",
      index: 1,
      price: 3259.37, // Dynamic value for price 
      quantity: 1
    }, 

    {
      item_id: "SKU_123415", // dynamic ID-value for product
      item_name: "GeneXmatch", // dynamic value for name
      affiliation: "ESB",
      index: 1,
      price: 3259.37, // Dynamic value for price 
      quantity: 1
    }
         {
      item_id: "SKU_123415", // dynamic ID-value for product
      item_name: "3 years storage", // dynamic value for name
      affiliation: "ESB",
      index: 1,
      price: 3012.37, // Dynamic value for price 
      quantity: 1
    }

]
````

## Select item
#### Send event when user clicks on a donor and when a user chooses a donor

![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/529951fa-ef8d-4023-ae66-abf0c19e21e0)
![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/eecbce72-80a8-45bf-b8f3-643885c0b8cb)

````javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'select_item',
  ecommerce: {
  items: [{ 
            // insert items array with dynamic values   
          }]    
     }
});
````


## View Item

#### Send event when a user a loads donorpage 1 (pagepath:"/product-detail/Jatin") and donorpage 2 (pagepath:"/add-to-cart")  
Donerpage 1:
![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/6dee9d8b-b217-4a1c-9234-097a50e4d033)
Donorpage 2:
![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/63301baa-8f57-40d7-892b-72ff5c9b56b6)

````javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'view_item',
  ecommerce: {
   items: [{ 
            // insert items array with dynamic values   
          }]    
     }
});
````

## Add to cart
#### Send event when a user succesfully adds product to cart, either on donorpage 2 and/or when a user adds product in the cart
![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/60d45635-6e71-413d-81eb-a80f606cf152)
![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/e9cd5e37-9531-4e09-a4b0-422bf376228f)
![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/4a08a6db-27df-4ed7-a42e-9935f548c8c6)

````javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'add_to_cart',
  ecommerce: {
  items: [{ 
            // insert items array with dynamic values   
         }]    
     }
});  
````

## View cart
#### Send event when user loads the cart page and/or when users clicks cart icon 

![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/5e9ea481-7f45-48ec-ae87-c56e395640a7)
![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/82220bc8-5464-4017-bf83-b6ea5b336e12)


````javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'view_cart',
  ecommerce: {
  items: [{ 
            // insert items array with dynamic values   
         }]    
     }
});
````

## Remove from cart
#### Send event when user removes product from cart

![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/7af9b7da-c56f-4bcd-b29a-370902e015a1)
![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/aab27769-a1aa-49a7-a183-80afd6942670)

````javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'remove_from_cart',
  ecommerce: {
  items: [{ 
           // insert items array with dynamic values   
         }]    
     }
});
````

## Begin checkout
#### Send event when user starts checkout flow

![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/fd8f6b3f-fdac-42f0-91ac-2697e9494cb6)

````javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'begin_checkout',
  ecommerce: {
  items: [{ 
           // insert items array with dynamic values   
         }]    
     }
});
````

## Add contact info
#### Send event when user has successlfully added contact info 
![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/acd6e3ae-1898-4fd0-ba16-46ee4adbf0ad)

````javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'add_contact_info',
 });
````

## Add treatment info
#### Send event when user has successlfully added all treatment info 

![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/a785b2c5-aca6-45fe-b44c-282312d01321)


````javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'add_treatment_info',
  treatment_clinic: 'Juno CITY IVF' // incert dynamic value for clinic name
  treatment_date: '20.12.24'  // incert dynamic value for treatment date
);
````

## Add shipping info 
#### Send event when user has successlfully added all shipping info 

![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/bb8fc281-24e7-42fa-8424-c06188df385d)


````javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'add_shipping_info',
  ecommerce: {
    shipping_tier: 'FedEx', // dynamic value for shiping provider (if static value is "standard" please use this)
  items: [{ 
           // insert items array with dynamic values   
         }]    
     }
});
````


## Add payment info 
#### Send event when user has successfully added payment info



````javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'add_payment_info',
    ecommerce: {
    payment_type: "creditcard" // dynamic value for payment method 
      items: [{ 
           // insert items array with dynamic values   
         }]    
     }
});
````

## Purchase 
Send event when user has successfully made a purchase - if possible send in callback from paymentgateway provider. if not send when thank you page is loads  

![image](https://github.com/RasmusEge/ESB-3.0/assets/122262884/4efefdfc-bee8-4348-b149-b64a78269b7b)


````javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'purchase',
    ecommerce: {
    currency: 'DKK', // dynamic value
    value: 116.47, // dynamic value
    tax: 7.18, // dynamic value
    shipping: 10.00 // dynamic value
    transaction_id: 'p115-20202000', // dynamic uniquie value for order 
    items: [{      
        // insert items array with dynamic values   
        }]    
     }
});
````

 