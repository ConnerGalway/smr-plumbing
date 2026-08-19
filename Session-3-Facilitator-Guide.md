# Session 3 Facilitator's Guide
## SEO Execution Sprint: 30-Day Results

**Duration:** 2 hours
**Client:** SMR Plumbing & Heating (Beth, Sean, Andrew)
**Facilitator:** Junction Consulting

---

## Pre-Session Checklist (5 min before start)

Confirm the client has:
- [ ] WordPress admin access (can access Pages, Posts, Appearance, WP Rocket)
- [ ] WP Rocket plugin installed and accessible
- [ ] Google Business Profile login ready
- [ ] Google Search Console access
- [ ] Bing Webmaster Tools (or ready to set up)
- [ ] 10-15 job site photos ready to upload
- [ ] Claude project "SMR Content Assistant" open
- [ ] FTP or File Manager access (or Neon Pig on standby)

**If WordPress access is still blocked:** Pivot to Parts 2-4 first. Contact Neon Pig during the call to resolve access.

---

## Part 1: Foundation Fixes (35 min)

### 1.1 Fix Mobile Speed (10 min)

**Goal:** Improve mobile PageSpeed score from 35 to 70+

**Steps:**

1. Open PageSpeed Insights in a new tab: https://pagespeed.web.dev/
2. Test smrplumbing.ca and note current mobile score
3. Log into WordPress admin: smrplumbing.ca/wp-admin
4. Navigate to **Settings > WP Rocket**
5. Configure these settings:

**File Optimization tab:**
- CSS Files: Enable "Minify CSS files"
- CSS Files: Enable "Optimize CSS delivery" (set to "Remove Unused CSS")
- JavaScript Files: Enable "Minify JavaScript files"
- JavaScript Files: Enable "Load JavaScript deferred"
- JavaScript Files: Enable "Delay JavaScript execution"

**Media tab:**
- Enable "LazyLoad" for images
- Enable "LazyLoad" for iframes and videos
- Enable "Add missing image dimensions"
- Enable "WebP Compatibility" if available

**Preload tab:**
- Enable "Preload Links"
- Add critical fonts to "Preload Fonts" if site uses custom fonts

**Advanced Rules tab:**
- Leave defaults unless specific issues arise

6. Click "Save Changes"
7. Click "Clear Cache"
8. Re-test in PageSpeed Insights (wait 60 seconds for cache to rebuild)

**Talking point:** "Mobile score directly affects rankings. Google uses mobile-first indexing, so your mobile score matters more than desktop."

**If score doesn't improve:** Check if the theme is loading heavy scripts. May need Neon Pig to audit theme files.

---

### 1.2 Add Business Address to Footer (5 min)

**Goal:** NAP consistency (Name, Address, Phone) across the site

**Address:** 1081 Roosevelt Crescent, North Vancouver, BC V7P 1M4

**Steps:**

1. In WordPress admin, go to **Appearance > Customize** (or **Appearance > Widgets** depending on theme)
2. Find the footer widget area
3. Add or edit a text widget with this exact format:
   ```
   SMR Plumbing & Heating
   1081 Roosevelt Crescent
   North Vancouver, BC V7P 1M4
   604-616-0062
   ```
4. Save and preview the site
5. Verify the address appears on all pages (check homepage, About, Contact)

**Talking point:** "This address must match your Google Business Profile exactly. Google cross-references these. Any mismatch hurts local rankings."

**Verify GBP match:** Open Google Maps, search "SMR Plumbing," confirm the address matches character-for-character.

---

### 1.3 Check Phone Number on Every Page (3 min)

**Goal:** Ensure 604-616-0062 appears consistently

**Steps:**

1. Open the site in a new tab
2. Check these pages:
   - Homepage (header and footer)
   - Contact page
   - About page
   - Any service pages
3. Use Ctrl+F (Cmd+F on Mac) to search for "604" on each page
4. If any numbers are wrong or missing, note them for editing

