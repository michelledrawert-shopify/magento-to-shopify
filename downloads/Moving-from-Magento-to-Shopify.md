# Moving from Magento to Shopify

### Data migration options for Magento and Adobe Commerce stores

October 2026

---

## Five ways to move store data

Shopify documents [five ways to move a store's content](https://help.shopify.com/en/manual/migrating-to-shopify), in order of technical complexity, simplest first:

1. Copying and pasting content, such as policy pages, into the new store  
2. Exporting data to CSV files and importing them into Shopify, which some data types do not support  
3. A migration app from the [Shopify App Store](https://apps.shopify.com/search?q=migrate)  
4. A [Shopify Partner](https://www.shopify.com/partners/directory/services/store-setup/migrate-from-another-platform) who manages the migration  
5. A custom migration built on the [Shopify API](https://shopify.dev/docs/api), in-house or by a partner

Shopify's free [Store Migration app](https://apps.shopify.com/store-migration) imports product and customer data from Square, WooCommerce, Etsy, Wix, Amazon, eBay, Clover and Lightspeed R/X (Vend). Magento is not on that list.

## Matching the route to the store

The best route depends on catalog size, data complexity and technical resources. Shopify's [Magento to Shopify migration guide](https://www.shopify.com/enterprise/blog/magento-to-shopify-migration) pairs each store profile with a route:

| Store profile | Route | When it fits |
| :---- | :---- | :---- |
| Small catalog (under 500 SKUs), simple pricing | Manual or CSV file import | Limited budget, straightforward products, no custom attributes |
| Medium catalog, standard product types | Migration app | Speed without heavy development involvement; standard Magento data structures |
| Large catalog, configurable products, tier pricing | Migration service or agency partner | Complex attribute mappings, customer group pricing, multi-store content |
| Multi-store, B2B pricing, custom ERP integrations | Custom API migration with a partner | Heavy customization, unique data relationships, ERP sync requirements |

Automated does not mean hands-off. Data mappings still need validation before the run, the output needs testing, and the final cutover needs a planned downtime window. A dry run into a development store allows testing and fixes before the live migration.

## What each data type supports

Each data type has its own set of [bulk migration options](https://help.shopify.com/en/manual/migrating-to-shopify).

| Data | Bulk migration options |
| :---- | :---- |
| Products | [Product CSV import](https://help.shopify.com/en/manual/products/import-export/import-products), migration apps |
| Customers | [Customer CSV import](https://help.shopify.com/en/manual/customers/import-export-customers), migration apps, [Customer API](https://shopify.dev/docs/api/admin-graphql/latest/queries/customer) |
| Historical orders | Migration apps, [Order API](https://shopify.dev/docs/api/admin-graphql/latest/queries/order), Transaction API |
| Gift cards, certificates and store credits | Migration apps, [GiftCard API](https://shopify.dev/docs/api/admin-graphql/latest/queries/giftCard) |
| Blogs | Migration apps, [Blog API](https://shopify.dev/docs/api/admin-graphql/latest/queries/blog), [Blog Article API](https://shopify.dev/docs/api/admin-graphql/latest/queries/article) |
| Pages (shipping policy, contact and other pages) | Migration apps, [Page API](https://shopify.dev/docs/api/admin-graphql/latest/queries/page) |

Import order matters. Products come first, then customers, then historical orders, so that each order connects to the right products and customers. Staff set to receive new order notifications get an email for each imported historical order unless those notifications are [deactivated](https://help.shopify.com/en/manual/fulfillment/setup/notifications/staff-notifications#adjust-new-order-notifications) for the import.

## Magento data that needs a plan

Some Magento data has [no direct Shopify equivalent](https://www.shopify.com/enterprise/blog/magento-to-shopify-migration):

- **Customer passwords** cannot be migrated in a usable format. The alternative is account activation emails or password reset prompts after launch.  
- **Configurable products** map to Shopify variants, though complex configurations may need manual review.  
- **Custom attributes** become Shopify metafields, mapped before migration rather than after.  
- **Tier pricing and customer group pricing** in heavy use calls for a review of whether Shopify's [B2B features](https://help.shopify.com/en/manual/b2b) cover the requirement. B2B is available on the Basic, Grow, Advanced and Shopify Plus plans, and the capabilities vary by plan.  
- **CMS blocks and widgets** have no direct parallel; key content is rebuilt natively in Shopify.  
- **URLs** in Magento often carry .html extensions and category paths, while Shopify uses a flat structure such as /products/product-handle. Every indexed URL needs a 301 redirect.  
- **Faceted filtering** by attribute works differently from Shopify's collection filtering, so filterable attributes need a translation plan.

## Migration apps that list Magento

Each app below names Magento as a supported source on its Shopify App Store listing. Listed alphabetically.

| App and developer | Data covered | Listed pricing (USD) | Rating |
| :---- | :---- | :---- | :---- |
| [Cart2Cart Store Migration](https://apps.shopify.com/cart2cart-shopify-migration-module), Cart2Cart | Products, customers, orders, categories and more; Magento named as supported | Free to install; fees based on store size, entities migrated and migration options | 4.2 (169 reviews) |
| [Matrixify: Data Export Import](https://apps.shopify.com/excel-export-import), ITissible | Products, collections, customers, B2B companies, discounts, orders, pages, blogs, redirects, metafields and more; Magento named as a migration source | Demo free; Basic \$20/month; Big \$50/month; Enterprise \$200/month; limits apply per file by plan | 4.9 (1,788 reviews) |
| [Migrate Go: Import & Export](https://apps.shopify.com/migratly), MigrateGO | Products, customers, orders, SEO data, URLs, 301 redirects; Magento named as supported | Free plan (up to 25 items per entity); Lite \$14.99/month; Growth \$34.99/month; Business \$49.99/month; API migration is an optional upgrade | 4.8 (23 reviews) |
| [Next-Cart Store Migration](https://apps.shopify.com/nextcart-store-migration), Next-Cart | Products, categories, customers, reviews, orders, coupons, blogs, pages, SEO metadata, URLs; Magento named as supported | Demo free (50 of each); Basic \$150/month (up to 10,000 of each); Standard \$350/month (50,000); Advanced \$550/month (100,000) | 4.8 (25 reviews) |
| [StoreCopy](https://apps.shopify.com/skemify-wix-store-migration), StoreCopy | Products, variants, inventory, collections, customers, discounts, orders, reviews (Yotpo); Magento named as supported; 6 months of support after migration | First 100 entities free; priced by number of entities, starting at \$24 | 5.0 (2 reviews) |
| [Vostari CSV Converter: Magento](https://apps.shopify.com/csv-converting-magento), Vostari | Reformats Magento CSV exports for Shopify's CSV import: products, inventory, customer data | Pay as you go; \$5.00 minimum fee; first conversion free; customer data conversion free | No reviews yet |

Cart2Cart also publishes a Magento-specific listing, [Import from Magento](https://apps.shopify.com/cart2cart-magento-importer), priced by the number of entities migrated and the options selected.

\*Fine print: App details are as published by each developer on its Shopify App Store listing, retrieved October 21, 2026\. The capabilities described have not been independently tested. Pricing, plans, features and ratings change over time, and some developers note that charges may be billed separately from the Shopify invoice.\*

## Working with a partner

The [Shopify Partner Directory](https://www.shopify.com/partners/directory/services/store-setup/migrate-from-another-platform) has a store migration category, filterable by location, partner tier, industry and price range.

Factors that typically point to a [dedicated migration service](https://www.shopify.com/enterprise/blog/shopify-plus-data-migration-service):

- High SKU counts with complex variants  
- Multiple markets, currencies or storefronts  
- ERP, OMS, WMS or PIM dependencies  
- Subscription, loyalty or returns workflows  
- Regulatory and security requirements

Starting-point deliverables for a Shopify Plus [migration statement of work](https://www.shopify.com/enterprise/blog/shopify-plus-data-migration-service):

- Discovery and data audit  
- Data mapping document, with transformation rules for fields that need restructuring  
- At least two migration runs (staging and production), each with documented results  
- QA plan: automated validation checks, a manual sampling protocol and business sign-off criteria  
- Cutover plan: data freeze windows, DNS changes and integration switchovers  
- Rollback plan for critical issues during cutover  
- SEO deliverables: 301 redirect map, canonical URL strategy, metadata mapping and post-launch crawl verification  
- Training on the migrated data in the Shopify admin  
- A post-launch support window, typically 2 to 4 weeks

## Custom builds

The GraphQL Admin API [supports bulk imports](https://shopify.dev/docs/apps/build/apis/graphql-admin/bulk-operations/imports). Mutation inputs go into a JSONL file, one input per line. The file is uploaded through the [stagedUploadsCreate](https://shopify.dev/docs/api/admin-graphql/latest/mutations/stagedUploadsCreate) mutation and run with [bulkOperationRunMutation](https://shopify.dev/docs/api/admin-graphql/latest/mutations/bulkOperationRunMutation) as a single asynchronous operation, and the results come back as a JSONL file. The mutation runs once for each line of the input file.

Limits to plan around, from the [bulk imports documentation](https://shopify.dev/docs/apps/build/apis/graphql-admin/bulk-operations/imports):

- The JSONL file can't exceed 100 MB.  
- An operation must finish within 24 hours, or it is stopped and marked failed.  
- Lines are not processed in order, so an import shouldn't depend on line sequence.  
- Errors are reported per line in the results file. The whole operation is marked failed only for critical system errors.  
- From API version 2026-01, up to five bulk mutation operations can run per shop at once.  
- Result file URLs expire after one week.  
