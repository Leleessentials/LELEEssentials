# LÈLE ESSENTIALS CO. — Website ready for GitHub Pages

A luxury, mobile-responsive **general product storefront**, currently featuring three LAIKOU products. No build tools or private hosting required. Customers assemble a cart, provide delivery details, and open a prefilled WhatsApp order addressed to **+880 1729-228117**. They must press **Send** in WhatsApp for your team to receive it; your team confirms price, availability, address, COD amount and dispatch manually.

## Upload to your existing GitHub repository

1. Download and unzip this package.
2. In your existing `lele-essentials` GitHub repository, upload **the contents of this folder** to the **repository root**. Do not upload the ZIP as one file and do not put the contents inside another `lele-essentials-final` subfolder. Replace any old files with the same names.
3. Confirm that `index.html`, `styles.css`, `app.js`, `.nojekyll`, `assets/`, and `products/` are at the root.
4. Go to **Settings → Pages** and choose **GitHub Actions** if using your existing successful `static.yml` workflow. That workflow must publish the repository root (`path: '.'`). Commit changes and wait for a green deployment run.
5. Visit `https://genzahnaf2009-hub.github.io/lele-essentials/` and hard-refresh (Ctrl+Shift+R).

**Important:** No back-end is required for this *manual WhatsApp order request* workflow. This website cannot silently/automatically send a message to WhatsApp, and it cannot charge a customer. Orders arrive **only after the customer presses Send in WhatsApp**. No online payment is collected; COD is coordinated by your team or courier.

## Current products / dedicated pages

- Sakura five-piece set: `products/sakura-set.html`
- Sakura mud mask (5 g): `products/sakura-mask.html`
- Matcha mud mask (5 g): `products/matcha-mask.html`

The user-provided product photographs are in `assets/`. The set contains a cleanser (50 g), toner (100 ml), serum (17 ml), eye cream (15 g), and essence cream (25 g), as reported by independent retailers. Product packaging and third-party descriptions are not proof of skincare efficacy or exact ingredients; always check the physical label.

## Set the three selling prices

Open **`app.js`**, find the `PRODUCTS` array near the top and change the three `price:null` values to actual selling prices in **BDT**. Example: `price:450` (displays `৳450`). `null` means **Price on request**; nothing is fabricated. Confirm delivery charges over WhatsApp since no fee was provided. Keep the exact product prices in sync with what your team quotes.

## Add a new product later (without hiring a developer)

1. Put its photo in `assets/`, e.g. `new-product.webp`. Use a high-quality image you have permission to publish.
2. Copy an existing object in the `PRODUCTS` array of `app.js`; update `id`, `slug`, `name`, `label`, `brand`, `category`, `size`, `image`, `price`, `badge`, `tone`, `short`, `intro`, `includes`, `highlights`, `directions`, `notes`. **IDs and slugs must be unique.**
3. The collection automatically displays the new product. Product cards automatically link to `products/item.html?id=YOUR-ID` for products other than the first three. Each new product therefore has its own shareable detail URL without creating more HTML pages.
4. To hide/remove a product, remove its object from `PRODUCTS`; you may also delete its unused image. Past customers' saved carts automatically drop removed items.
5. To add a new category filter, add a matching button in `index.html` under `id="filters"` with `data-filter="YOUR CATEGORY"`.
6. Commit; GitHub Actions redeploys the site.

## WhatsApp details / contacts

- Order destination in `app.js`: `whatsapp:'8801729228117'`
- Secondary public phone: `+8801970155970`
- Buyer name, Bangladesh mobile, email, division, district, address, items, quantities and notes are included in the **prefilled** WhatsApp message.
- Your private email address is **not** in the website source, and **no email** is sent or received by this static site.
- The shopper's contact information is used to prepare the WhatsApp message on their device; it is not saved to a store database.

## Connect your own domain

1. Purchase/manage your custom domain (e.g. `www.yourdomain.com`). Do not add a `CNAME` file until you know the exact domain.
2. In GitHub repository **Settings → Pages → Custom domain**, enter the domain and save.
3. Configure DNS at your domain registrar following GitHub's current Pages instructions: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site . For `www`, configure a `CNAME` record pointing to `genzahnaf2009-hub.github.io`. For an apex/root domain, use the current GitHub Pages A/AAAA records from those instructions rather than guessing IPs.
4. After DNS propagates and the HTTPS certificate is issued, enable **Enforce HTTPS** in the Pages settings. Test root and `www` redirects.
5. Do not create a `CNAME` file in GitHub with an example address; it can break the site.

## Safety / limitations

- GitHub Pages cannot safely provide an owner-password/admin portal, real-time inventory, an order database, automatic WhatsApp sending, automatic email confirmations, or a sales dashboard without an external backend.
- WhatsApp opens a new tab. If the browser blocks it, the checkout shows a clickable fallback link.
- Pricing and stock are not server-validated. Your team must confirm final payable total, delivery charge, address and stock before courier dispatch.
- This is **not** a Shopify theme; it's a static HTML, CSS and JavaScript storefront.
- Before announcing the store publicly: fill actual prices, review product information and claims, test on Android/iPhone, verify your WhatsApp number, check courier service and delivery/returns policy, test your custom domain and HTTPS, and place an end-to-end test order.