**If edits needed:**
- Header phone: Usually in **Appearance > Customize > Header** or theme settings
- Page content: Edit the specific page in **Pages > All Pages**

**Talking point:** "Click-to-call on mobile is a conversion signal. If someone has to hunt for your number, you lose the call."

---

### 1.4 Add LocalBusiness/Plumber Schema (7 min)

**Goal:** Help Google understand the business type, location, and service areas

**Steps:**

1. In WordPress, go to **Plugins > Add New**
2. Search for "Schema Pro" or "Rank Math" (if not already installed)
3. If using Rank Math:
   - Go to **Rank Math > Schema Templates**
   - Click "Add New Schema"
   - Select "Local Business" type
   - Set Business Type to "Plumber"

4. Fill in these fields:
   ```
   Name: SMR Plumbing & Heating
   Address: 1081 Roosevelt Crescent, North Vancouver, BC V7P 1M4
   Phone: 604-616-0062
   URL: https://smrplumbing.ca
   Price Range: $$

   Area Served (add each separately):
   - North Vancouver, BC
   - West Vancouver, BC
   - Burnaby, BC
   ```

5. If no schema plugin exists, provide this JSON-LD to add to the theme's header.php or via a code snippet plugin:

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Plumber",
  "name": "SMR Plumbing & Heating",
  "image": "https://smrplumbing.ca/logo.png",
  "telephone": "604-616-0062",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "1081 Roosevelt Crescent",
    "addressLocality": "North Vancouver",
    "addressRegion": "BC",
    "postalCode": "V7P 1M4",
    "addressCountry": "CA"
  },
  "areaServed": [
    {"@type": "City", "name": "North Vancouver"},
    {"@type": "City", "name": "West Vancouver"},
    {"@type": "City", "name": "Burnaby"}
  ],
  "url": "https://smrplumbing.ca",
  "priceRange": "$$"
}
</script>
```

6. Save and test with Google's Rich Results Test: https://search.google.com/test/rich-results

**Talking point:** "Schema is how you speak Google's language. It tells the algorithm exactly what you do and where you do it."

---

### 1.5 Upload llms.txt and llms-full.txt (5 min)

**Goal:** Make the site discoverable by AI search tools (ChatGPT, Perplexity, Claude)

**Steps:**

1. Open Claude and generate the llms.txt content:

**Prompt for Claude:**
```
Create an llms.txt file for SMR Plumbing & Heating, a plumbing and HVAC company in North Vancouver, BC. They specialize in heat pump installation, gas fitting, furnace repair, and drain cleaning. Phone: 604-616-0062. Address: 1081 Roosevelt Crescent, North Vancouver, BC V7P 1M4. They serve North Vancouver, West Vancouver, and Burnaby.
```

2. The file should look something like:
```
# SMR Plumbing & Heating

> Licensed plumbing and HVAC contractor serving North Vancouver, West Vancouver, and Burnaby, BC.

## Services
- Heat pump installation and repair
- Gas fitting and gas line installation
- Furnace installation and repair
- Drain cleaning and plumbing repairs
- Hot water tank replacement

## Contact
- Phone: 604-616-0062
- Address: 1081 Roosevelt Crescent, North Vancouver, BC V7P 1M4
- Website: https://smrplumbing.ca

