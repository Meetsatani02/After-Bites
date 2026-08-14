After-Bites — Email & WhatsApp Marketing Playbook (Klaviyo)

A beginner's guide. Read top-to-bottom once, then use it as a checklist.
Tools in your stack: Shopify (store) · GoKwik (login) · Razorpay Magic Checkout (checkout) · Klaviyo (email + WhatsApp).

--------------------------------------------------------------------------------

1. THE 3 CONCEPTS YOU MUST UNDERSTAND FIRST

| Term | What it means | Example |
|------|---------------|---------|
| Campaign | A one-time message you write and blast to a list. Manual. | "Diwali Sale – 20% off today" sent to everyone. |
| Flow | An automated sequence that fires when a customer does something (a trigger). Set once, runs forever. | Someone abandons cart, they get 3 reminders over 2 days automatically. |
| Segment / List | A group of contacts. A list is manual/opt-in; a segment is auto-built from rules. | Segment: "Bought in last 60 days". |

Golden rule: Flows make about 80% of email/WhatsApp revenue with 20% of the effort, because they run on autopilot. Build flows first, do campaigns second.

--------------------------------------------------------------------------------

2. BEFORE YOU BUILD ANYTHING — THE PLUMBING (do this once)

You cannot market to people you can't reach. So step zero is making sure contacts + consent flow from GoKwik/Shopify into Klaviyo.

