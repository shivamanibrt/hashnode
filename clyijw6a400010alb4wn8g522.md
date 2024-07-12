---
title: "Integrating Stripe Payments into Your SaaS with MERN Stack."
seoTitle: "Integrating Stripe Payments with MERN Stack: A Comprehensive Guide."
seoDescription: "Learn how to integrate Stripe payments into your SaaS application using the MERN stack. This guide covers frontend and backend implementation."
datePublished: Fri Jul 12 2024 10:24:10 GMT+0000 (Coordinated Universal Time)
cuid: clyijw6a400010alb4wn8g522
slug: integrating-stripe-payments-into-your-saas-with-mern-stack
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/XH2JFgT4Abc/upload/133761be8faa6ef4d9664d9e2344889f.jpeg
tags: stripepayments, stripe-integration, nodejs-payment-processing, saas-payments

---

Hey, in this post I am going to explain how you can integrate Stripe payments into your SaaS and update your database for payments using webhooks. I will use MongoDB as an example, but this method can be applied to any other database of your choice. I use React, Express, and Node.js for the tech stack.

### Prerequisites

* Have a basic understanding of the MERN stack.
    
* Create separate folders for frontend and backend code.
    
* Have a pricing page of your choice, or set up the code as needed. If not you can download the page from ***Link***
    
* Install Stripe on both the Frontend and Backend.
    

### Let's have a look at how the layout looks.

I have created a dummy pricing page with a toggle button that offers two options: monthly or annually. There are also two cards: free and premium. For this tutorial, we will only be working with the premium card.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720773909004/de6a2779-144f-4f49-a384-400fec97ed21.png align="center")

Once you click to Try Free for 14 days it will navigate you to stripe checkout options where you can simply provide your details and it will update your database accordingly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720774003199/c4d95b37-bf5f-4bf2-a065-41cf215d0aaa.png align="center")

1. ### Configure Stripe and create products.
    

* Go to Stripe and create an account.
    
* Search for "Products" and create two products: Monthly and Annually.
    
* Copy their price IDs from the product profiles and store them in your `.env` file or another secure location.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720774870123/05fa290b-3828-4774-9da3-732d8701d1f4.jpeg align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720774877458/5016e0c0-3a77-41e0-b412-cde7e8e120c1.jpeg align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720774881477/bc3cd7bc-930d-426b-a700-47f64816d835.jpeg align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720774936859/31052922-b599-4bac-9eab-610d531adc32.jpeg align="center")

Now, go to the Developer section in Stripe and copy the **Publishable Key** and **Secret Key**. Store them in a safe place, preferably in your `.env` file. You'll need these to interact with your Stripe account programmatically.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720775499206/5986c5b2-93e1-4a7e-adbd-59ca09c948cf.jpeg align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720775505351/1ac06379-6307-49f1-a7b6-6d3c8d0d6ede.jpeg align="center")

2. ### Frontend: Implement Stripe Frontend Integration and Subscription Management
    

* Install Stripe using the following command:
    
    `npm install --save @stripe/react-stripe-js @stripe/stripe-js`
    
* Write the code for a Premium Card component and attach a function, e.g., `handleOnPricing` to Premium card div.
    
* Choose the subscription type based on a toggle button and store it using `useState` hooks.
    
* Create `stripeProfile` and load the **Publishable Key** from the `.env` file to connect with the correct Stripe user for payment processing.
    
* Create an object that stores `userId`, `email`, and `planType` to pass to the backend.
    
* Create three functions:
    
    * To store the current Stripe profile in the database with the customer ID.
        
    * To retrieve the current user session for utilizing the email address and pricing information during checkout.
        
    * A prebuilt Stripe redirect-to-checkout function.
        

Code eg. below

