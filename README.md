# My Khata  (all files in ONE folder, no sub-folders)

## Website files (upload to GitHub Pages)
index.html, store.html, community.html, script.js, cloud.js, config.js, admin.html, manifest.json, service-worker.js, icon.svg
Keep your existing icon-192.png, icon-512.png, icon-maskable-512.png, qr.png next to them.

## What changed in this version
- **AI removed completely** (ai.js and all training files deleted, no AI code left in the app).
- **Ads are commented out.** Nothing opens them (no Ads tab, no Ads settings, no app-open popup, adsense.js not loaded).
  The ad code is still in script.js. To turn ads back on, search for `ADS-DISABLED` in script.js and service-worker.js and remove those comment marks.
- **Buy check / Sell check** (Settings > Business), each has its own ON / OFF:
  - Sell check: you can only sell what is in stock.
  - Buy check: buying stock needs enough cash in hand.
- **Inventory** starts with 5 products at quantity 0 (Rice, Sugar, Cooking Oil, Tea, Flour) for a new shop, or an existing shop with empty inventory.
- **Product pictures are links only.** Add / Edit stock has a "Picture link" box (must start with https://). Without a link, a small emoji / first letter is shown.
  Pictures show in Inventory, the product picker, customer entries, and in Profit > "Sold Items" and "Recent Sales" so you can see what customers bought.
- **Online store**: Settings > Online Store. Customers open `store.html?s=<your link name>`, see products with pictures, and send an order.

## Online store setup (one time)
1. Supabase Dashboard > SQL Editor > paste the whole `store_setup.sql` > Run.
2. In the app: Settings > Online Store > turn ON, then open "Store link & WhatsApp" to choose your link name.
3. Share the link. Orders appear in Settings > Online Store > Store orders (needs internet).
Prices come from your Sell Rate. Products with no sell rate or with 0 stock cannot be ordered. The store updates by itself a few seconds after you change stock.
When you hand over an order, add the sale in the customer khata so stock and profit are updated.

## Community (new)
Open from Settings > Online Store > Community. Uses the same login as the app.
- Feed: anyone can post a message or code (HTML / CSS / JS). Long messages and long code are shortened with Show more. Copy, Save, Message and Delete (own posts) on every post.
- Stores: list of all online stores with city, product count and star rating. Open store, Rate (1 to 5 + review), Reviews, and private Chat with the owner.
- Chats: private one-to-one messages. Saved: your saved posts.
- Store profile: Settings > Online Store > Store link & WhatsApp now also has City and About, which show in the Stores list.
Setup (one time, after store_setup.sql): Supabase > SQL Editor > run `community_setup.sql`.

## Store (new look)
- `store.html` = customer store AND your admin store (same page). In the app tap the **Store** icon (top bar) or Settings > Online Store > Open my store.
- Admin can: turn store ON/OFF, accept orders, home delivery ON/OFF, pickup, fee, free-delivery limit, hours, min order, max per item, pay methods, discount code, **own rules** (customers can be forced to agree), colour, card size, edit each product (price, category, text, hide), and see/handle orders.
- Customers can change mode (light/dark/auto), colour, card size and pictures on/off for themselves.
- Files: store.html, community.html, owner.html, admin.html, theme.js, khicons.js (icons), shop-ui.css (shared look).