## Service Area
North Vancouver, West Vancouver, Burnaby, BC, Canada
```

3. Save as `llms.txt`

4. Create `llms-full.txt` with expanded content including:
   - Full list of services with descriptions
   - Service area details
   - Business hours
   - Certifications and licenses
   - Brief company history

5. Upload both files to the website root via FTP or File Manager:
   - Files go at: smrplumbing.ca/llms.txt and smrplumbing.ca/llms-full.txt

6. Test by visiting: https://smrplumbing.ca/llms.txt

**Talking point:** "This is like robots.txt but for AI. When ChatGPT or Perplexity crawls the web, they look for this file to understand what your business does."

---

### 1.6 Submit Sitemap to Bing (5 min)

**Goal:** Get indexed by Bing so ChatGPT Search can find SMR

**Steps:**

1. Go to Bing Webmaster Tools: https://www.bing.com/webmasters
2. Sign in with Microsoft account (create one if needed)
3. Click "Add a Site"
4. Enter: https://smrplumbing.ca
5. Choose verification method:
   - **Recommended:** Import from Google Search Console (fastest)
   - **Alternative:** Add meta tag to homepage or upload XML file

6. Once verified, go to **Sitemaps** in the left menu
7. Click "Submit sitemap"
8. Enter: https://smrplumbing.ca/sitemap.xml (or sitemap_index.xml if using Yoast/Rank Math)
9. Submit

**Talking point:** "ChatGPT Search runs on Bing's index. If you're not in Bing, ChatGPT literally cannot find you when someone asks for a plumber in North Vancouver."

**Check indexing status:** After a few days, return to Bing Webmaster Tools and check "URL Inspection" for key pages.

---

## Part 2: Content Creation (40 min)

### 2.1 BC Heat Pump Rebates Page (15 min)

**Goal:** Create a page targeting "fortisbc rebate heat pump" (720/mo) and "bc hydro heat pump rebate" (390/mo)

**Steps:**

1. Open the SMR Content Assistant project in Claude
2. Share this brief with Claude:

**Prompt:**
```
Write a webpage for SMR Plumbing & Heating about BC heat pump rebates.

Key requirements:
- Put the answer first (the total rebate amount and that SMR handles paperwork)
- Target keywords: "fortisbc rebate heat pump", "bc hydro heat pump rebate", "heat pump rebate bc"
- Include current rebate amounts (research the latest FortisBC and BC Hydro programs)
- Mention SMR is a registered FortisBC contractor
- Include a clear call to action
- Write in a direct, helpful tone
- Include FAQ section for FAQ schema

Opening line should be: "SMR Plumbing installs heat pumps in North Vancouver with up to $9,000 in combined BC rebates. As a registered FortisBC contractor, we handle the rebate paperwork."

Location: North Vancouver, serving West Van and Burnaby too.
Phone: 604-616-0062
```

3. Review Claude's output with the client
4. In WordPress, go to **Pages > Add New**
5. Title: "BC Heat Pump Rebates | Up to $9,000 in Savings"
6. Set URL slug to: `bc-heat-pump-rebates`
7. Paste the content and format with headings (H2, H3)
8. Add a featured image (heat pump installation photo)
9. If using Rank Math/Yoast:
   - Set focus keyword: "bc heat pump rebates"
   - Write meta description: "Get up to $9,000 in BC heat pump rebates. SMR Plumbing is a registered FortisBC contractor in North Vancouver. We handle your rebate paperwork. Call 604-616-0062."
10. Publish

**Add FAQ Schema:**
If using Rank Math, add FAQ block with 4-5 questions:
- "How much is the FortisBC heat pump rebate?"
- "Does BC Hydro offer heat pump rebates?"
- "Can I combine FortisBC and BC Hydro rebates?"
- "How do I apply for heat pump rebates in BC?"
- "What heat pumps qualify for BC rebates?"

---

### 2.2 North Vancouver Location Page (15 min)

**Goal:** Create a page targeting "plumber north vancouver" and "hvac north vancouver"

**Steps:**

1. In Claude, use this prompt:

**Prompt:**
```
Write a location page for SMR Plumbing & Heating targeting "plumber north vancouver" and "hvac north vancouver."

Requirements:
- Put the main answer first: SMR Plumbing serves North Vancouver for plumbing and HVAC
- Include real numbers: "500+ installations since 2018" (confirm with client)
- Mention specific North Vancouver neighborhoods they serve
- Include services offered
- Add social proof (review count, rating)
- Write FAQ section for schema
- Direct, helpful tone