2.1 Connect the tools
- Shopify to Klaviyo: Install the Klaviyo app from Shopify App Store, then connect. This syncs customers, orders, products automatically.
- GoKwik (login): GoKwik captures the customer's phone number when they log in. Make sure that number lands on the Shopify customer record.
- Razorpay Magic Checkout (checkout): Razorpay captures phone number, email, and shipping address at checkout (phone via OTP). When an order is placed, that data flows into Shopify as the customer + order record. Klaviyo then pulls it from Shopify.
  - After connecting, check Klaviyo Profiles and confirm new orders show up with both email and phone.
  - Important — abandoned checkout tracking: Because Razorpay Magic Checkout replaces Shopify's native checkout, Shopify's built-in "Checkout Started" event may NOT fire the way Klaviyo expects. That means Klaviyo's standard abandoned-checkout flow can fail to trigger. Two options: (a) use Razorpay Magic Checkout's own abandoned-cart feature/integration to capture and message drop-offs, or (b) trigger Klaviyo off the earlier "Added to Cart" event instead. Test with a real drop-off (add to cart, start checkout, don't pay) and see what shows up in Klaviyo before you rely on it.

2.2 Get consent (legally required — don't skip)
- Email: A subscriber must opt in (newsletter popup, checkout checkbox).
- WhatsApp: WhatsApp Business rules require explicit opt-in before you message someone. You collect it via:
  - A checkbox at checkout / signup: "Send me order updates & offers on WhatsApp"
  - A Klaviyo signup form
- Warning: Messaging people who never opted in gets your WhatsApp number banned by Meta. Only message opted-in contacts.

2.3 Klaviyo free-plan reality check
- Free plan = limited monthly email sends and a small contact cap (verify current numbers in your Klaviyo account — they change).
- WhatsApp in Klaviyo needs a connected Meta WhatsApp Business account and may need a paid tier / has per-message costs. Confirm what's included in your plan inside Klaviyo Settings > Billing before promising yourself free WhatsApp.
- Strategy on a free plan: put your cheap, high-value messages on WhatsApp (order/shipping updates people love), and keep bulk promos on email to save WhatsApp cost.

--------------------------------------------------------------------------------

3. THE FLOW MAP (build these in this order)

Priority = revenue impact. Start at number 1.

    Visitor signs up ----------> 1. WELCOME FLOW              (email + WhatsApp)

    Adds to cart, no buy ------> 2. ABANDONED CART FLOW       (biggest earner)

    Starts checkout, no buy ---> 3. ABANDONED CHECKOUT FLOW   (GoKwik checkout)

    Buys something ------------> 4. POST-PURCHASE / THANK YOU (builds loyalty)

    Order delivered ~7 days ---> 5. REVIEW REQUEST FLOW       (social proof)

    Bought a consumable -------> 6. REPLENISHMENT FLOW        (perfect for pouches)

    No purchase in 60-90 days -> 7. WIN-BACK FLOW

After-Bites sells a consumable product (pouches run out). Flow number 6 Replenishment is a money-printer for you — prioritise it right after cart flows.

--------------------------------------------------------------------------------

4. EACH FLOW, STEP BY STEP (trigger + timing + channel + template)

For every flow: in Klaviyo go to Flows > Create Flow > Build your own, pick the trigger, then add Email and WhatsApp/SMS action blocks with time delays between them.

Placeholders like {{ first_name }}, {{ product_name }} are Klaviyo variables — Klaviyo fills them in automatically per person.

--------------------------------------------------------------------------------

FLOW 1 — Welcome Flow
Trigger: Subscribed to list (newsletter popup / checkout opt-in)
Goal: Introduce brand, give a first-order nudge.

| Step | Wait | Channel | Message |
|------|------|---------|---------|
| 1 | 0 min | Email | Welcome + 10% code |
| 2 | 30 min | WhatsApp | Short nudge if code unused |
| 3 | 2 days | Email | Brand story / why tobacco-free |

Email 1 — subject: Welcome to After-Bites. Here's 10% off

    Hi {{ first_name|default:'there' }},

    Welcome to After-Bites — clean, tobacco-free pouches made for a fresher hit.

    Here's 10% off your first order: WELCOME10

    [ Shop Now ]  ->  yourstore.com

    Questions? Just reply to this email.
    – Team After-Bites

WhatsApp 2:

    Hey {{ first_name|default:'' }}, your 10% welcome code WELCOME10 is still waiting.
    Grab your first pack of After-Bites here: yourstore.com
    Tobacco-free. No mess. Reply STOP to opt out.

--------------------------------------------------------------------------------

FLOW 2 — Abandoned Cart Flow (biggest earner)
Trigger: Added to Cart / "Checkout Started" metric (but did NOT place order)
Goal: Recover the sale. This is usually your number 1 revenue flow.

| Step | Wait | Channel | Message |
|------|------|---------|---------|
| 1 | 1 hour | Email | "You left something behind" |
| 2 | 4 hours | WhatsApp | Short reminder + cart link |
| 3 | 24 hours | Email | Add urgency / small incentive |

Add a flow filter: "has not placed order since starting this flow" so buyers stop getting reminders.

Email 1 — subject: You left your pouches behind

    Hi {{ first_name|default:'there' }},

    You've got great taste — {{ product_name }} is still in your cart.

    [ Return to Cart ]

    Selling fast, so don't wait too long.
    – Team After-Bites

WhatsApp 2:

    {{ first_name|default:'Hey' }}, your After-Bites cart is still saved.
    Finish up here: {{ checkout_url }}
    Fast delivery, COD available. Reply STOP to opt out.

Email 3 — subject: Last chance — here's 5% off to finish up

    Still thinking it over?
    Use SAVE5 for 5% off your cart — valid for 24 hours only.

    [ Complete My Order ]

--------------------------------------------------------------------------------

FLOW 3 — Abandoned Checkout (Razorpay Magic Checkout)
Trigger: Customer started checkout but did not pay. Because Razorpay Magic Checkout collects phone (via OTP) up front, you'll often have their number for WhatsApp, which is gold here.
Goal: Same as cart, but for people who got further (higher intent).

Setup note: Razorpay Magic Checkout runs outside Shopify's native checkout, so Shopify's "Checkout Started" event may not reach Klaviyo. Before building this flow, decide the source:
- Option A (recommended to check first): Use Razorpay Magic Checkout's own abandoned-cart recovery — it can message drop-offs directly. Confirm what's available in your Razorpay dashboard.
- Option B: Trigger the Klaviyo flow off "Added to Cart" instead of "Started Checkout" so it still fires even if the checkout event is missing.

| Step | Wait | Channel | Message |
|------|------|---------|---------|
| 1 | 30 min | WhatsApp | "Almost done!" + resume link |
| 2 | 6 hours | Email | Reminder |

WhatsApp 1:

    {{ first_name|default:'Hi' }}, you were one tap away from your After-Bites order.
    Resume checkout: {{ checkout_url }}
    COD & UPI available. Reply STOP to opt out.

Warning: Only enable this if the phone numbers are reaching Klaviyo with WhatsApp consent. Otherwise keep it email-only.

--------------------------------------------------------------------------------

FLOW 4 — Post-Purchase / Thank-You
Trigger: Placed Order
Goal: Reassure, reduce "where's my order?" support, start loyalty.

| Step | Wait | Channel | Message |
|------|------|---------|---------|
| 1 | 10 min | WhatsApp | Order confirmed + what's next |
| 2 | 1 day | Email | Thank you + how to use the product |

WhatsApp 1:

    Thanks for your order, {{ first_name|default:'' }}!
    Order number {{ order_id }} is confirmed. We'll message you when it ships.
    Questions? Just reply here.

Email 2 — subject: Thanks! Here's how to get the most out of After-Bites

    Your pouches are on the way.

    Quick tips:
    - Tuck one under your lip, no chewing needed
    - Each pouch lasts about 20-30 mins
    - Store in a cool, dry place

    Love it? A review would mean the world (link coming soon).

--------------------------------------------------------------------------------

FLOW 5 — Review Request
Trigger: Fulfilled Order + wait about 7 days (enough time to try it)
Goal: Collect reviews = social proof = more sales.

| Step | Wait | Channel | Message |
|------|------|---------|---------|
| 1 | 7 days after fulfilled | Email | Ask for review |
| 2 | 3 days | WhatsApp | Gentle nudge if no review |

Email 1 — subject: How are your After-Bites?

    Hi {{ first_name|default:'there' }},

    You've had a week with your pouches — what do you think?

    [ Leave a 30-second review ]

    As a thank-you, we'll email you a discount for your next pack.

--------------------------------------------------------------------------------

FLOW 6 — Replenishment (your secret weapon)
Trigger: Placed Order + time delay = how long a pack lasts (estimate, e.g. 21 days)
Goal: Remind them to reorder right when they're running low, driving repeat revenue.

| Step | Wait | Channel | Message |
|------|------|---------|---------|
| 1 | about 21 days after order | WhatsApp | "Running low?" + reorder link |
| 2 | 3 days | Email | Reorder + subscribe idea |

WhatsApp 1:

    {{ first_name|default:'Hey' }}, running low on After-Bites?
    Reorder in one tap: yourstore.com
    Restock before you run out. Reply STOP to opt out.

Tune the "21 days" to how long a pack actually lasts your average customer. This one flow can drive a huge share of repeat orders for a consumable.

--------------------------------------------------------------------------------

FLOW 7 — Win-Back (lapsed customers)
Trigger: Segment "placed order once, nothing in 60-90 days"
Goal: Re-activate people drifting away.

| Step | Wait | Channel | Message |
|------|------|---------|---------|
| 1 | Day 0 | Email | "We miss you" + offer |
| 2 | 4 days | WhatsApp | Reminder of offer |

Email 1 — subject: We miss you — here's 15% back

    It's been a while, {{ first_name|default:'friend' }}.

    Here's 15% off to welcome you back: COMEBACK15

    [ Reorder Now ]

--------------------------------------------------------------------------------

5. CAMPAIGNS (the manual broadcasts) — a simple monthly rhythm

Once flows run themselves, add campaigns for news/offers. A calm starter cadence:

| Frequency | Channel | Type |
|-----------|---------|------|
| 1x / week | Email | Offer, new flavour, or content |
| 2x / month | WhatsApp | Only your best offer (keep WhatsApp rare so people don't mute you) |

Before sending any campaign:
- Send to a segment, not everyone (e.g. "engaged in last 90 days") — protects deliverability and free-plan send limits.
- Always include an unsubscribe / STOP option.
- A/B test the subject line when you can.

--------------------------------------------------------------------------------

6. WHATSAPP RULES (so Meta doesn't ban you)

1. Opt-in only. Never message someone who didn't agree.
2. Templates need approval. WhatsApp marketing messages use pre-approved templates (Klaviyo submits them to Meta). Utility messages (order/shipping updates) are easier to get approved than promos.
3. Include STOP. Every marketing message needs an opt-out.
4. Don't spam. 2-4 WhatsApp marketing messages a month max. It's a personal channel.
5. Utility over Promo. Order confirmations, shipping updates, replenishment reminders feel helpful, get approved easily, and are cheaper. Lean into these.

--------------------------------------------------------------------------------

7. YOUR 7-DAY ACTION CHECKLIST

- Day 1: Confirm Shopify and Klaviyo connected; check profiles have email + phone (from GoKwik login and Razorpay Magic Checkout).
- Day 1: Add a newsletter popup with email + WhatsApp opt-in checkbox.
- Day 2: Build Welcome Flow (Flow 1).
- Day 3: Build Abandoned Cart (Flow 2) — the big one.
- Day 4: Build Post-Purchase (Flow 4) + Abandoned Checkout (Flow 3).
- Day 5: Connect WhatsApp (Meta Business account) in Klaviyo; submit utility templates.
- Day 6: Build Replenishment (Flow 6) + Review (Flow 5).
- Day 7: Build Win-Back (Flow 7); schedule your first email campaign.

--------------------------------------------------------------------------------

8. WHAT "GOOD" LOOKS LIKE (rough benchmarks)

| Metric | Aim for |
|--------|---------|
| Email open rate | 25-40% |
| Email click rate | 2-5% |
| Abandoned cart recovery | 5-15% of carts |
| Flow revenue share | 20-40% of total store revenue |
| Unsubscribe rate | Under 0.5% per send |

Check these in Klaviyo Analytics. If unsubscribes climb, you're sending too often — slow down.

--------------------------------------------------------------------------------

QUICK GLOSSARY
- Trigger — the event that starts a flow.
- Flow filter — a condition that removes people from a flow (e.g. "already bought").
- Variable — {{ ... }} placeholder Klaviyo auto-fills.
- Segment — auto-updating group based on rules.
- Deliverability — whether your emails land in inbox vs spam. Protected by only mailing engaged people.

Start small: Welcome + Abandoned Cart + Post-Purchase covers most of the value. Add the rest as you get comfortable.
