# Data Sources

## Data Sources Classification

### Sources with an API

Data sources providing an official API, whether free or paid, are the best foundation to build a business upon. They offer reliability, dependability, and a straightforward way to access data for further processing to meet the product’s needs. Such sources are clearly considered long-term viable options.

| Source Name | Use Case | API Available | Notes |
| ----------- | -------- | ------------- | ----- |
| [eBay API](https://developer.ebay.com/) | Sales data (real-time & historical) | Yes | Robust API with filters for sport, card year, and grade. OAuth required. |
| [Alt.xyz API](https://developers.alt.xyz/) | Historical price trends and card indices | Yes | Strong market analytics and trend data. Requires developer registration. |
| [Pokémon TCG API](https://pokemontcg.io/) | Non-sports card data (Pokémon) | Yes | Robust and free. Great for Pokémon collectors. |
| [Sports Card Investor API](https://www.sportscardinvestor.com/) | Card catalog, images, pricing | Yes (Paid) | API access via premium plan. Good for retail card price lookups. |
| [Card Hedge API](https://www.cardhedger.com/) | Card prices, grading data, trends | Yes (Paid) | Promising data source for price comps and graded card analytics. |


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


#### TECHNICAL ASPECTS OF WEB SCRAPING

Web scraping is, technically, never a stable solution. If the structure of a scraped website changes, the scraping setup can break overnight. As such, web scraping should be considered a constantly moving target that requires continuous monitoring and immediate reaction when a change occurs. Any structural modification may cause the scraper to fail, requiring the scraping logic to be immediately updated to match the new layout.

That said, recent advances in AI-driven tools are beginning to change this landscape, offering more adaptive approaches to web data extraction that are less dependent on rigid structural assumptions. Still, this remains relatively uncharted territory, introducing its own set of risks around timelines and budgets, compared to classic web scraping solutions which use headless browsers and CSS selectors or XPath expressions to locate and extract data.


#### LEGAL ASPECTS OF WEB SCRAPING

Web scraping is typically against the terms of service of most websites and may sometimes even violate copyright law. Not that it prevents people from scraping websites in general, and it may have no repercussions for hobby projects or very small-scale businesses that stay under the radar. Still, if a business takes off and becomes successful and popular, unauthorized or illicit data scraping will likely not go unnoticed.

If possible, arranging authorization deals with the respective data owners as soon as it becomes business-feasible may help avoid unnecessary disputes and could even open up the possibility of gaining structured access to the data through an API or via CSV, XML, or JSON data dumps.
