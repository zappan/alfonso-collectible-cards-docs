# Data Sources

## Sources with an API

Data sources providing an official API, whether free or paid, are the best foundation to build a business upon. They offer reliability, dependability, and a straightforward way to access data for further processing to meet the product’s needs. Such sources are clearly considered long-term viable options.

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [eBay API](https://developer.ebay.com/) | Sales data (real-time & historical) | Yes _(Limitations apply)_ | Robust API with filters for sport, card year, and grade. OAuth required. |
| [Pokémon TCG API](https://pokemontcg.io/) | Non-sports card data (Pokémon) | Yes | Robust and free. Great for Pokémon collectors. |

---

### [eBay API](https://developer.ebay.com/)

**NOTE:** Some of the eBay APIs are limited or a public beta releases, with limitations and conditions on their use.

**Sales History data**, which we're interested in, is part of the [Buy APIs](https://developer.ebay.com/api-docs/buy/static/buying-ig-landing.html), specifically the [Marketplace Insights API](https://developer.ebay.com/api-docs/buy/static/api-insights.html). That API allows retrieving eBay sales history information of items sold on eBay for the last 90 days.

Unfortunately, many of the Buy APIs, including the Marketplace Insights API, are a Limited Release with specific requirements. For more information, refer to [API launch stages](https://developer.ebay.com/api-docs/static/versioning.html#stages) in the _Using eBay RESTful APIs Guide_, and the [Buy APIs Requirements](https://developer.ebay.com/api-docs/buy/static/buy-requirements.html) in the _Buying Integration Guide_.

> _"The use of eBay’s Buy APIs in production is **intended for eBay partners only**. You must apply for production access through the eBay Partner Network. Acceptance of applications is based on the proposed business model, as well as a formal agreement to abide by the policies and requirements stipulated by eBay."_

Users must meet standard [Eligibility requirements](https://developer.ebay.com/api-docs/buy/static/buy-requirements.html#ProductionReq), get approvals from eBay support organizations, and sign contracts with eBay to access the Buy APIs in production. See [Production access process](https://developer.ebay.com/api-docs/buy/static/buy-requirements.html#Applying) for additional information and instructions for requesting production access.

##### eBay APIs RESOURCES

* [Using eBay RESTful APIs Guide](https://developer.ebay.com/api-docs/static/ebay-rest-landing.html)
* [eBay SDKs](https://developer.ebay.com/develop/sdks-and-widgets)
* [Taxonomy API Overview](https://developer.ebay.com/api-docs/commerce/taxonomy/overview.html)
* [Buy APIs Overview](https://developer.ebay.com/api-docs/buy/static/buy-overview.html)
  * [Buying Integration Guide](https://developer.ebay.com/api-docs/buy/static/buying-ig-landing.html)
* [Selling Apps APIs](https://developer.ebay.com/develop/selling-apps)
  * [Selling Integration Guide](https://developer.ebay.com/api-docs/sell/static/selling-ig-landing.html)
* [eBay API Call Limits](https://developer.ebay.com/develop/get-started/api-call-limits)
* [Postman Documentation](https://www.postman.com/api-evangelist/ebay/documentation/3bv8oa7/ebay)

---

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

##### Pokémon TCG API RESOURCES

* [Pokémon TCG Developer Portal](https://dev.pokemontcg.io/)
* [Pokémon TCG API Documentation](https://docs.pokemontcg.io/)


---

### ADDITIONAL API SOURCES FOUND DURING RESEARCH

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [Mavin.io](https://www.mavin.io/developers) | price guide and search engine for real-time market value of collectibles, strongly focused on sports cards and trading cards | Yes | aggregates real-time sales data from multiple marketplaces, pricing information based on actual sales |
| [SportsCardsPro API](https://www.sportscardspro.com/api-documentation) | Prices API, Marketplace API, CSV download | Yes (Paid) | Current & Historic Sports Card Prices, Free PSA, BGS & Ungraded Sports Card Price Guide; OAuth required. |
| [CardTrader.com](https://www.cardtrader.com/en/docs/api) | online marketplace for trading card games (TCGs) | Yes ([see ToS](https://static.cardtrader.com/en/pages/terms-of-service)) | It caters to both individual collectors and professional retailers. OAuth required |
| [Cardmarket API](https://help.cardmarket.com/en/cardmarket-api) | peer-to-peer marketplace for TCG enthusiasts | Yes (Paid) | Europe’s largest online marketplace dedicated to trading card games (TCGs); OAuth required; _Currently, not accepting applications for access to the Cardmarket API._ |

---

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

---

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

---

### [CardTrader.com](https://www.cardtrader.com/en/docs/api)

CardTrader is a European-based online marketplace specializing in the buying and selling of trading cards from popular games, including: Magic: The Gathering, Pokémon, Yu-Gi-Oh!, Flesh and Blood, Digimon, One Piece, Dragon Ball Super, Cardfight!! Vanguard, My Hero Academia, Disney Lorcana, Star Wars Unlimited, etc.

A standout feature of CardTrader is its "CardTrader Zero" service, which revolutionizes shipping by consolidating all purchases from different sellers worldwide into a single shipment, significantly reducing expenses for buyers. The platform emphasizes original cards and fraud protection, providing buyers with confidence in their purchases.

CardTrader’s API is designed to support trading functionality, including the listing of marketplace products along with pricing information.

---

### [Cardmarket API](https://help.cardmarket.com/en/cardmarket-api)

[Cardmarket](https://www.cardmarket.com/en) is Europe's largest peer-to-peer online marketplace dedicated to trading card games. It supports a wide range of games, including Magic: The Gathering, Pokémon, Yu-Gi-Oh!, Dragon Ball Super, Final Fantasy TCG, Cardfight!! Vanguard, Weiss Schwarz. The platform hosts over 500 million card offers, such as individual cards, boxes, and accessories, facilitating the sale of over 600 million cards to date.

Cardmarket offers an API interface for users to create their own apps for using Cardmarket. Only users with a commercial account can apply for and register 3rd Party apps, which need to be verified by Cardmarket.

_Unfortunately, Cardmarket is not currently accepting new applications for access to the Cardmarket API. Still, it may be worthwhile to reach out and explore potential partnership opportunities._

---
---

## Unofficial APIs & Data Dumps

Data sources that don't offer an API but provide standardized and reliable data dumps in structured formats such as CSV, XML, or JSON can still be considered dependable. These structured formats are easy to process using data orchestration workflow tools, like the ones being considered for this project, making such sources a viable and maintainable option for long-term data integration.

Data sources with an unofficial API, although seemingly viable, pose a reliability risk. These unofficial APIs can disappear overnight without prior notice, or may be placed behind an authorization wall if the owners decide that external data access is not acceptable. Such sources may be integrated into the solution with the caveat that they, and the data they provide, could become unavailable at any time, potentially having a tangible impact on the business.

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [MLB](https://www.mlb.com/) / [NFL](https://www.nfl.com/) / [NBA](https://www.nba.com/) / [NHL](https://www.nhl.com/) | Official player data and stats | Unofficial | Some endpoints are discoverable but undocumented. |
| [Gemrate](https://www.gemrate.com/) | Grading population trends, PSA volume stats | No (Web-Scraping or CSV) | Offers valuable population reports and grading activity insights. No public API, but data is structured and updated frequently. |

---

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

---

### [MLB](https://www.mlb.com/) / [NBA](https://www.nba.com/) / [NFL](https://www.nfl.com/) / [NHL](https://www.nhl.com/)

MLB.com / NBA.com / NFL.com / NHL.com don't provide a public, documented API
for developers for accessing trading card data programmatically. For accessing
sports collectible and trading card data, there are 3rd party APIs designed to
provide detailed card information and pricing data.

---
---

## Sources with no API

### DATA SOURCES UNEXPECTEDLY HAVING SOME KIND OF AN API

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [Heritage](https://www.ha.com/) | Premium auction sales data | ~No~ Yes (for partners) | ~Manual access or scraping needed. No public API.~ |
| [PSA](https://www.psacard.com/pop/) | Grading population reports and cert verification | ~No~ Yes (free / paid) | Free account has a limitation of 100 reqs/day. |

---

### [Heritage Auctions](https://www.ha.com/)

Heritage Auctions (ha.com) is the largest collectibles auctioneer and the third largest auction house in the world. Heritage is recognized as the undisputed internet leader in the collectibles field, with over 1.8 million registered bidder-members.

Heritage Auctions, apparently, offer an API specifically through its Heritage Images division, which provides access to an extensive library of images and metadata related to collectibles. This API is intended for established sales partners under contract with Heritage, and is not publicly available for general third-party use. For general Heritage Auctions marketplace or auction data, there is no public API available for third-party integrations.

Extensive interactive documentation is available for exploration and implementation at [https://api.heritage-images.com/v1/api-docs/](https://api.heritage-images.com/v1/api-docs/).

| Feature               | Details                                                   |
|-----------------------|-----------------------------------------------------------|
| API Availability      | Yes, but only for Heritage Images partners under contract |
| Public Access         | No, requires sales agreement                              |
| API Functionality     | Access to image files and metadata                        |
| Documentation         | Available online for partners                             |
| Usage Restrictions    | No caching or storing data, image availability checks     |

API access requires contacting Heritage’s sales department for login credentials.

---

### [PSA](https://www.psacard.com/pop/)

Professional Sports Authenticator (PSA) is the largest and most trusted third-party grading and authentication service for trading cards and collectibles. The PSA Population Report (PSA Pop) provides detailed, trusted data on the number and grades of collectibles PSA has certified. The tool is essential for collectors and investors to understand item rarity and market value. Updated daily, the database offers a thorough overview of grading statistics across all categories.

PSA does offer a public API, available at [https://www.psacard.com/publicapi/documentation](https://www.psacard.com/publicapi/documentation). Free accounts are allowed up to 100 API calls a day, and paid plans exist for higher daily limits. API offers access to certification info, population report data, auction prices, price guides, and more, with the full specification available at [https://api.psacard.com/publicapi/swagger](https://api.psacard.com/publicapi/swagger)

Community-built wrappers for the API exist, enabling integration more seamlessly, such as [fetch-psa-api (Python)](https://github.com/brad-newman/fetch-psa-api) for retrieving card details by cert number.

Web scrapers for harvesting population report and auction price data also exist ([PSA Cards Web Scraper](https://github.com/ChrisMuir/psa-scrape)), though PSA recommends using the official API for stability

---


### DATA SOURCES WITH 3RD PARTY / UNOFFICIAL COMMUNITY APIS

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [BGS (Beckett)](https://www.beckett.com/grading/) | Grading info and population reports | No | No public API; may require scraping or third-party access; unofficial community effort exists. |
| [FanGraphs](https://www.fangraphs.com/) | Baseball prospecting and advanced stats | No | CSV export and well-structured HTML. Good for scouting. |
| [Sports Reference](https://www.sports-reference.com/) (BBall&#160;/&#160;Football&#160;/&#160;Hockey) | Player stats, bios, history | No | Well-structured HTML for parsing. |

---

### [BGS (Beckett)](https://www.beckett.com/grading/)

[Beckett Grading Services](https://www.beckett.com/grading/) provide professional grading, authentication, and encapsulation for sports, gaming, and non-sports cards. They professionally grade trading cards on condition, centering, edges, corners, and surface quality to assign a numeric grade. Beckett is known for consistency, accuracy, and integrity in grading, and the company has been a trusted name in collectibles for over 40 years.

There is no mention of an API for programmatic access to their grading data, set checklists, or population reports.

However, there are community efforts to create APIs that interact with Beckett's data. For instance, a GitHub repository named [beckett-data-api](https://github.com/ecds/beckett-data-api) exists, which aims to provide an API for Beckett data. It's an unofficial project and may not be fully reliable, nor up-to-date.

---

### [FanGraphs](https://www.fangraphs.com/)

FanGraphs is a comprehensive baseball statistics and analysis website focused on Major League Baseball (MLB) and Minor League Baseball. It provides in-depth sabermetrics, advanced statistical data, projections, graphs, and tools for analyzing player and team performance. FanGraphs is widely used by baseball fans, analysts, fantasy players, and professionals for its rich data and insightful analysis, making it a leading resource in the baseball analytics community.

FanGraphs offers some options for accessing its data for third-party integration, though not through a formal, fully supported API. Unofficial and undocumented API endpoints can be found by inspecting the browser network traffic, and several Python packages, such as [`pybaseball`](https://github.com/jldbc/pybaseball/blob/master/docs/fangraphs.md) and [`fangraphs`](https://pypi.org/project/fangraphs/), are designed to scrape and retrieve data from FanGraphs. However, all of these methods are subject to change and are not officially supported.

---

### [Sports Reference](https://www.sports-reference.com/) (BBall/Football/Hockey)

Sports Reference is a network of websites providing sports statistics, history, and records for various sports. These sites aim to "democratize data" and offer comprehensive information for sports fans. The network includes sites dedicated to baseball, football, basketball, hockey, soccer, college basketball, and college football. Relation to trading sports cards is by providing the underlying sports statistics and data used to evaluate players, which in turn affects the value and desirability of their trading cards.

Sports Reference does not provide an official, publicly supported API due to licensing restrictions with their data providers. However, there is a popular unofficial Python API called [`sportsreference`](https://pypi.org/project/sportsreference/) _([API Reference](https://sportsreference.readthedocs.io/en/stable/))_ that allows developers to programmatically pull statistics and other sports data.

---


### DATA SOURCES HAVING NO API FOUND, CONTRARY TO THE INITIAL REPORT

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [Alt.xyz API](https://developers.alt.xyz/) | Historical price trends and card indices | ~Yes~ _(no API found)_ | Strong market analytics and trend data. Requires developer registration. |
| [Sports Card Investor API](https://www.sportscardinvestor.com/) | Card catalog, images, pricing | ~Yes (Paid)~ _(no API found)_ | API access via premium plan. Good for retail card price lookups. |
| [Card Hedge API](https://www.cardhedger.com/) | Card prices, grading data, trends | ~Yes (Paid)~ _(no API found)_ | Promising data source for price comps and graded card analytics. |

---

### [Alt.xyz API](https://developers.alt.xyz/)

_There is no developers section on https://www.alt.xyz/ website, nor is
https://developers.alt.xyz/ URL active. It seems there is no public API
available here._


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

---
---

### DATA SOURCES WITH NO API

Data sources with no API and no structured data dumps pose a range of challenges and risks that the product needs to take into account. These include technical issues affecting the reliability, sustainability, and maintenance of data extraction, as well as legal concerns related to collecting data without the owners’ consent. The product should aim to avoid critical dependencies on such sources, or pursue agreements that permit the data to be used legally and reliably.

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [130point](https://130point.com/) (Unofficial) | Sales comps across marketplaces | No | No public API. Scraping or data parsing may be needed. |
| [Goldin](https://www.goldin.co/) / [PWCC](https://www.pwccmarketplace.com/) / [REA&#160;Auctions](https://www.robertedwardauctions.com/) | Premium auction sales data | No | Manual access or scraping needed. No public API. |
| [SGC](https://www.gosgc.com) | Grading info and population reports | No | No public API; may require scraping or third-party access. |
| [CGC Cards](https://www.cgccards.com/) | Graded card verification and reports | No | No API available. Web scraping or OCR might be options. |
| [TCDB (Trading Card Database)](https://www.tcdb.com/) | Card images, checklists, and variations | No | Community-driven data. No public API but structured data. |
| [COMC](https://www.comc.com/) | Images, inventory, some pricing | No | Data available via website structure; scraping needed. |


---

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

---

### [Goldin](https://www.goldin.co/)

Goldin is a top-tier, full-service platform for serious collectors and investors—offering auctions, listings, authentication, grading, and secure storage, all supported by a major auction pedigree and PSA infrastructure. The official Goldin app and website provide robust features for buying, selling, vaulting, and managing collectibles directly through their own platforms, but Goldin does not publicly offer an API or developer portal for external programmatic access.

For a possible integration with Goldin’s marketplace or data, it may be worthwhile to reach out and explore potential partnership opportunities, as they must have an internal API for supporting their mobile apps.

---

### [PWCC](https://www.pwccmarketplace.com/)

PWCC Marketplace (now known as Fanatics Collect) is a major player in the high-end trading card, memorabilia, comic, video game, numismatic, and pop‑culture auction space. It offers secure storage, auctions, fixed-price sales, breaking services, and lending mechanisms, all underpinned by Fanatics' infrastructure.

Their official communications and profiles emphasize a secure, transparent marketplace and vaulting services for trading cards and collectibles but do not mention any developer API or data access endpoints. For a potential integration, contacting PWCC exploring partnership opportunities is an option.

---

### [REA Auctions](https://www.robertedwardauctions.com/)

Robert Edward Auctions is a premier auction house renowned for handling some of the most valuable and iconic sports collectibles, especially baseball cards, offering trusted, professional auction services to collectors and investors worldwide.

Their official website and related resources do not mention any developer API or programmatic data access. For data integration with REA, it would be best to contact them directly to inquire about any private or partner API offerings.

---

### [SGC](https://www.gosgc.com)

SGC are a professional card grading and authentication company that specializes in the sports industry with the distribution of trading cards and accessories for sale online to customers.

SGC also has a mobile app that allows collectors to submit cards for grading and track their submissions, which means there is an API of some kind existing. It could be worth exploring more through a direct contact.

---

### [CGC Cards](https://www.cgccards.com/)

CGC Cards specializes in the expert grading, authentication, and encapsulation of trading cards. Their services include grading and authentication, encapsulation and cards sealing, population reports, and collectors' registry.

CGC Cards provides an API, but restricted to authorized dealers, providing access to certain services programmatically. For general users, public tools like certification verification and population reports are available on their website only.

---

### [TCDB (Trading Card Database)](https://www.tcdb.com/)

The Trading Card Database (TCDB) is a comprehensive, crowdsourced archive dedicated to trading cards and all related aspects of the hobby. It serves as a searchable resource where collectors and enthusiasts can find detailed information on cards by year, manufacturer, player or character name, and team.

The TCDB does not currently offer a public API for third-party integrations.

---

### [COMC](https://www.comc.com/)

COMC is the world’s largest online marketplace for trading cards, including sports cards, trading card games, and non-sports cards, with suggested prices and historical data to help sellers set competitive prices and buyers make informed decisions.

There is no official documentation or mention of an API for developers to access COMC’s marketplace data or services programmatically.

---


### ADDITIONAL SOURCES FOUND DURING RESEARCH W/O API

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [AP Grading](https://www.apgrading.net/) | ... | ... | ... |
| [SellThePeak](https://sellthepeak.com/) | tools and resources for determining the value of sports cards, especially through accurate eBay Best Offer Accepted prices | No | Ajax-driven, hard to web-scrape; if AJAX calls can be reverse-engineered, there could be a chance |
| [CardSnoop](https://cardsnoop.com) | sales data across various market places for sports cards | ? (_TBD_) | focuses on sales rather than listings; _Site currently not accessible; could be defunct_ |


---

### [AP Grading](https://www.apgrading.net/)

Alpha Professional Grading is the largest third-party authentication company in Europe for grading cards, comics, and boosters, based in Schüttorf, Germany. They specialize in grading Pokémon, sports, and Yu-Gi-Oh! cards, but also grades other TCGs. It was the first German grading GmbH and has gained international acceptance for its grading services.

The company utilizes high-quality ultrasound technology and unique cases with security engraving to ensure careful treatment of trading cards and a globally recognized result. Their special tools locate even the smallest scratches or creases on a card.

AP Grading does not appear to offer a developer API or integration services.

---

### [SellThePeak](https://sellthepeak.com/)

SellThePeak is a platform that downsized from being a trading platform, while now it offers Free Sports Card Price Check Lookup Tool for trading cards only. It also offers a Discord server where collectors and investors can discuss sports card topics and ask questions. It does not offer a readily apparent or documented API.

---

### [CardSnoop](https://cardsnoop.com)

_Site currently not accessible; could be defunct_

---
---

## TECHNICAL ASPECTS OF WEB SCRAPING

Web scraping is, technically, never a stable solution. If the structure of a scraped website changes, the scraping setup can break overnight. As such, web scraping should be considered a constantly moving target that requires continuous monitoring and immediate reaction when a change occurs. Any structural modification may cause the scraper to fail, requiring the scraping logic to be immediately updated to match the new layout.

That said, recent advances in AI-driven tools are beginning to change this landscape, offering more adaptive approaches to web data extraction that are less dependent on rigid structural assumptions. Still, this remains relatively uncharted territory, introducing its own set of risks around timelines and budgets, compared to classic web scraping solutions which use headless browsers and CSS selectors or XPath expressions to locate and extract data.


## LEGAL ASPECTS OF WEB SCRAPING

Web scraping is typically against the terms of service of most websites and may sometimes even violate copyright law. Not that it prevents people from scraping websites in general, and it may have no repercussions for hobby projects or very small-scale businesses that stay under the radar. Still, if a business takes off and becomes successful and popular, unauthorized or illicit data scraping will likely not go unnoticed.

If possible, arranging authorization deals with the respective data owners as soon as it becomes business-feasible may help avoid unnecessary disputes and could even open up the possibility of gaining structured access to the data through an API or via CSV, XML, or JSON data dumps.