```javascript
import React, { useEffect, useState } from 'react';

const stripePromise = loadStripe(process.env.REACT_APP_STRIPE_PUBLISHABLE_KEY);

const Pricing = () => {
    const { adminUser } = useSelector((state) => state.admin);
    const [loading, setLoading] = useState(false);
    const [toggleOn, setToggleOn] = useState(true);

    const handelOnToggle = (e) => {
        setToggleOn(!toggleOn);
    };

    const handelOnPricing = async () => {
        setLoading(true);
        if (adminUser && adminUser?._id) {
            const subscriptionType = toggleOn ? 'yearly' : 'monthly';
            const obj = {
                userId: adminUser?._id,
                email: adminUser?.email,
                plan: subscriptionType,
            };
            // 1. Create a Stripe customer
            const { customerId } = await createStripeCustomer(obj);

            // 2. Create a Stripe Checkout Session
            const { sessionId } = await stripePayment({ ...obj, customerId });

            // 3. Redirect the user to the Stripe Checkout page
            const stripe = await stripePromise;
            await stripe.redirectToCheckout({ sessionId });
        } else {
            navigate('/signup');
        }
    };
```

I created a separate component to handle API calls to make clean code.

```javascript
import axios from 'axios'

const rootUrl = process.env.REACT_APP_API_ENDPOINT;
const stripeEP = rootUrl + '/stripe'

const apiProcessor = async ({ method, url, data}) => {
    try {
        const response = await axios({
            method,
            url,
            data,
           
        })
        return response.data
    } catch (error) {
        let message = error.message
        console.log(message)
        if (error.response) {
            return {
                status: 'error',
                message
            }
        }

    }
}

// creting stripe customer  payment
export const createStripeCustomer = (data) => {
    const option = {
        method: 'post',
        url: stripeEp + '/create-customer',
        isPrivate: true,
        data
    }
    return apiProcessor(option)
}

// stripe payment
export const stripePayment = (data) => {
    const option = {
        method: 'post',
        url: stripeEp + '/create-checkout-session',
        isPrivate: true,
        data
    }
    return apiProcessor(option)
}
```

### Backend: Handle API Requests and Payment Processing for Stripe Integration

* Install Stripe using the following command:
    
    `npm install --save @stripe/react-stripe-js @stripe/stripe-js`
    
* Create `stripeProfile` and load the **Secret Key** from the `.env` file to connect with the correct Stripe user for payment processing.
    

Create two endpoints

* Create a customer in the database based on the Stripe response to keep a record for future reference.
    
* Create an endpoint for checkout sessions to process payments programmatically based on a monthly or yearly subscription.
    

Code eg. below.

```javascript
import express from 'express'
const router = express.Router();
import Stripe from 'stripe';
import dotenv from 'dotenv'
import { updateOneAdminUser } from '../../MongoModles/User/AdminUserModal.js';

dotenv.config();

const stripe = new Stripe(process.env.STRIPE_SECRET);

//Create stripe  customer 
router.post('/create-customer', async (req, res, next) => {
    try {
        const { email, userId } = req.body;
        const customer = await stripe.customers.create({
            email: email,
        });
        // Update the user's document with the Stripe customer ID
        await updateOneAdminUser({ _id: userId }, { 'subscription.stripeCustomerId': customer.id });

        res.status(200).json({ customerId: customer.id });
    } catch (error) {
        next(error);
    }
});


//Stripe checkout session
router.post('/create-checkout-session', async (req, res, next) => {
    try {
        const { plan, customerId, } = req.body;
        const priceId = plan === 'monthly' ? process.env.STRIPE_MONTHLY_PLAN_ID : process.env.STRIPE_YEARLY_PLAN_ID;
        const session = await stripe.checkout.sessions.create({
            customer: customerId,
            payment_method_types: ['card'],
            mode: 'subscription',
            line_items: [
                {
                    price: priceId,
                    quantity: 1,
                },
            ],
            success_url: `${process.env.SERVER_URL}/home`,
            cancel_url: `${process.env.SERVER_URL}/pricing`,
        });
        res.status(200).json({ sessionId: session.id });
    } catch (error) {
        next(error);
    }
});



export default router;
```

Since this blog is already quite detailed, I will cover how to use webhooks to update the database based on payment events such as success, cancellation, or updates in a separate section.