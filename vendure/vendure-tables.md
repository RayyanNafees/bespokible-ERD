# Vendure ERD

```mermaid
erDiagram
	collection_asset }o--|| asset : references
	collection }o--|| asset : references
	facet_translation }o--|| facet : references
	facet_value }o--|| facet : references
	product_asset }o--|| asset : references
	product }o--|| asset : references
	order_line_reference }o--|| fulfillment : references
	order_modification }o--|| payment : references
	order_modification }o--|| refund : references
	promotion_translation }o--|| promotion : references
	shipping_method_translation }o--|| shipping_method : references
	shipping_line }o--|| shipping_method : references
	stock_movement }o--|| stock_location : references
	order_line }o--|| shipping_line : references
	order_line }o--|| tax_category : references
	order_line }o--|| asset : references
	order_line }o--|| order : references
	stock_level }o--|| stock_location : references
	product_variant_asset }o--|| asset : references
	product_variant }o--|| asset : references
	product_variant }o--|| tax_category : references
	product_variant }o--|| product : references
	tax_rate }o--|| tax_category : references
	tax_rate }o--|| zone : references
	tax_rate }o--|| customer_group : references
	authentication_method }o--|| user : references
	session }o--|| order : references
	session }o--|| user : references
	customer }o--|| user : references
	address }o--|| customer : references
	address }o--|| region : references
	administrator }o--|| user : references
	payment_method_translation }o--|| payment_method : references
	channel }o--|| seller : references
	channel }o--|| zone : references
	channel }o--|| zone : references
	history_entry }o--|| administrator : references
	history_entry }o--|| customer : references
	history_entry }o--|| order : references
	collection_product_variants_product_variant }o--|| collection : references
	collection_product_variants_product_variant }o--|| product_variant : references
	collection_channels_channel }o--|| collection : references
	collection_channels_channel }o--|| channel : references
	facet_channels_channel }o--|| facet : references
	facet_channels_channel }o--|| channel : references
	facet_value_channels_channel }o--|| facet_value : references
	facet_value_channels_channel }o--|| channel : references
	product_facet_values_facet_value }o--|| product : references
	product_facet_values_facet_value }o--|| facet_value : references
	product_channels_channel }o--|| product : references
	product_channels_channel }o--|| channel : references
	asset_tags_tag }o--|| asset : references
	asset_tags_tag }o--|| tag : references
	asset_channels_channel }o--|| asset : references
	asset_channels_channel }o--|| channel : references
	promotion_channels_channel }o--|| promotion : references
	promotion_channels_channel }o--|| channel : references
	shipping_method_channels_channel }o--|| shipping_method : references
	shipping_method_channels_channel }o--|| channel : references
	order_promotions_promotion }o--|| order : references
	order_promotions_promotion }o--|| promotion : references
	order_fulfillments_fulfillment }o--|| order : references
	order_fulfillments_fulfillment }o--|| fulfillment : references
	order_channels_channel }o--|| order : references
	order_channels_channel }o--|| channel : references
	stock_location_channels_channel }o--|| stock_location : references
	stock_location_channels_channel }o--|| channel : references
	product_variant_options_product_option }o--|| product_variant : references
	product_variant_options_product_option }o--|| product_option : references
	product_variant_facet_values_facet_value }o--|| product_variant : references
	product_variant_facet_values_facet_value }o--|| facet_value : references
	product_variant_channels_channel }o--|| product_variant : references
	product_variant_channels_channel }o--|| channel : references
	zone_members_region }o--|| zone : references
	zone_members_region }o--|| region : references
	role_channels_channel }o--|| role : references
	role_channels_channel }o--|| channel : references
	user_roles_role }o--|| user : references
	user_roles_role }o--|| role : references
	customer_groups_customer_group }o--|| customer : references
	customer_groups_customer_group }o--|| customer_group : references
	customer_channels_channel }o--|| customer : references
	customer_channels_channel }o--|| channel : references
	payment_method_channels_channel }o--|| payment_method : references
	payment_method_channels_channel }o--|| channel : references
	collection_closure }o--|| collection : references
	collection_closure }o--|| collection : references

	facet {
		DATETIME createdAt
		DATETIME updatedAt
		BOOLEAN isPrivate
		VARCHAR code
		INTEGER id
	}

	tag {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR value
		INTEGER id
	}

	asset {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR name
		VARCHAR type
		VARCHAR mimeType
		INTEGER width
		INTEGER height
		INTEGER fileSize
		VARCHAR source
		VARCHAR preview
		TEXT focalPoint
		INTEGER id
	}

	fulfillment {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR state
		VARCHAR trackingCode
		VARCHAR method
		VARCHAR handlerCode
		INTEGER id
	}

	promotion {
		DATETIME createdAt
		DATETIME updatedAt
		DATETIME deletedAt
		DATETIME startsAt
		DATETIME endsAt
		VARCHAR couponCode
		INTEGER perCustomerUsageLimit
		INTEGER usageLimit
		BOOLEAN enabled
		TEXT conditions
		TEXT actions
		INTEGER priorityScore
		INTEGER id
	}

	shipping_method {
		DATETIME createdAt
		DATETIME updatedAt
		DATETIME deletedAt
		VARCHAR code
		TEXT checker
		TEXT calculator
		VARCHAR fulfillmentHandlerCode
		INTEGER id
	}

	stock_location {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR name
		VARCHAR description
		INTEGER id
	}

	tax_category {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR name
		BOOLEAN isDefault
		INTEGER id
	}

	zone {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR name
		INTEGER id
	}

	customer_group {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR name
		INTEGER id
	}

	role {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR code
		VARCHAR description
		TEXT permissions
		INTEGER id
	}

	user {
		DATETIME createdAt
		DATETIME updatedAt
		DATETIME deletedAt
		VARCHAR identifier
		BOOLEAN verified
		DATETIME lastLogin
		INTEGER id
	}

	global_settings {
		DATETIME createdAt
		DATETIME updatedAt
		TEXT availableLanguages
		BOOLEAN trackInventory
		INTEGER outOfStockThreshold
		INTEGER id
	}

	payment_method {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR code
		BOOLEAN enabled
		TEXT checker
		TEXT handler
		INTEGER id
	}

	seller {
		DATETIME createdAt
		DATETIME updatedAt
		DATETIME deletedAt
		VARCHAR name
		INTEGER id
	}

	settings_store_entry {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR key
		BLOB value
		VARCHAR scope
		INTEGER id
	}

	job_record {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR queueName
		TEXT data
		VARCHAR state
		INTEGER progress
		TEXT result
		VARCHAR error
		DATETIME startedAt
		DATETIME settledAt
		BOOLEAN isSettled
		INTEGER retries
		INTEGER attempts
		INTEGER id
	}

	job_record_buffer {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR bufferId
		TEXT job
		INTEGER id
	}

	scheduled_task_record {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR taskId
		BOOLEAN enabled
		DATETIME lockedAt
		DATETIME lastExecutedAt
		DATETIME manuallyTriggeredAt
		BLOB lastResult
		INTEGER id
	}

	search_index_item {
		VARCHAR languageCode
		BOOLEAN enabled
		VARCHAR productName
		VARCHAR productVariantName
		TEXT description
		VARCHAR slug
		VARCHAR sku
		TEXT facetIds
		TEXT facetValueIds
		TEXT collectionIds
		TEXT collectionSlugs
		TEXT channelIds
		VARCHAR productPreview
		TEXT productPreviewFocalPoint
		VARCHAR productVariantPreview
		TEXT productVariantPreviewFocalPoint
		BOOLEAN inStock
		BOOLEAN productInStock
		INTEGER productVariantId
		INTEGER channelId
		INTEGER productId
		INTEGER productAssetId
		INTEGER productVariantAssetId
		INTEGER price
		INTEGER priceWithTax
	}

	collection_asset {
		DATETIME createdAt
		DATETIME updatedAt
		INTEGER assetId
		INTEGER position
		INTEGER collectionId
		INTEGER id
	}

	collection_translation {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR languageCode
		VARCHAR name
		VARCHAR slug
		TEXT description
		INTEGER id
		INTEGER baseId
	}

	collection {
		DATETIME createdAt
		DATETIME updatedAt
		BOOLEAN isRoot
		INTEGER position
		BOOLEAN isPrivate
		TEXT filters
		BOOLEAN inheritFilters
		INTEGER id
		INTEGER parentId
		INTEGER featuredAssetId
	}

	facet_translation {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR languageCode
		VARCHAR name
		INTEGER id
		INTEGER baseId
	}

	facet_value_translation {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR languageCode
		VARCHAR name
		INTEGER id
		INTEGER baseId
	}

	facet_value {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR code
		INTEGER id
		INTEGER facetId
	}

	product_option_translation {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR languageCode
		VARCHAR name
		INTEGER id
		INTEGER baseId
	}

	product_option {
		DATETIME createdAt
		DATETIME updatedAt
		DATETIME deletedAt
		VARCHAR code
		INTEGER id
		INTEGER groupId
	}

	product_option_group_translation {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR languageCode
		VARCHAR name
		INTEGER id
		INTEGER baseId
	}

	product_option_group {
		DATETIME createdAt
		DATETIME updatedAt
		DATETIME deletedAt
		VARCHAR code
		INTEGER id
		INTEGER productId
	}

	product_asset {
		DATETIME createdAt
		DATETIME updatedAt
		INTEGER assetId
		INTEGER position
		INTEGER productId
		INTEGER id
	}

	product_translation {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR languageCode
		VARCHAR name
		VARCHAR slug
		TEXT description
		INTEGER id
		INTEGER baseId
	}

	product {
		DATETIME createdAt
		DATETIME updatedAt
		DATETIME deletedAt
		BOOLEAN enabled
		INTEGER id
		INTEGER featuredAssetId
	}

	order_line_reference {
		DATETIME createdAt
		DATETIME updatedAt
		INTEGER quantity
		INTEGER id
		INTEGER fulfillmentId
		INTEGER modificationId
		INTEGER orderLineId
		INTEGER refundId
		VARCHAR discriminator
	}

	refund {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR method
		VARCHAR reason
		VARCHAR state
		VARCHAR transactionId
		TEXT metadata
		INTEGER id
		INTEGER paymentId
		INTEGER items
		INTEGER shipping
		INTEGER adjustment
		INTEGER total
	}

	payment {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR method
		VARCHAR state
		VARCHAR errorMessage
		VARCHAR transactionId
		TEXT metadata
		INTEGER id
		INTEGER amount
		INTEGER orderId
	}

	surcharge {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR description
		BOOLEAN listPriceIncludesTax
		VARCHAR sku
		TEXT taxLines
		INTEGER id
		INTEGER listPrice
		INTEGER orderId
		INTEGER orderModificationId
	}

	order_modification {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR note
		TEXT shippingAddressChange
		TEXT billingAddressChange
		INTEGER id
		INTEGER priceChange
		INTEGER orderId
		INTEGER paymentId
		INTEGER refundId
	}

	promotion_translation {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR languageCode
		VARCHAR name
		TEXT description
		INTEGER id
		INTEGER baseId
	}

	shipping_method_translation {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR languageCode
		VARCHAR name
		VARCHAR description
		INTEGER id
		INTEGER baseId
	}

	shipping_line {
		DATETIME createdAt
		DATETIME updatedAt
		BOOLEAN listPriceIncludesTax
		TEXT adjustments
		TEXT taxLines
		INTEGER id
		INTEGER shippingMethodId
		INTEGER listPrice
		INTEGER orderId
	}

	order {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR type
		VARCHAR code
		VARCHAR state
		BOOLEAN active
		DATETIME orderPlacedAt
		TEXT couponCodes
		TEXT shippingAddress
		TEXT billingAddress
		VARCHAR currencyCode
		INTEGER id
		INTEGER aggregateOrderId
		INTEGER customerId
		INTEGER taxZoneId
		INTEGER subTotal
		INTEGER subTotalWithTax
		INTEGER shipping
		INTEGER shippingWithTax
	}

	stock_movement {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR type
		INTEGER quantity
		INTEGER id
		INTEGER stockLocationId
		VARCHAR discriminator
		INTEGER productVariantId
		INTEGER orderLineId
	}

	order_line {
		DATETIME createdAt
		DATETIME updatedAt
		INTEGER quantity
		INTEGER orderPlacedQuantity
		BOOLEAN listPriceIncludesTax
		TEXT adjustments
		TEXT taxLines
		INTEGER id
		INTEGER sellerChannelId
		INTEGER shippingLineId
		INTEGER productVariantId
		INTEGER taxCategoryId
		INTEGER initialListPrice
		INTEGER listPrice
		INTEGER featuredAssetId
		INTEGER orderId
	}

	stock_level {
		DATETIME createdAt
		DATETIME updatedAt
		INTEGER stockOnHand
		INTEGER stockAllocated
		INTEGER id
		INTEGER productVariantId
		INTEGER stockLocationId
	}

	product_variant_asset {
		DATETIME createdAt
		DATETIME updatedAt
		INTEGER assetId
		INTEGER position
		INTEGER productVariantId
		INTEGER id
	}

	product_variant_price {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR currencyCode
		INTEGER id
		INTEGER channelId
		INTEGER price
		INTEGER variantId
	}

	product_variant_translation {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR languageCode
		VARCHAR name
		INTEGER id
		INTEGER baseId
	}

	product_variant {
		DATETIME createdAt
		DATETIME updatedAt
		DATETIME deletedAt
		BOOLEAN enabled
		VARCHAR sku
		INTEGER outOfStockThreshold
		BOOLEAN useGlobalOutOfStockThreshold
		VARCHAR trackInventory
		INTEGER id
		INTEGER featuredAssetId
		INTEGER taxCategoryId
		INTEGER productId
	}

	region_translation {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR languageCode
		VARCHAR name
		INTEGER id
		INTEGER baseId
	}

	region {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR code
		VARCHAR type
		BOOLEAN enabled
		INTEGER id
		INTEGER parentId
		VARCHAR discriminator
	}

	tax_rate {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR name
		BOOLEAN enabled
		BLOB value
		INTEGER id
		INTEGER categoryId
		INTEGER zoneId
		INTEGER customerGroupId
	}

	authentication_method {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR identifier
		VARCHAR passwordHash
		VARCHAR verificationToken
		VARCHAR passwordResetToken
		VARCHAR identifierChangeToken
		VARCHAR pendingIdentifier
		VARCHAR strategy
		VARCHAR externalIdentifier
		TEXT metadata
		INTEGER id
		VARCHAR type
		INTEGER userId
	}

	session {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR token
		DATETIME expires
		BOOLEAN invalidated
		VARCHAR authenticationStrategy
		INTEGER id
		INTEGER activeOrderId
		INTEGER activeChannelId
		VARCHAR type
		INTEGER userId
	}

	customer {
		DATETIME createdAt
		DATETIME updatedAt
		DATETIME deletedAt
		VARCHAR title
		VARCHAR firstName
		VARCHAR lastName
		VARCHAR phoneNumber
		VARCHAR emailAddress
		INTEGER id
		INTEGER userId
	}

	address {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR fullName
		VARCHAR company
		VARCHAR streetLine1
		VARCHAR streetLine2
		VARCHAR city
		VARCHAR province
		VARCHAR postalCode
		VARCHAR phoneNumber
		BOOLEAN defaultShippingAddress
		BOOLEAN defaultBillingAddress
		INTEGER id
		INTEGER customerId
		INTEGER countryId
	}

	administrator {
		DATETIME createdAt
		DATETIME updatedAt
		DATETIME deletedAt
		VARCHAR firstName
		VARCHAR lastName
		VARCHAR emailAddress
		INTEGER id
		INTEGER userId
	}

	payment_method_translation {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR languageCode
		VARCHAR name
		TEXT description
		INTEGER id
		INTEGER baseId
	}

	channel {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR code
		VARCHAR token
		VARCHAR description
		VARCHAR defaultLanguageCode
		TEXT availableLanguageCodes
		VARCHAR defaultCurrencyCode
		TEXT availableCurrencyCodes
		BOOLEAN trackInventory
		INTEGER outOfStockThreshold
		BOOLEAN pricesIncludeTax
		INTEGER id
		INTEGER sellerId
		INTEGER defaultTaxZoneId
		INTEGER defaultShippingZoneId
	}

	history_entry {
		DATETIME createdAt
		DATETIME updatedAt
		VARCHAR type
		BOOLEAN isPublic
		TEXT data
		INTEGER id
		VARCHAR discriminator
		INTEGER administratorId
		INTEGER customerId
		INTEGER orderId
	}

	collection_product_variants_product_variant {
		INTEGER collectionId
		INTEGER productVariantId
	}

	collection_channels_channel {
		INTEGER collectionId
		INTEGER channelId
	}

	facet_channels_channel {
		INTEGER facetId
		INTEGER channelId
	}

	facet_value_channels_channel {
		INTEGER facetValueId
		INTEGER channelId
	}

	product_facet_values_facet_value {
		INTEGER productId
		INTEGER facetValueId
	}

	product_channels_channel {
		INTEGER productId
		INTEGER channelId
	}

	asset_tags_tag {
		INTEGER assetId
		INTEGER tagId
	}

	asset_channels_channel {
		INTEGER assetId
		INTEGER channelId
	}

	promotion_channels_channel {
		INTEGER promotionId
		INTEGER channelId
	}

	shipping_method_channels_channel {
		INTEGER shippingMethodId
		INTEGER channelId
	}

	order_promotions_promotion {
		INTEGER orderId
		INTEGER promotionId
	}

	order_fulfillments_fulfillment {
		INTEGER orderId
		INTEGER fulfillmentId
	}

	order_channels_channel {
		INTEGER orderId
		INTEGER channelId
	}

	stock_location_channels_channel {
		INTEGER stockLocationId
		INTEGER channelId
	}

	product_variant_options_product_option {
		INTEGER productVariantId
		INTEGER productOptionId
	}

	product_variant_facet_values_facet_value {
		INTEGER productVariantId
		INTEGER facetValueId
	}

	product_variant_channels_channel {
		INTEGER productVariantId
		INTEGER channelId
	}

	zone_members_region {
		INTEGER zoneId
		INTEGER regionId
	}

	role_channels_channel {
		INTEGER roleId
		INTEGER channelId
	}

	user_roles_role {
		INTEGER userId
		INTEGER roleId
	}

	customer_groups_customer_group {
		INTEGER customerId
		INTEGER customerGroupId
	}

	customer_channels_channel {
		INTEGER customerId
		INTEGER channelId
	}

	payment_method_channels_channel {
		INTEGER paymentMethodId
		INTEGER channelId
	}

	collection_closure {
		INTEGER id_ancestor
		INTEGER id_descendant
	}

	migrations {
		INTEGER id
		INTEGER timestamp
		VARCHAR name
	}
```

