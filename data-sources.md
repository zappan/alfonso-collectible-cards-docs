# Data Sources

## Data Sources Classification

### Sources with an API

Data sources providing an official API, whether free or paid, are the best foundation to build a business upon. They offer reliability, dependability, and a straightforward way to access data for further processing to meet the product’s needs. Such sources are clearly considered long-term viable options.

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [eBay API](https://developer.ebay.com/) | Sales data (real-time & historical) | Yes _(Limitations apply)_ | Robust API with filters for sport, card year, and grade. OAuth required. |
| [Pokémon TCG API](https://pokemontcg.io/) | Non-sports card data (Pokémon) | Yes | Robust and free. Great for Pokémon collectors. |

##### ADDITIONAL SOURCES FOUND DURING RESEARCH

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [Mavin.io](https://www.mavin.io/developers) | price guide and search engine for real-time market value of collectibles, strongly focused on sports cards and trading cards | Yes | aggregates real-time sales data from multiple marketplaces, pricing information based on actual sales |
| [SportsCardsPro API](https://www.sportscardspro.com/api-documentation) | Prices API, Marketplace API, CSV download | Yes (Paid) | Current & Historic Sports Card Prices, Free PSA, BGS & Ungraded Sports Card Price Guide; OAuth required. |
| [CardTrader.com](https://www.cardtrader.com/en/docs/api) | online marketplace for trading card games (TCGs) | Yes ([see ToS](https://static.cardtrader.com/en/pages/terms-of-service)) | It caters to both individual collectors and professional retailers. OAuth required |
| [Cardmarket API](https://help.cardmarket.com/en/cardmarket-api) | peer-to-peer marketplace for TCG enthusiasts | Yes (Paid) | Europe’s largest online marketplace dedicated to trading card games (TCGs); OAuth required; _Currently, not accepting applications for access to the Cardmarket API._ |

##### NO API FOUND

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [Alt.xyz API](https://developers.alt.xyz/) | Historical price trends and card indices | ~Yes~ _(no API found)_ | Strong market analytics and trend data. Requires developer registration. |
| [Sports Card Investor API](https://www.sportscardinvestor.com/) | Card catalog, images, pricing | ~Yes (Paid)~ _(no API found)_ | API access via premium plan. Good for retail card price lookups. |
| [Card Hedge API](https://www.cardhedger.com/) | Card prices, grading data, trends | ~Yes (Paid)~ _(no API found)_ | Promising data source for price comps and graded card analytics. |


### Sources with an unofficial API or structured data dumps

Data sources that don't offer an API but provide standardized and reliable data dumps in structured formats such as CSV, XML, or JSON can still be considered dependable. These structured formats are easy to process using data orchestration workflow tools, like the ones being considered for this project, making such sources a viable and maintainable option for long-term data integration.

Data sources with an unofficial API, although seemingly viable, pose a reliability risk. These unofficial APIs can disappear overnight without prior notice, or may be placed behind an authorization wall if the owners decide that external data access is not acceptable. Such sources may be integrated into the solution with the caveat that they, and the data they provide, could become unavailable at any time, potentially having a tangible impact on the business.

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [MLB](https://www.mlb.com/) / [NFL](https://www.nfl.com/) / [NBA](https://www.nba.com/) / [NHL](https://www.nhl.com/) | Official player data and stats | Unofficial | Some endpoints are discoverable but undocumented. |
| [Gemrate](https://www.gemrate.com/) | Grading population trends, PSA volume stats | No (Web-Scraping or CSV) | Offers valuable population reports and grading activity insights. No public API, but data is structured and updated frequently. |


### Sources with no API

Data sources with no API and no structured data dumps pose a range of challenges and risks that the product needs to take into account. These include technical issues affecting the reliability, sustainability, and maintenance of data extraction, as well as legal concerns related to collecting data without the owners’ consent. The product should aim to avoid critical dependencies on such sources, or pursue agreements that permit the data to be used legally and reliably.

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [130point](https://130point.com/) (Unofficial) | Sales comps across marketplaces | No | No public API. Scraping or data parsing may be needed. |
| [Goldin](https://www.goldin.co/) / [PWCC](https://www.pwccmarketplace.com/) / [Heritage](https://www.ha.com/) / [REA&#160;Auctions](https://www.robertedwardauctions.com/) | Premium auction sales data | No | Manual access or scraping needed. No public API. |
| [PSA](https://www.psacard.com/pop/) | Grading population reports and cert verification | No | Limited access. Web scraping or browser automation may be used. |
| [BGS (Beckett)](https://www.beckett.com/grading/)) | Grading info and population reports | No | No public API; may require scraping or third-party access. |
| [SGC](https://www.gosgc.com) | Grading info and population reports | No | No public API; may require scraping or third-party access. |
| [CGC Cards](https://www.cgccards.com/) | Graded card verification and reports | No | No API available. Web scraping or OCR might be options. |
| [TCDB (Trading Card Database)](https://www.tcdb.com/) | Card images, checklists, and variations | No | Community-driven data. No public API but structured data. |
| [COMC](https://www.comc.com/) | Images, inventory, some pricing | No | Data available via website structure; scraping needed. |
| [FanGraphs](https://www.fangraphs.com/) | Baseball prospecting and advanced stats | No | CSV export and well-structured HTML. Good for scouting. |
| [Sports Reference](https://www.sports-reference.com/) (BBall&#160;/&#160;Football&#160;/&#160;Hockey) | Player stats, bios, history | No | Well-structured HTML for parsing. |

##### ADDITIONAL SOURCES FOUND DURING RESEARCH

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [SellThePeak](https://sellthepeak.com/) | tools and resources for determining the value of sports cards, especially through accurate eBay Best Offer Accepted prices | No | Ajax-driven, hard to web-scrape; if AJAX calls can be reverse-engineered, there could be a chance |
| [CardSnoop](https://cardsnoop.com) | sales data across various market places for sports cards | ? (_TBD_) | focuses on sales rather than listings; _Site currently not accessible; could be defunct_ |




#### TECHNICAL ASPECTS OF WEB SCRAPING

Web scraping is, technically, never a stable solution. If the structure of a scraped website changes, the scraping setup can break overnight. As such, web scraping should be considered a constantly moving target that requires continuous monitoring and immediate reaction when a change occurs. Any structural modification may cause the scraper to fail, requiring the scraping logic to be immediately updated to match the new layout.

That said, recent advances in AI-driven tools are beginning to change this landscape, offering more adaptive approaches to web data extraction that are less dependent on rigid structural assumptions. Still, this remains relatively uncharted territory, introducing its own set of risks around timelines and budgets, compared to classic web scraping solutions which use headless browsers and CSS selectors or XPath expressions to locate and extract data.


#### LEGAL ASPECTS OF WEB SCRAPING

Web scraping is typically against the terms of service of most websites and may sometimes even violate copyright law. Not that it prevents people from scraping websites in general, and it may have no repercussions for hobby projects or very small-scale businesses that stay under the radar. Still, if a business takes off and becomes successful and popular, unauthorized or illicit data scraping will likely not go unnoticed.

If possible, arranging authorization deals with the respective data owners as soon as it becomes business-feasible may help avoid unnecessary disputes and could even open up the possibility of gaining structured access to the data through an API or via CSV, XML, or JSON data dumps.

---

## Data Sources with an API


### [eBay API](https://developer.ebay.com/)

**NOTE:** Some of the eBay APIs are limited or a public beta releases, with limitations and conditions on their use.

**Sales History data**, which we're interested in, is part of the [Buy APIs](https://developer.ebay.com/api-docs/buy/static/buying-ig-landing.html), specifically the [Marketplace Insights API](https://developer.ebay.com/api-docs/buy/static/api-insights.html). That API allows retrieving eBay sales history information of items sold on eBay for the last 90 days.

Unfortunately, many of the Buy APIs, including the Marketplace Insights API, are a Limited Release with specific requirements. For more information, refer to [API launch stages](https://developer.ebay.com/api-docs/static/versioning.html#stages) in the _Using eBay RESTful APIs Guide_, and the [Buy APIs Requirements](https://developer.ebay.com/api-docs/buy/static/buy-requirements.html) in the _Buying Integration Guide_.

> _"The use of eBay’s Buy APIs in production is **intended for eBay partners only**. You must apply for production access through the eBay Partner Network. Acceptance of applications is based on the proposed business model, as well as a formal agreement to abide by the policies and requirements stipulated by eBay."_

Users must meet standard [Eligibility requirements](https://developer.ebay.com/api-docs/buy/static/buy-requirements.html#ProductionReq), get approvals from eBay support organizations, and sign contracts with eBay to access the Buy APIs in production. See [Production access process](https://developer.ebay.com/api-docs/buy/static/buy-requirements.html#Applying) for additional information and instructions for requesting production access.

#### eBay APIs RESOURCES

* [Using eBay RESTful APIs Guide](https://developer.ebay.com/api-docs/static/ebay-rest-landing.html)
* [eBay SDKs](https://developer.ebay.com/develop/sdks-and-widgets)
* [Taxonomy API Overview](https://developer.ebay.com/api-docs/commerce/taxonomy/overview.html)
* [Buy APIs Overview](https://developer.ebay.com/api-docs/buy/static/buy-overview.html)
  * [Buying Integration Guide](https://developer.ebay.com/api-docs/buy/static/buying-ig-landing.html)
* [Selling Apps APIs](https://developer.ebay.com/develop/selling-apps)
  * [Selling Integration Guide](https://developer.ebay.com/api-docs/sell/static/selling-ig-landing.html)
* [eBay API Call Limits](https://developer.ebay.com/develop/get-started/api-call-limits)
* [Postman Documentation](https://www.postman.com/api-evangelist/ebay/documentation/3bv8oa7/ebay)


### [Alt.xyz API](https://developers.alt.xyz/)

_There is no developers section on https://www.alt.xyz/ website, nor is https://developers.alt.xyz/ URL active. It seems there is no public API available here._


### [Pokémon TCG API](https://pokemontcg.io/)

The Pokémon Trading Cards Game (TCG) API offers comprehensive information
about the Pokemon trading cards, including cards and sets information, types,
and the list of rarities. Card API offers some basic card market data details,
like average prices, trending price, and the lowest price for the card.

It's a REST API that can be used with or without an API key. API key provides
higher usage limits, and is obtained through registration at the Developer Portal.

> _The Pokémon TCG Developer Portal lets you manage your account and API Key_
> _associated with the Pokémon TCG API. Creating an account will get you access_
> _to higher rate limits and no IP restrictions._

By default, requests are limited to 20,000/day with an API key. For a higher
rate limit, contact the author via Discord or email to discuss. Without an API
key, rate limits are at 1,000 requests a day, and a maxium of 30 per minute.

#### Pokémon TCG API RESOURCES

* [Pokémon TCG Developer Portal](https://dev.pokemontcg.io/)
* [Pokémon TCG API Documentation](https://docs.pokemontcg.io/)


### [Sports Card Investor API](https://www.sportscardinvestor.com/)

Sports Card Investor does not publicly advertise or offer an API for accessing
its data. Their main data tool, Market Movers, is available through web and
mobile applications, but there is no mention of API access for developers or
third-party integrations on their official channels or promotional materials.

There is a mention of [Market Movers](https://www.marketmoversapp.com/sci/),
an application owned by the Sports Card Investor. Market Movers does offer a
Premium Plan, but still there is no mention of an API, no developers section,
nor any kind of API documentation available. They don't seem to be in the
business of selling or providing data, they seem to be in the business of
offering a consumer application with a collection tracker, price guide, sales
charts, for-sale listings, and pricing analytics.

_NOTE: The shared note mentioned the existence of API access through a premium
plan. Unfortunately, there is no mention of the API itself, nor is any
documentation available to support any kind of assessment._


### [Card Hedge API](https://www.cardhedger.com/)

Card Hedge advertises an "enterprise grade sports card & trading card API",
offering data on over 1.8 million cards, with prices for all major graders,
and an ability to get real-time price updates and download card data. They
offer an API or a CSV data dumps. Prices are updated every 5 minutes, and
a real-time webhook API is advertised.

_NOTE: The shared note included an indication this is a paid API. Unfortunately,
there is no public documentation available to make a first-hand assessment of
the API interface, nor is there any pricing communicated publicly. The only
thing available is the contact form._


#### ADDITIONAL API SOURCES FOUND DURING RESEARCH

### [Mavin.io](https://www.mavin.io/developers)

Mavin.io is designed to help collectors and sellers determine the current
market value of various items, particularly collectibles. By aggregating
real-time sales data from multiple marketplaces, Mavin provides users with
accurate pricing information based on actual sales, rather than just listed
prices.

Mavin.io offers a RESTful JSON API that allows developers to integrate
real-time market value data for collectibles into their applications. This API
provides up-to-date information on current market prices, including high and
low values, for various collectibles. The API is available at no cost.


### [SportsCardsPro API](https://www.sportscardspro.com/api-documentation)

SportsCardsPro is an comprehensive platform dedicated to providing current and
historic price data for major sports and non-sports collectibles. SportsCardsPro
covers a broad spectrum of collectibles, including Sports Cards (Baseball,
Basketball, Football, Hockey, Soccer, UFC, Wrestling, Golf, Tennis, Racing,
Boxing), Non-Sports Collectibles (Pokémon, Magic: The Gathering, Yu-Gi-Oh!,
Disney Lorcana, Garbage Pail Kids, etc.), and other Collectibles (Funko Pops,
Coins, Comic Books, LEGO Sets)

Key Features include real-time price tracking from eBay and its own marketplace
to provide up-to-date pricing for a wide range of cards, including ungraded and
graded (PSA, BGS) conditions _(see [FAQ](https://www.sportscardspro.com/faq)
for details)_. It also offers various analytical tools such as a lot value
calculator, eBay deal scanner, and item demand reports to assist users in making
informed decisions.

Developers can integrate SportsCardsPro's data into their applications through
available API access. For API access, a [commercial license](https://www.sportscardspro.com/sportscardspro-premium?f=api)
is required


### [CardTrader.com](https://www.cardtrader.com/en/docs/api)

CardTrader is a European-based online marketplace specializing in the buying and selling of trading cards from popular games, including: Magic: The Gathering, Pokémon, Yu-Gi-Oh!, Flesh and Blood, Digimon, One Piece, Dragon Ball Super, Cardfight!! Vanguard, My Hero Academia, Disney Lorcana, Star Wars Unlimited, etc.

A standout feature of CardTrader is its "CardTrader Zero" service, which revolutionizes shipping by consolidating all purchases from different sellers worldwide into a single shipment, significantly reducing expenses for buyers. The platform emphasizes original cards and fraud protection, providing buyers with confidence in their purchases.

CardTrader’s API is designed to support trading functionality, including the listing of marketplace products along with pricing information.


### [Cardmarket API](https://help.cardmarket.com/en/cardmarket-api)

[Cardmarket](https://www.cardmarket.com/en) is Europe's largest peer-to-peer online marketplace dedicated to trading card games. It supports a wide range of games, including Magic: The Gathering, Pokémon, Yu-Gi-Oh!, Dragon Ball Super, Final Fantasy TCG, Cardfight!! Vanguard, Weiss Schwarz. The platform hosts over 500 million card offers, such as individual cards, boxes, and accessories, facilitating the sale of over 600 million cards to date.

Cardmarket offers an API interface for users to create their own apps for using Cardmarket. Only users with a commercial account can apply for and register 3rd Party apps, which need to be verified by Cardmarket.

_Unfortunately, Cardmarket is not currently accepting new applications for access to the Cardmarket API. Still, it may be worthwhile to reach out and explore potential partnership opportunities._


## Unofficial APIs & Data Dumps


### [Gemrate](https://www.gemrate.com/)

Gemrate offers services centered around population reports, and tracking and
analyzing card grading trends across major grading companies such as PSA, BGS,
SGC, and CGC.

It does not publicly advertise or provide access to its data via an API or
downloadable data exports, nor is there any documentation indicating that
Gemrate offers a way for developers to programmatically access their data.

What is available is a CSV export option via the website's UI. This data is
possibly acquireble via a headless browser, and some automation to browse
through the vast amount of available reports on the site.


### [MLB](https://www.mlb.com/) / [NBA](https://www.nba.com/) / [NFL](https://www.nfl.com/) / [NHL](https://www.nhl.com/)

MLB.com / NBA.com / NFL.com / NHL.com don't provide a public, documented API
for developers for accessing trading card data programmatically. For accessing
sports collectible and trading card data, there are 3rd party APIs designed to
provide detailed card information and pricing data.


---


### No-API Sources


### [130point (Unofficial)](https://130point.com/)

There is no indication that 130point.com offers a public API for accessing its
data. The community discussions also do not reference any developer access or
integration options. And, the technology used is a classic server-side rendering
website which doesn't rely on an API, not even internally.

What the site does offer is an eBay sales search, leveraging the eBay API for
finding cards for sale, and a separate "integrated" search that includes eBay
plus some other platforms. They also link to [WaxStat](https://www.waxstat.com/)
for release calendar and their price guide. Of own searchable data, it seems
the site offers cards checklists, per sports or per athlete, but no pricing
data is attached to it. It also seems that they don't produce any unique
datasets that can't be obtained elsewhere.

As cards and card sets search have their unique URLs that can be easily
constructed, there is an opportunity for downloading the data from the search
results as CSV through web-scraping techniques.