Business details:
- Address: 1081 Roosevelt Crescent, North Vancouver, BC V7P 1M4
- Phone: 604-616-0062
- Google rating: 4.9 stars, 109 reviews

Also serve: West Vancouver, Burnaby
```

2. Ask the client: "How many installations have you done? Any specific neighborhoods you focus on?"
3. Review and customize the output
4. In WordPress: **Pages > Add New**
5. Title: "Plumber in North Vancouver | SMR Plumbing & Heating"
6. URL slug: `north-vancouver-plumber`
7. Format and add local images
8. Add FAQ schema with questions like:
   - "What areas of North Vancouver do you serve?"
   - "Do you offer emergency plumbing in North Vancouver?"
   - "How fast can you get to North Vancouver?"
9. Publish

**Talking point:** "Location pages are gold for local SEO. This page will rank for anyone searching 'plumber near me' while in North Van."

---

### 2.3 Heat Pump vs Furnace Comparison (10 min)

**Goal:** Create a comparison page targeting "heat pump vs furnace bc" (300/mo)

**Steps:**

1. In Claude, use this prompt:

**Prompt:**
```
Write a comparison page: Heat Pump vs Furnace for BC homeowners.

Requirements:
- Answer the question immediately: which is better for BC climate?
- Include a comparison table (efficiency, cost, lifespan, rebates)
- Mention BC's mild climate makes heat pumps ideal
- Note the rebate advantage for heat pumps
- End with SMR's recommendation and CTA
- FAQ section

