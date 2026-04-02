# TPMA GHL Setup — Tomorrow's Checklist

**Sub-account:** Perfect Synergy Solutions  
**Time estimate:** 30–45 minutes total

---

## Step 1: Create the Two Contact Tags

1. In GHL → go to **Contacts** → **Tags** (top right or settings)
2. Create tag: `TPMA-Newsletter`
3. Create tag: `TPMA-Member`

---

## Step 2: Build Form 1 — "TPMA Briefing Signup"

1. Go to **Sites** → **Forms** → **New Form**
2. Name it: `TPMA Briefing Signup`
3. Add fields:
   - **First Name** (required)
   - **Email** (required)
4. Style: minimal, no extra fields
5. Submit button text: `Get the Weekly Briefing`
6. **Save**
7. Click **Integrate** → copy the embed code → paste it here (or send to Manus)

---

## Step 3: Build Form 2 — "TPMA Member Signup"

1. Go to **Sites** → **Forms** → **New Form**
2. Name it: `TPMA Member Signup`
3. Add fields:
   - **First Name** (required)
   - **Last Name** (required)
   - **Email** (required)
   - **Company Name** (required)
   - **Property Type** — Dropdown (required): Hotel / Healthcare / Commercial Real Estate / Multifamily / Other
   - **City** (required)
4. Submit button text: `Join TPMA`
5. **Save**
6. Click **Integrate** → copy the embed code → paste it here (or send to Manus)

---

## Step 4: Build Workflow 1 — "TPMA Briefing Welcome"

**Trigger:** Form submitted → TPMA Briefing Signup

**Actions (in order):**

1. **Add Tag:** `TPMA-Newsletter`
2. **Add Tag:** `Source - TPMA Site`
3. **Send Email:**
   - From Name: `Texas Parking Management Association`
   - From Email: `briefing@texasparkingmanagement.com`
   - Subject: `You're in — welcome to the TPMA Weekly Briefing`
   - Body: *(paste from email template below)*

---

## Step 5: Build Workflow 2 — "TPMA Member Welcome"

**Trigger:** Form submitted → TPMA Member Signup

**Actions (in order):**

1. **Add Tag:** `TPMA-Member`
2. **Add Tag:** `Source - TPMA Site`
3. **Send Email to contact:**
   - From Name: `Texas Parking Management Association`
   - From Email: `briefing@texasparkingmanagement.com`
   - Subject: `Welcome to TPMA — you're now listed in the registry`
   - Body: *(paste from email template below)*
4. **Send Internal Notification (email to you):**
   - To: `hunter@americanwatersavings.com`
   - Subject: `New TPMA Member: {{contact.firstName}} {{contact.lastName}}`
   - Body:
     ```
     New TPMA member signup:
     
     Name: {{contact.firstName}} {{contact.lastName}}
     Company: {{contact.companyName}}
     Property Type: {{contact.propertyType}}
     City: {{contact.city}}
     Email: {{contact.email}}
     
     Submitted: {{now}}
     ```

---

## Step 6: Set Up Email Forwarding

At your domain registrar (wherever texasparkingmanagement.com is registered):

1. Go to **Email Forwarding** or **Email Aliases**
2. Create: `briefing@texasparkingmanagement.com` → forward to `hunter@americanwatersavings.com`

This makes the "From" address look like it's from TPMA while replies come to your real inbox.

**Note:** Some registrars call this "email forwarding" or "catch-all forwarding." If your registrar doesn't support it, use Cloudflare Email Routing (free) — takes 10 minutes to set up.

---

## Email Template 1: Briefing Welcome

**Subject:** You're in — welcome to the TPMA Weekly Briefing

```
Hi {{contact.firstName}},

You're now subscribed to the Texas Parking Management Association Weekly Briefing.

Every Thursday, you'll get:

• Enforcement updates — towing law changes, signage requirements, city-specific rules
• Revenue strategy — pricing, conversion, and vendor selection insights
• Market intelligence — demand signals from Houston, Dallas, Austin, San Antonio, and beyond

This is a no-fluff, no-vendor-bias briefing written for Texas property owners. 
We don't sell anything. We just report what's happening.

Your first briefing arrives this Thursday.

— The TPMA Editorial Team
Texas Parking Management Association
texasparkingmanagement.com

---
You subscribed at texasparkingmanagement.com. 
Unsubscribe at any time: {{unsubscribe_link}}
```

---

## Email Template 2: Member Welcome

**Subject:** Welcome to TPMA — you're now listed in the registry

```
Hi {{contact.firstName}},

Welcome to the Texas Parking Management Association.

You're now a registered member of TPMA — an independent coalition of Texas property owners 
advocating for fair, transparent parking management.

What you get as a member:

• The Weekly Briefing — enforcement news, revenue strategy, market intelligence
• Registry listing — your property is now part of the Texas Parking Owners Registry
• Member resources — RFP templates, towing law guides, and market data (coming soon)

We'll be in touch Thursday with your first briefing.

If you have questions or want to submit a topic for coverage, reply to this email.

— The TPMA Editorial Team
Texas Parking Management Association
texasparkingmanagement.com

---
You joined at texasparkingmanagement.com.
Unsubscribe at any time: {{unsubscribe_link}}
```

---

## Final Step: Get Embed Codes to Manus

Once both forms are created in GHL:
1. Click each form → **Integrate** tab
2. Copy the iframe embed code
3. Send both codes to Manus
4. Manus will update the site and push to GitHub in under 5 minutes

---

*Document prepared by TPMA build team — April 3, 2026*