- [Introduction](#introduction)
- [Database Type](#database-type)
- [Table Structure](#table-structure)
	- [facet](#facet)
	- [tag](#tag)
	- [asset](#asset)
	- [fulfillment](#fulfillment)
	- [promotion](#promotion)
	- [shipping_method](#shipping_method)
	- [stock_location](#stock_location)
	- [tax_category](#tax_category)
	- [zone](#zone)
	- [customer_group](#customer_group)
	- [role](#role)
	- [user](#user)
	- [global_settings](#global_settings)
	- [payment_method](#payment_method)
	- [seller](#seller)
	- [settings_store_entry](#settings_store_entry)
	- [job_record](#job_record)
	- [job_record_buffer](#job_record_buffer)
	- [scheduled_task_record](#scheduled_task_record)
	- [search_index_item](#search_index_item)
	- [collection_asset](#collection_asset)
	- [collection_translation](#collection_translation)
	- [collection](#collection)
	- [facet_translation](#facet_translation)
	- [facet_value_translation](#facet_value_translation)
	- [facet_value](#facet_value)
	- [product_option_translation](#product_option_translation)
	- [product_option](#product_option)
	- [product_option_group_translation](#product_option_group_translation)
	- [product_option_group](#product_option_group)
	- [product_asset](#product_asset)
	- [product_translation](#product_translation)
	- [product](#product)
	- [order_line_reference](#order_line_reference)
	- [refund](#refund)
	- [payment](#payment)
	- [surcharge](#surcharge)
	- [order_modification](#order_modification)
	- [promotion_translation](#promotion_translation)
	- [shipping_method_translation](#shipping_method_translation)
	- [shipping_line](#shipping_line)
	- [order](#order)
	- [stock_movement](#stock_movement)
	- [order_line](#order_line)
	- [stock_level](#stock_level)
	- [product_variant_asset](#product_variant_asset)
	- [product_variant_price](#product_variant_price)
	- [product_variant_translation](#product_variant_translation)
	- [product_variant](#product_variant)
	- [region_translation](#region_translation)
	- [region](#region)
	- [tax_rate](#tax_rate)
	- [authentication_method](#authentication_method)
	- [session](#session)
	- [customer](#customer)
	- [address](#address)
	- [administrator](#administrator)
	- [payment_method_translation](#payment_method_translation)
	- [channel](#channel)
	- [history_entry](#history_entry)
	- [collection_product_variants_product_variant](#collection_product_variants_product_variant)
	- [collection_channels_channel](#collection_channels_channel)
	- [facet_channels_channel](#facet_channels_channel)
	- [facet_value_channels_channel](#facet_value_channels_channel)
	- [product_facet_values_facet_value](#product_facet_values_facet_value)
	- [product_channels_channel](#product_channels_channel)
	- [asset_tags_tag](#asset_tags_tag)
	- [asset_channels_channel](#asset_channels_channel)
	- [promotion_channels_channel](#promotion_channels_channel)
	- [shipping_method_channels_channel](#shipping_method_channels_channel)
	- [order_promotions_promotion](#order_promotions_promotion)
	- [order_fulfillments_fulfillment](#order_fulfillments_fulfillment)
	- [order_channels_channel](#order_channels_channel)
	- [stock_location_channels_channel](#stock_location_channels_channel)
	- [product_variant_options_product_option](#product_variant_options_product_option)
	- [product_variant_facet_values_facet_value](#product_variant_facet_values_facet_value)
	- [product_variant_channels_channel](#product_variant_channels_channel)
	- [zone_members_region](#zone_members_region)
	- [role_channels_channel](#role_channels_channel)
	- [user_roles_role](#user_roles_role)
	- [customer_groups_customer_group](#customer_groups_customer_group)
	- [customer_channels_channel](#customer_channels_channel)
	- [payment_method_channels_channel](#payment_method_channels_channel)
	- [collection_closure](#collection_closure)
	- [migrations](#migrations)
- [Relationships](#relationships)
- [Database Diagram](#database-diagram)

## Introduction

## Database type

- **Database system:** SQLite
## Table structure

### facet

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **isPrivate** | BOOLEAN | not null, default: 0 |  | |
| **code** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### tag

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **value** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### asset

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **name** | VARCHAR | not null |  | |
| **type** | VARCHAR | not null |  | |
| **mimeType** | VARCHAR | not null |  | |
| **width** | INTEGER | not null, default: 0 |  | |
| **height** | INTEGER | not null, default: 0 |  | |
| **fileSize** | INTEGER | not null |  | |
| **source** | VARCHAR | not null |  | |
| **preview** | VARCHAR | not null |  | |
| **focalPoint** | TEXT | null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### fulfillment

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **state** | VARCHAR | not null |  | |
| **trackingCode** | VARCHAR | not null |  | |
| **method** | VARCHAR | not null |  | |
| **handlerCode** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### promotion

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **deletedAt** | DATETIME | null |  | |
| **startsAt** | DATETIME | null |  | |
| **endsAt** | DATETIME | null |  | |
| **couponCode** | VARCHAR | null |  | |
| **perCustomerUsageLimit** | INTEGER | null |  | |
| **usageLimit** | INTEGER | null |  | |
| **enabled** | BOOLEAN | not null |  | |
| **conditions** | TEXT | not null |  | |
| **actions** | TEXT | not null |  | |
| **priorityScore** | INTEGER | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### shipping_method

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **deletedAt** | DATETIME | null |  | |
| **code** | VARCHAR | not null |  | |
| **checker** | TEXT | not null |  | |
| **calculator** | TEXT | not null |  | |
| **fulfillmentHandlerCode** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### stock_location

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **name** | VARCHAR | not null |  | |
| **description** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### tax_category

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **name** | VARCHAR | not null |  | |
| **isDefault** | BOOLEAN | not null, default: 0 |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### zone

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **name** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### customer_group

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **name** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### role

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **code** | VARCHAR | not null |  | |
| **description** | VARCHAR | not null |  | |
| **permissions** | TEXT | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### user

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **deletedAt** | DATETIME | null |  | |
| **identifier** | VARCHAR | not null |  | |
| **verified** | BOOLEAN | not null, default: 0 |  | |
| **lastLogin** | DATETIME | null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### global_settings

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **availableLanguages** | TEXT | not null |  | |
| **trackInventory** | BOOLEAN | not null, default: 1 |  | |
| **outOfStockThreshold** | INTEGER | not null, default: 0 |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### payment_method

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **code** | VARCHAR | not null |  | |
| **enabled** | BOOLEAN | not null |  | |
| **checker** | TEXT | null |  | |
| **handler** | TEXT | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### seller

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **deletedAt** | DATETIME | null |  | |
| **name** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### settings_store_entry

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **key** | VARCHAR | not null |  | |
| **value** | BLOB | null |  | |
| **scope** | VARCHAR | null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] | ✅ | ,  |
### job_record

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **queueName** | VARCHAR | not null |  | |
| **data** | TEXT | null |  | |
| **state** | VARCHAR | not null |  | |
| **progress** | INTEGER | not null |  | |
| **result** | TEXT | null |  | |
| **error** | VARCHAR | null |  | |
| **startedAt** | DATETIME | null |  | |
| **settledAt** | DATETIME | null |  | |
| **isSettled** | BOOLEAN | not null |  | |
| **retries** | INTEGER | not null |  | |
| **attempts** | INTEGER | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### job_record_buffer

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **bufferId** | VARCHAR | not null |  | |
| **job** | TEXT | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### scheduled_task_record

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **taskId** | VARCHAR | not null |  | |
| **enabled** | BOOLEAN | not null, default: 1 |  | |
| **lockedAt** | DATETIME | null |  | |
| **lastExecutedAt** | DATETIME | null |  | |
| **manuallyTriggeredAt** | DATETIME | null |  | |
| **lastResult** | BLOB | null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


### search_index_item

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **languageCode** | VARCHAR | 🔑 PK, not null |  | |
| **enabled** | BOOLEAN | not null |  | |
| **productName** | VARCHAR | not null |  | |
| **productVariantName** | VARCHAR | not null |  | |
| **description** | TEXT | not null |  | |
| **slug** | VARCHAR | not null |  | |
| **sku** | VARCHAR | not null |  | |
| **facetIds** | TEXT | not null |  | |
| **facetValueIds** | TEXT | not null |  | |
| **collectionIds** | TEXT | not null |  | |
| **collectionSlugs** | TEXT | not null |  | |
| **channelIds** | TEXT | not null |  | |
| **productPreview** | VARCHAR | not null |  | |
| **productPreviewFocalPoint** | TEXT | null |  | |
| **productVariantPreview** | VARCHAR | not null |  | |
| **productVariantPreviewFocalPoint** | TEXT | null |  | |
| **inStock** | BOOLEAN | not null, default: 1 |  | |
| **productInStock** | BOOLEAN | not null, default: 1 |  | |
| **productVariantId** | INTEGER | 🔑 PK, not null |  | |
| **channelId** | INTEGER | 🔑 PK, not null |  | |
| **productId** | INTEGER | not null |  | |
| **productAssetId** | INTEGER | null |  | |
| **productVariantAssetId** | INTEGER | null |  | |
| **price** | INTEGER | not null |  | |
| **priceWithTax** | INTEGER | not null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
### collection_asset

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **assetId** | INTEGER | not null | fk_collection_asset_assetId_asset | |
| **position** | INTEGER | not null |  | |
| **collectionId** | INTEGER | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### collection_translation

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **languageCode** | VARCHAR | not null |  | |
| **name** | VARCHAR | not null |  | |
| **slug** | VARCHAR | not null |  | |
| **description** | TEXT | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **baseId** | INTEGER | null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### collection

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **isRoot** | BOOLEAN | not null, default: 0 |  | |
| **position** | INTEGER | not null |  | |
| **isPrivate** | BOOLEAN | not null, default: 0 |  | |
| **filters** | TEXT | not null |  | |
| **inheritFilters** | BOOLEAN | not null, default: 1 |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **parentId** | INTEGER | null |  | |
| **featuredAssetId** | INTEGER | null | fk_collection_featuredAssetId_asset | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### facet_translation

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **languageCode** | VARCHAR | not null |  | |
| **name** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **baseId** | INTEGER | null | fk_facet_translation_baseId_facet | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### facet_value_translation

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **languageCode** | VARCHAR | not null |  | |
| **name** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **baseId** | INTEGER | null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### facet_value

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **code** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **facetId** | INTEGER | not null | fk_facet_value_facetId_facet | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### product_option_translation

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **languageCode** | VARCHAR | not null |  | |
| **name** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **baseId** | INTEGER | null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### product_option

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **deletedAt** | DATETIME | null |  | |
| **code** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **groupId** | INTEGER | not null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### product_option_group_translation

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **languageCode** | VARCHAR | not null |  | |
| **name** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **baseId** | INTEGER | null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### product_option_group

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **deletedAt** | DATETIME | null |  | |
| **code** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **productId** | INTEGER | null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### product_asset

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **assetId** | INTEGER | not null | fk_product_asset_assetId_asset | |
| **position** | INTEGER | not null |  | |
| **productId** | INTEGER | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### product_translation

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **languageCode** | VARCHAR | not null |  | |
| **name** | VARCHAR | not null |  | |
| **slug** | VARCHAR | not null |  | |
| **description** | TEXT | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **baseId** | INTEGER | null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### product

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **deletedAt** | DATETIME | null |  | |
| **enabled** | BOOLEAN | not null, default: 1 |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **featuredAssetId** | INTEGER | null | fk_product_featuredAssetId_asset | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### order_line_reference

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **quantity** | INTEGER | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **fulfillmentId** | INTEGER | null | fk_order_line_reference_fulfillmentId_fulfillment | |
| **modificationId** | INTEGER | null |  | |
| **orderLineId** | INTEGER | not null |  | |
| **refundId** | INTEGER | null |  | |
| **discriminator** | VARCHAR | not null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
### refund

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **method** | VARCHAR | not null |  | |
| **reason** | VARCHAR | null |  | |
| **state** | VARCHAR | not null |  | |
| **transactionId** | VARCHAR | null |  | |
| **metadata** | TEXT | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **paymentId** | INTEGER | not null |  | |
| **items** | INTEGER | not null |  | |
| **shipping** | INTEGER | not null |  | |
| **adjustment** | INTEGER | not null |  | |
| **total** | INTEGER | not null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### payment

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **method** | VARCHAR | not null |  | |
| **state** | VARCHAR | not null |  | |
| **errorMessage** | VARCHAR | null |  | |
| **transactionId** | VARCHAR | null |  | |
| **metadata** | TEXT | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **amount** | INTEGER | not null |  | |
| **orderId** | INTEGER | null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### surcharge

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **description** | VARCHAR | not null |  | |
| **listPriceIncludesTax** | BOOLEAN | not null |  | |
| **sku** | VARCHAR | not null |  | |
| **taxLines** | TEXT | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **listPrice** | INTEGER | not null |  | |
| **orderId** | INTEGER | null |  | |
| **orderModificationId** | INTEGER | null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### order_modification

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **note** | VARCHAR | not null |  | |
| **shippingAddressChange** | TEXT | null |  | |
| **billingAddressChange** | TEXT | null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **priceChange** | INTEGER | not null |  | |
| **orderId** | INTEGER | null |  | |
| **paymentId** | INTEGER | null | fk_order_modification_paymentId_payment | |
| **refundId** | INTEGER | null | fk_order_modification_refundId_refund | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### promotion_translation

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **languageCode** | VARCHAR | not null |  | |
| **name** | VARCHAR | not null |  | |
| **description** | TEXT | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **baseId** | INTEGER | null | fk_promotion_translation_baseId_promotion | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### shipping_method_translation

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **languageCode** | VARCHAR | not null |  | |
| **name** | VARCHAR | not null |  | |
| **description** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **baseId** | INTEGER | null | fk_shipping_method_translation_baseId_shipping_method | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### shipping_line

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **listPriceIncludesTax** | BOOLEAN | not null |  | |
| **adjustments** | TEXT | not null |  | |
| **taxLines** | TEXT | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **shippingMethodId** | INTEGER | not null | fk_shipping_line_shippingMethodId_shipping_method | |
| **listPrice** | INTEGER | not null |  | |
| **orderId** | INTEGER | null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### order

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **type** | VARCHAR | not null, default: Regular |  | |
| **code** | VARCHAR | not null |  | |
| **state** | VARCHAR | not null |  | |
| **active** | BOOLEAN | not null, default: 1 |  | |
| **orderPlacedAt** | DATETIME | null |  | |
| **couponCodes** | TEXT | not null |  | |
| **shippingAddress** | TEXT | not null |  | |
| **billingAddress** | TEXT | not null |  | |
| **currencyCode** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **aggregateOrderId** | INTEGER | null |  | |
| **customerId** | INTEGER | null |  | |
| **taxZoneId** | INTEGER | null |  | |
| **subTotal** | INTEGER | not null |  | |
| **subTotalWithTax** | INTEGER | not null |  | |
| **shipping** | INTEGER | not null, default: 0 |  | |
| **shippingWithTax** | INTEGER | not null, default: 0 |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] | ✅ |  |
| [object Object] |  |  |
| [object Object] |  |  |
### stock_movement

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **type** | VARCHAR | not null |  | |
| **quantity** | INTEGER | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **stockLocationId** | INTEGER | not null | fk_stock_movement_stockLocationId_stock_location | |
| **discriminator** | VARCHAR | not null |  | |
| **productVariantId** | INTEGER | null |  | |
| **orderLineId** | INTEGER | null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
### order_line

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **quantity** | INTEGER | not null |  | |
| **orderPlacedQuantity** | INTEGER | not null, default: 0 |  | |
| **listPriceIncludesTax** | BOOLEAN | not null |  | |
| **adjustments** | TEXT | not null |  | |
| **taxLines** | TEXT | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **sellerChannelId** | INTEGER | null |  | |
| **shippingLineId** | INTEGER | null | fk_order_line_shippingLineId_shipping_line | |
| **productVariantId** | INTEGER | not null |  | |
| **taxCategoryId** | INTEGER | null | fk_order_line_taxCategoryId_tax_category | |
| **initialListPrice** | INTEGER | null |  | |
| **listPrice** | INTEGER | not null |  | |
| **featuredAssetId** | INTEGER | null | fk_order_line_featuredAssetId_asset | |
| **orderId** | INTEGER | null | fk_order_line_orderId_order | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
### stock_level

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **stockOnHand** | INTEGER | not null |  | |
| **stockAllocated** | INTEGER | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **productVariantId** | INTEGER | not null |  | |
| **stockLocationId** | INTEGER | not null | fk_stock_level_stockLocationId_stock_location | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] | ✅ | ,  |
### product_variant_asset

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **assetId** | INTEGER | not null | fk_product_variant_asset_assetId_asset | |
| **position** | INTEGER | not null |  | |
| **productVariantId** | INTEGER | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### product_variant_price

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **currencyCode** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **channelId** | INTEGER | null |  | |
| **price** | INTEGER | not null |  | |
| **variantId** | INTEGER | null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### product_variant_translation

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **languageCode** | VARCHAR | not null |  | |
| **name** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **baseId** | INTEGER | null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### product_variant

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **deletedAt** | DATETIME | null |  | |
| **enabled** | BOOLEAN | not null, default: 1 |  | |
| **sku** | VARCHAR | not null |  | |
| **outOfStockThreshold** | INTEGER | not null, default: 0 |  | |
| **useGlobalOutOfStockThreshold** | BOOLEAN | not null, default: 1 |  | |
| **trackInventory** | VARCHAR | not null, default: INHERIT |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **featuredAssetId** | INTEGER | null | fk_product_variant_featuredAssetId_asset | |
| **taxCategoryId** | INTEGER | null | fk_product_variant_taxCategoryId_tax_category | |
| **productId** | INTEGER | null | fk_product_variant_productId_product | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
### region_translation

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **languageCode** | VARCHAR | not null |  | |
| **name** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **baseId** | INTEGER | null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### region

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **code** | VARCHAR | not null |  | |
| **type** | VARCHAR | not null |  | |
| **enabled** | BOOLEAN | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **parentId** | INTEGER | null |  | |
| **discriminator** | VARCHAR | not null |  | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### tax_rate

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **name** | VARCHAR | not null |  | |
| **enabled** | BOOLEAN | not null |  | |
| **value** | BLOB | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **categoryId** | INTEGER | null | fk_tax_rate_categoryId_tax_category | |
| **zoneId** | INTEGER | null | fk_tax_rate_zoneId_zone | |
| **customerGroupId** | INTEGER | null | fk_tax_rate_customerGroupId_customer_group | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
### authentication_method

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **identifier** | VARCHAR | null |  | |
| **passwordHash** | VARCHAR | null |  | |
| **verificationToken** | VARCHAR | null |  | |
| **passwordResetToken** | VARCHAR | null |  | |
| **identifierChangeToken** | VARCHAR | null |  | |
| **pendingIdentifier** | VARCHAR | null |  | |
| **strategy** | VARCHAR | null |  | |
| **externalIdentifier** | VARCHAR | null |  | |
| **metadata** | TEXT | null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **type** | VARCHAR | not null |  | |
| **userId** | INTEGER | null | fk_authentication_method_userId_user | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### session

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **token** | VARCHAR | not null |  | |
| **expires** | DATETIME | not null |  | |
| **invalidated** | BOOLEAN | not null |  | |
| **authenticationStrategy** | VARCHAR | null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **activeOrderId** | INTEGER | null | fk_session_activeOrderId_order | |
| **activeChannelId** | INTEGER | null |  | |
| **type** | VARCHAR | not null |  | |
| **userId** | INTEGER | null | fk_session_userId_user | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] | ✅ |  |
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
### customer

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **deletedAt** | DATETIME | null |  | |
| **title** | VARCHAR | null |  | |
| **firstName** | VARCHAR | not null |  | |
| **lastName** | VARCHAR | not null |  | |
| **phoneNumber** | VARCHAR | null |  | |
| **emailAddress** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **userId** | INTEGER | null | fk_customer_userId_user | | 


### address

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **fullName** | VARCHAR | not null |  | |
| **company** | VARCHAR | not null |  | |
| **streetLine1** | VARCHAR | not null |  | |
| **streetLine2** | VARCHAR | not null |  | |
| **city** | VARCHAR | not null |  | |
| **province** | VARCHAR | not null |  | |
| **postalCode** | VARCHAR | not null |  | |
| **phoneNumber** | VARCHAR | not null |  | |
| **defaultShippingAddress** | BOOLEAN | not null, default: 0 |  | |
| **defaultBillingAddress** | BOOLEAN | not null, default: 0 |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **customerId** | INTEGER | null | fk_address_customerId_customer | |
| **countryId** | INTEGER | null | fk_address_countryId_region | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### administrator

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **deletedAt** | DATETIME | null |  | |
| **firstName** | VARCHAR | not null |  | |
| **lastName** | VARCHAR | not null |  | |
| **emailAddress** | VARCHAR | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **userId** | INTEGER | null | fk_administrator_userId_user | | 


### payment_method_translation

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **languageCode** | VARCHAR | not null |  | |
| **name** | VARCHAR | not null |  | |
| **description** | TEXT | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **baseId** | INTEGER | null | fk_payment_method_translation_baseId_payment_method | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
### channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **code** | VARCHAR | not null |  | |
| **token** | VARCHAR | not null |  | |
| **description** | VARCHAR | null |  | |
| **defaultLanguageCode** | VARCHAR | not null |  | |
| **availableLanguageCodes** | TEXT | null |  | |
| **defaultCurrencyCode** | VARCHAR | not null |  | |
| **availableCurrencyCodes** | TEXT | null |  | |
| **trackInventory** | BOOLEAN | not null, default: 1 |  | |
| **outOfStockThreshold** | INTEGER | not null, default: 0 |  | |
| **pricesIncludeTax** | BOOLEAN | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **sellerId** | INTEGER | null | fk_channel_sellerId_seller | |
| **defaultTaxZoneId** | INTEGER | null | fk_channel_defaultTaxZoneId_zone | |
| **defaultShippingZoneId** | INTEGER | null | fk_channel_defaultShippingZoneId_zone | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
### history_entry

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **createdAt** | DATETIME | not null, default: datetime('now') |  | |
| **updatedAt** | DATETIME | not null, default: datetime('now') |  | |
| **type** | VARCHAR | not null |  | |
| **isPublic** | BOOLEAN | not null |  | |
| **data** | TEXT | not null |  | |
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **discriminator** | VARCHAR | not null |  | |
| **administratorId** | INTEGER | null | fk_history_entry_administratorId_administrator | |
| **customerId** | INTEGER | null | fk_history_entry_customerId_customer | |
| **orderId** | INTEGER | null | fk_history_entry_orderId_order | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
| [object Object] |  |  |
### collection_product_variants_product_variant

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **collectionId** | INTEGER | 🔑 PK, not null | fk_collection_product_variants_product_variant_collectionId_collection | |
| **productVariantId** | INTEGER | 🔑 PK, not null | fk_collection_product_variants_product_variant_productVariantId_product_variant | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### collection_channels_channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **collectionId** | INTEGER | 🔑 PK, not null | fk_collection_channels_channel_collectionId_collection | |
| **channelId** | INTEGER | 🔑 PK, not null | fk_collection_channels_channel_channelId_channel | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### facet_channels_channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **facetId** | INTEGER | 🔑 PK, not null | fk_facet_channels_channel_facetId_facet | |
| **channelId** | INTEGER | 🔑 PK, not null | fk_facet_channels_channel_channelId_channel | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### facet_value_channels_channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **facetValueId** | INTEGER | 🔑 PK, not null | fk_facet_value_channels_channel_facetValueId_facet_value | |
| **channelId** | INTEGER | 🔑 PK, not null | fk_facet_value_channels_channel_channelId_channel | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### product_facet_values_facet_value

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **productId** | INTEGER | 🔑 PK, not null | fk_product_facet_values_facet_value_productId_product | |
| **facetValueId** | INTEGER | 🔑 PK, not null | fk_product_facet_values_facet_value_facetValueId_facet_value | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### product_channels_channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **productId** | INTEGER | 🔑 PK, not null | fk_product_channels_channel_productId_product | |
| **channelId** | INTEGER | 🔑 PK, not null | fk_product_channels_channel_channelId_channel | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### asset_tags_tag

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **assetId** | INTEGER | 🔑 PK, not null | fk_asset_tags_tag_assetId_asset | |
| **tagId** | INTEGER | 🔑 PK, not null | fk_asset_tags_tag_tagId_tag | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### asset_channels_channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **assetId** | INTEGER | 🔑 PK, not null | fk_asset_channels_channel_assetId_asset | |
| **channelId** | INTEGER | 🔑 PK, not null | fk_asset_channels_channel_channelId_channel | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### promotion_channels_channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **promotionId** | INTEGER | 🔑 PK, not null | fk_promotion_channels_channel_promotionId_promotion | |
| **channelId** | INTEGER | 🔑 PK, not null | fk_promotion_channels_channel_channelId_channel | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### shipping_method_channels_channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **shippingMethodId** | INTEGER | 🔑 PK, not null | fk_shipping_method_channels_channel_shippingMethodId_shipping_method | |
| **channelId** | INTEGER | 🔑 PK, not null | fk_shipping_method_channels_channel_channelId_channel | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### order_promotions_promotion

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **orderId** | INTEGER | 🔑 PK, not null | fk_order_promotions_promotion_orderId_order | |
| **promotionId** | INTEGER | 🔑 PK, not null | fk_order_promotions_promotion_promotionId_promotion | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### order_fulfillments_fulfillment

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **orderId** | INTEGER | 🔑 PK, not null | fk_order_fulfillments_fulfillment_orderId_order | |
| **fulfillmentId** | INTEGER | 🔑 PK, not null | fk_order_fulfillments_fulfillment_fulfillmentId_fulfillment | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### order_channels_channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **orderId** | INTEGER | 🔑 PK, not null | fk_order_channels_channel_orderId_order | |
| **channelId** | INTEGER | 🔑 PK, not null | fk_order_channels_channel_channelId_channel | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### stock_location_channels_channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **stockLocationId** | INTEGER | 🔑 PK, not null | fk_stock_location_channels_channel_stockLocationId_stock_location | |
| **channelId** | INTEGER | 🔑 PK, not null | fk_stock_location_channels_channel_channelId_channel | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### product_variant_options_product_option

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **productVariantId** | INTEGER | 🔑 PK, not null | fk_product_variant_options_product_option_productVariantId_product_variant | |
| **productOptionId** | INTEGER | 🔑 PK, not null | fk_product_variant_options_product_option_productOptionId_product_option | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### product_variant_facet_values_facet_value

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **productVariantId** | INTEGER | 🔑 PK, not null | fk_product_variant_facet_values_facet_value_productVariantId_product_variant | |
| **facetValueId** | INTEGER | 🔑 PK, not null | fk_product_variant_facet_values_facet_value_facetValueId_facet_value | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### product_variant_channels_channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **productVariantId** | INTEGER | 🔑 PK, not null | fk_product_variant_channels_channel_productVariantId_product_variant | |
| **channelId** | INTEGER | 🔑 PK, not null | fk_product_variant_channels_channel_channelId_channel | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### zone_members_region

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **zoneId** | INTEGER | 🔑 PK, not null | fk_zone_members_region_zoneId_zone | |
| **regionId** | INTEGER | 🔑 PK, not null | fk_zone_members_region_regionId_region | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### role_channels_channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **roleId** | INTEGER | 🔑 PK, not null | fk_role_channels_channel_roleId_role | |
| **channelId** | INTEGER | 🔑 PK, not null | fk_role_channels_channel_channelId_channel | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### user_roles_role

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **userId** | INTEGER | 🔑 PK, not null | fk_user_roles_role_userId_user | |
| **roleId** | INTEGER | 🔑 PK, not null | fk_user_roles_role_roleId_role | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### customer_groups_customer_group

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **customerId** | INTEGER | 🔑 PK, not null | fk_customer_groups_customer_group_customerId_customer | |
| **customerGroupId** | INTEGER | 🔑 PK, not null | fk_customer_groups_customer_group_customerGroupId_customer_group | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### customer_channels_channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **customerId** | INTEGER | 🔑 PK, not null | fk_customer_channels_channel_customerId_customer | |
| **channelId** | INTEGER | 🔑 PK, not null | fk_customer_channels_channel_channelId_channel | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### payment_method_channels_channel

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **paymentMethodId** | INTEGER | 🔑 PK, not null | fk_payment_method_channels_channel_paymentMethodId_payment_method | |
| **channelId** | INTEGER | 🔑 PK, not null | fk_payment_method_channels_channel_channelId_channel | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### collection_closure

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id_ancestor** | INTEGER | 🔑 PK, not null | fk_collection_closure_id_ancestor_collection | |
| **id_descendant** | INTEGER | 🔑 PK, not null | fk_collection_closure_id_descendant_collection | | 


#### Indexes
| Name | Unique | Fields |
|------|--------|--------|
| [object Object] |  |  |
| [object Object] |  |  |
### migrations

| Name        | Type          | Settings                      | References                    | Note                           |
|-------------|---------------|-------------------------------|-------------------------------|--------------------------------|
| **id** | INTEGER | 🔑 PK, not null, autoincrement |  | |
| **timestamp** | INTEGER | not null |  | |
| **name** | VARCHAR | not null |  | | 


## Relationships

- **collection_asset to asset**: many_to_one
- **collection to asset**: many_to_one
- **facet_translation to facet**: many_to_one
- **facet_value to facet**: many_to_one
- **product_asset to asset**: many_to_one
- **product to asset**: many_to_one
- **order_line_reference to fulfillment**: many_to_one
- **order_modification to payment**: many_to_one
- **order_modification to refund**: many_to_one
- **promotion_translation to promotion**: many_to_one
- **shipping_method_translation to shipping_method**: many_to_one
- **shipping_line to shipping_method**: many_to_one
- **stock_movement to stock_location**: many_to_one
- **order_line to shipping_line**: many_to_one
- **order_line to tax_category**: many_to_one
- **order_line to asset**: many_to_one
- **order_line to order**: many_to_one
- **stock_level to stock_location**: many_to_one
- **product_variant_asset to asset**: many_to_one
- **product_variant to asset**: many_to_one
- **product_variant to tax_category**: many_to_one
- **product_variant to product**: many_to_one
- **tax_rate to tax_category**: many_to_one
- **tax_rate to zone**: many_to_one
- **tax_rate to customer_group**: many_to_one
- **authentication_method to user**: many_to_one
- **session to order**: many_to_one
- **session to user**: many_to_one
- **customer to user**: many_to_one
- **address to customer**: many_to_one
- **address to region**: many_to_one
- **administrator to user**: many_to_one
- **payment_method_translation to payment_method**: many_to_one
- **channel to seller**: many_to_one
- **channel to zone**: many_to_one
- **channel to zone**: many_to_one
- **history_entry to administrator**: many_to_one
- **history_entry to customer**: many_to_one
- **history_entry to order**: many_to_one
- **collection_product_variants_product_variant to collection**: many_to_one
- **collection_product_variants_product_variant to product_variant**: many_to_one
- **collection_channels_channel to collection**: many_to_one
- **collection_channels_channel to channel**: many_to_one
- **facet_channels_channel to facet**: many_to_one
- **facet_channels_channel to channel**: many_to_one
- **facet_value_channels_channel to facet_value**: many_to_one
- **facet_value_channels_channel to channel**: many_to_one
- **product_facet_values_facet_value to product**: many_to_one
- **product_facet_values_facet_value to facet_value**: many_to_one
- **product_channels_channel to product**: many_to_one
- **product_channels_channel to channel**: many_to_one
- **asset_tags_tag to asset**: many_to_one
- **asset_tags_tag to tag**: many_to_one
- **asset_channels_channel to asset**: many_to_one
- **asset_channels_channel to channel**: many_to_one
- **promotion_channels_channel to promotion**: many_to_one
- **promotion_channels_channel to channel**: many_to_one
- **shipping_method_channels_channel to shipping_method**: many_to_one
- **shipping_method_channels_channel to channel**: many_to_one
- **order_promotions_promotion to order**: many_to_one
- **order_promotions_promotion to promotion**: many_to_one
- **order_fulfillments_fulfillment to order**: many_to_one
- **order_fulfillments_fulfillment to fulfillment**: many_to_one
- **order_channels_channel to order**: many_to_one
- **order_channels_channel to channel**: many_to_one
- **stock_location_channels_channel to stock_location**: many_to_one
- **stock_location_channels_channel to channel**: many_to_one
- **product_variant_options_product_option to product_variant**: many_to_one
- **product_variant_options_product_option to product_option**: many_to_one
- **product_variant_facet_values_facet_value to product_variant**: many_to_one
- **product_variant_facet_values_facet_value to facet_value**: many_to_one
- **product_variant_channels_channel to product_variant**: many_to_one
- **product_variant_channels_channel to channel**: many_to_one
- **zone_members_region to zone**: many_to_one
- **zone_members_region to region**: many_to_one
- **role_channels_channel to role**: many_to_one
- **role_channels_channel to channel**: many_to_one
- **user_roles_role to user**: many_to_one
- **user_roles_role to role**: many_to_one
- **customer_groups_customer_group to customer**: many_to_one
- **customer_groups_customer_group to customer_group**: many_to_one
- **customer_channels_channel to customer**: many_to_one
- **customer_channels_channel to channel**: many_to_one
- **payment_method_channels_channel to payment_method**: many_to_one
- **payment_method_channels_channel to channel**: many_to_one
- **collection_closure to collection**: many_to_one
- **collection_closure to collection**: many_to_one