Target keyword: "heat pump vs furnace bc"
SMR phone: 604-616-0062
```

2. Review output and verify any technical claims with Sean (he knows this stuff)
3. Create page in WordPress:
   - Title: "Heat Pump vs Furnace: Which Is Best for BC Homes?"
   - URL slug: `heat-pump-vs-furnace-bc`
4. Add comparison table using WordPress table block
5. Include a "Our Recommendation" section at the end
6. Add FAQ schema
7. Publish

**Talking point:** "AI tools love comparison pages. When someone asks Perplexity 'should I get a heat pump or furnace in Vancouver,' this page can be cited."

---

## Part 3: Google Business Profile (20 min)

### 3.1 Add All Services (4 min)

**Goal:** Complete the services list so Google knows everything SMR offers

**Steps:**

1. Go to Google Business Profile: https://business.google.com/
2. Select SMR Plumbing & Heating
3. Click **Edit profile > Services**
4. Add these service categories (confirm with client):

**Plumbing:**
- Emergency plumbing
- Drain cleaning
- Pipe repair
- Water heater installation
- Water heater repair
- Leak detection
- Sewer line repair
- Fixture installation

**HVAC:**
- Heat pump installation
- Heat pump repair
- Furnace installation
- Furnace repair
- Air conditioning installation
- AC repair
- Ductless mini-split installation

**Gas:**
- Gas line installation
- Gas fitting
- Gas appliance hookup
- Gas leak repair

5. Add prices where possible (even ranges help)
6. Save

---

### 3.2 Upload Geotagged Photos (4 min)

**Goal:** Add location-rich photos that shape the AI-generated "vibe" description

**Steps:**

1. Have client share 10-15 photos (should be ready from pre-session)
2. For each photo, add geotag data:

**Option A - Using a phone:**
- If photos are on phone with location enabled, they already have geotags
- Upload directly from phone to GBP

**Option B - Adding geotags manually:**
- Use https://tool.geoimgr.com/
- Upload photo
- Search for "1081 Roosevelt Crescent, North Vancouver"
- Click the location on map
- Download geotagged version

3. In GBP, go to **Photos**
4. Upload photos in these categories:
   - **Logo** (if not already uploaded)
   - **Cover photo** (best project photo)
   - **Interior** (2-3 of team working, office)
   - **Exterior** (van with logo, job sites)
   - **At work** (installation photos, team in action)
   - **Team** (group photo or individual headshots)

5. Write captions with keywords:
   - "Heat pump installation in North Vancouver"
   - "SMR Plumbing team servicing furnace in West Van"
   - "Drain cleaning service in Burnaby"

---

### 3.3 Add 15-20 Q&As (5 min)

**Goal:** Seed the Q&A section with keyword-rich answers that AI Overviews can pull from

**Steps:**

1. In GBP, go to the Q&A section (visible on your listing)
2. Click "Ask a question"
3. Add these questions (you answer your own questions as the owner):

**Service questions:**
1. Q: "Do you install heat pumps in North Vancouver?"
   A: "Yes! SMR Plumbing & Heating is a licensed heat pump installer serving North Vancouver, West Vancouver, and Burnaby. We're a registered FortisBC contractor, so we can help you access up to $9,000 in rebates. Call 604-616-0062 for a free estimate."

2. Q: "What areas do you serve?"
   A: "We serve North Vancouver, West Vancouver, Burnaby, and surrounding areas. Our team is based in North Van and can usually respond same-day for emergencies."

3. Q: "Do you offer emergency plumbing services?"
   A: "Yes, we offer 24/7 emergency plumbing in North Vancouver and nearby areas. Call 604-616-0062 for immediate help with burst pipes, water heater failures, or gas leaks."

4. Q: "How much does a heat pump cost to install in BC?"
   A: "Heat pump installation typically ranges from $5,000-$15,000 depending on the system. With FortisBC and BC Hydro rebates, you could save up to $9,000. We provide free estimates."

5. Q: "Are you licensed for gas fitting?"
   A: "Yes, SMR Plumbing & Heating holds a valid BC gas fitting license. We install gas lines, gas appliances, and perform gas leak detection."

4. Continue adding 10-15 more questions covering:
   - Pricing questions
   - Service area questions
   - Specific service questions (furnace, water heater, drains)
   - Hours and scheduling questions
   - Payment and financing questions

**Talking point:** "When someone asks Google a question and your GBP has the exact answer, you show up in AI Overviews. We're basically pre-loading Google with your answers."

---

### 3.4 Post Twice (3 min)

**Goal:** Show Google the business is active

**Steps:**

1. In GBP, click **Add update**
2. Create first post (Offer):
   - Title: "Free Heat Pump Estimate"
   - Photo: Heat pump installation
   - Text: "Get a free estimate on heat pump installation. As a registered FortisBC contractor, we'll help you access up to $9,000 in rebates. Call 604-616-0062."
   - Button: "Call now" with phone number

3. Create second post (What's new):
   - Photo: Recent project
   - Text: "Just completed another heat pump installation in North Vancouver! The homeowner will save an estimated $1,200/year on heating costs plus received $6,500 in rebates. #HeatPump #NorthVancouver"

4. Set a reminder for ongoing posts:
   - **Monday:** Project photo with brief description
   - **Wednesday:** Offer or seasonal tip
   - **Friday:** Customer testimonial or team update

---

### 3.5 Set Up Review Responses (4 min)

**Goal:** Create a system for responding to every review within 24 hours

**Steps:**

1. Review current reviews in GBP
2. Respond to any unanswered reviews now
3. Show client how to respond:
   - Click on the review
   - Click "Reply"
   - Write personalized response

**Template for positive reviews:**
```
Thanks [Name]! We're glad the [service type] went smoothly. It was great working with you in [neighborhood]. Let us know if you ever need anything else. - The SMR Team
```

**Template for neutral/constructive reviews:**
```
Thanks for the feedback, [Name]. We're always looking to improve. If there's anything we can do to make it right, please call us at 604-616-0062. We appreciate you giving us a try.
```

4. Set up notification:
   - In GBP settings, ensure email notifications are on for new reviews
   - Consider Google Business Profile app on phone for instant alerts

**Talking point:** "Review responses with keywords help rankings. Saying 'glad the heat pump installation went smoothly in North Vancouver' is SEO."

---

## Part 4: 30-Day Plan + Tracking (20 min)

### 4.1 Content Calendar (5 min)

**Goal:** Plan 8-10 new pages over the next 30 days

**Steps:**

1. Open a shared doc or spreadsheet
2. Create this content calendar:

| Week | Page | Target Keywords | Status |
|------|------|-----------------|--------|
| Week 1 | West Vancouver Location Page | plumber west vancouver, hvac west vancouver | To Write |
| Week 1 | Emergency Plumbing Page | emergency plumber north vancouver | To Write |
| Week 2 | Furnace Repair Page | furnace repair north vancouver | To Write |
| Week 2 | Water Heater Installation Page | water heater installation vancouver | To Write |
| Week 2 | Plumbing Pricing Guide | plumber cost vancouver, how much does a plumber cost | To Write |
| Week 3 | Drain Cleaning Page | drain cleaning north vancouver | To Write |
| Week 3 | Gas Line Installation Page | gas line installation vancouver | To Write |
| Week 4 | Burnaby Location Page | plumber burnaby | To Write |
| Week 4 | Heat Pump Maintenance Page | heat pump maintenance vancouver | To Write |
| Week 4 | FAQ Hub Page | (consolidate all FAQ schema) | To Write |

3. Assign responsibility:
   - Beth: WordPress publishing, formatting, images
   - Sean: Technical accuracy review
   - Andrew: Photo selection, GBP posts

4. Share the calendar

**Talking point:** "Velocity matters. Publishing 8-10 pages in a month signals to Google that this site is active and authoritative. One page a month won't move the needle."

---

### 4.2 Quick Backlinks (4 min)

**Goal:** Get 3 supplier testimonials published this week for instant backlinks

**Steps:**

1. Identify suppliers SMR uses:
   - Noble Trade Supply
   - Emco Corporation
   - Wolseley Canada
   - Local HVAC distributors
   - Equipment manufacturers (Lennox, Carrier, Trane, etc.)

2. For each supplier, write a brief testimonial:

**Template:**
```
Subject: Testimonial for your website

Hi [Supplier Name] team,

We've been buying from [Supplier] for [X] years and wanted to share a quick testimonial for your website:

"Noble Trade has been our go-to supplier for plumbing parts in North Vancouver. Their staff knows the products and gets us what we need fast. Highly recommend for any contractor."

- Sean, SMR Plumbing & Heating
www.smrplumbing.ca

Feel free to use this on your website, and if possible, we'd appreciate a link back to smrplumbing.ca.

Thanks!
```

3. Send 3 emails during the session (screen share, have client send from their email)

4. Also consider:
   - Local business associations (North Van Chamber of Commerce)
   - Trade associations (BC Plumbing Association)
   - Manufacturers they're certified with

**Talking point:** "These suppliers have websites with DA 40-60. One link from them is worth more than 50 links from random directories. And they want testimonials."

---

### 4.3 Review Requests (4 min)

**Goal:** Set up a system to get 3-5 new reviews per week

**Steps:**

1. Create a review request template:

**SMS template:**
```
Hi [Name], thanks for choosing SMR Plumbing! If you have a minute, we'd really appreciate a Google review. It helps other North Vancouver homeowners find us. [LINK] - Sean & the SMR team
```

2. Get the direct review link:
   - Go to GBP > Home > "Get more reviews"
   - Copy the short link (looks like: g.page/smrplumbing/review)

3. Set up the process:
   - **Option A:** Use Jobber/Housecall Pro if they have review request feature
   - **Option B:** Manual SMS after each completed job
   - **Option C:** Email follow-up 2 days after job completion

4. Track reviews:
   - Current count: 109
   - Target: 125 by Day 30 (16 new reviews = ~4/week)

**Talking point:** "You're at 109 reviews. Getting to 125 in 30 days is totally doable with a simple text after every job. More reviews = higher local rankings."

---

### 4.4 Tracking Setup (4 min)

**Goal:** Create a simple weekly check routine

**Steps:**

1. Open Google Search Console: https://search.google.com/search-console
2. Show the client:
   - **Performance tab:** Track clicks, impressions, CTR, position
   - **Pages tab:** See which pages are getting traffic
   - **Queries tab:** See what keywords you're ranking for

3. Open Bing Webmaster Tools: https://www.bing.com/webmasters
4. Show similar metrics

5. Create a weekly tracking checklist (share as doc):

**Weekly SEO Check (15 min every Monday):**
- [ ] Check Google Search Console: Total clicks this week vs. last week
- [ ] Check top 10 queries: Any new keywords appearing?
- [ ] Check Google Business Profile: New reviews to respond to?
- [ ] Check GBP Insights: Calls, direction requests, website clicks
- [ ] Check Bing Webmaster: Indexed pages, any errors?
- [ ] Publish 2 new GBP posts

6. Set calendar reminder for Monday morning checks

---

### 4.5 AI Citation Checks (3 min)

**Goal:** Show client how to monitor AI search visibility

**Steps:**

1. Open ChatGPT: https://chat.openai.com
2. Search: "best plumber in north vancouver"
3. Check if SMR appears in the response or sources
4. Note: If not appearing yet, this is expected. Takes time to get indexed.

5. Open Perplexity: https://perplexity.ai
6. Search: "heat pump installation north vancouver"
7. Check citations

6. Open Google and search: "plumber north vancouver"
7. Look for "AI Overview" box at top
8. Check if SMR appears

**Tracking method:**
- Test these 5 queries weekly:
  1. "plumber north vancouver"
  2. "heat pump installation north vancouver"
  3. "furnace repair north vancouver"
  4. "emergency plumber north vancouver"
  5. "best hvac company north vancouver"

- Screenshot any AI citations
- Note date first cited

**Talking point:** "Right now you probably won't show up in AI answers. That's normal. After we get Bing indexed and the new content live, check again in 2-3 weeks. The llms.txt file and structured content will help."

---

## Session Wrap-Up (5 min)

### Recap Completed Items
- [ ] Mobile speed optimized (target: 70+)
- [ ] Address in footer
- [ ] Phone number verified
- [ ] Schema added
- [ ] llms.txt uploaded
- [ ] Bing sitemap submitted
- [ ] 3 new pages published
- [ ] GBP services complete
- [ ] GBP photos uploaded
- [ ] GBP Q&As added
- [ ] 2 GBP posts published
- [ ] Content calendar created
- [ ] 3 supplier testimonial emails sent
- [ ] Review request system set up
- [ ] Tracking routine established

### Homework for Client (Before Session 4)
1. Publish 2 more pages from the content calendar (West Van + Emergency)
2. Respond to every new review within 24 hours
3. Post 2-3x per week on GBP
4. Follow up on supplier testimonials
5. Send review requests after every job
6. Do the Monday tracking check

### Schedule Session 4
- Suggested timing: 2-3 weeks out
- Topic: Review 30-day results + next phase planning

---

## Troubleshooting

### If WordPress Access Doesn't Work
- Have client call Neon Pig during session
- Pivot to Parts 2-4 while waiting
- Can still write content in Claude, just can't publish

### If WP Rocket Isn't Installed
- Alternative plugins: LiteSpeed Cache, W3 Total Cache, Autoptimize
- Configure similar settings
- Or have Neon Pig install WP Rocket

### If Schema Plugin Issues
- Manually add JSON-LD to header
- Use Google Tag Manager as backup
- Or have Neon Pig add to theme

### If GBP Access Issues
- Help client recover access
- May need to verify ownership again
- Can request access from current owner

### If Client Gets Overwhelmed
- Slow down, focus on highest-impact items
- Prioritize: Mobile speed > llms.txt > Bing > One content page > GBP basics
- Save remaining items for homework or Session 4
