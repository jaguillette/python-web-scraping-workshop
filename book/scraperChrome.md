# Chrome Scraper Tool

To start, we won't be using Python at all. We'll be using a free browser extension for Google Chrome that I find helpful for scraping data from a single page of data that isn't friendly to copying and pasting.

The tool is called [Scraper](https://chrome.google.com/webstore/detail/scraper/mbigbapnjcgaffohmbkdlecaccepngjd), making it very difficult to find in the Chrome app store if you don't have that link.

In Chrome, with the tool installed, let's take a look at [US state birds](https://en.wikipedia.org/wiki/List_of_U.S._state_birds). Say you want to throw together a quick data viz about how many different states have the same state bird. Sometimes you can kind of copy and paste data from a table on a website to a spreadsheet, but it doesn't always work. In those cases, this scraper extension can save you some time, once you know how to use it.

Start by right clicking on one of the state name links and clicking on the new "Scrape similar" option. You should see a list of names and wiki links, which is a great start.

Scraper will guess an Xpath selector that seems like it will select a lot of similar content. Sometimes it'll do what you want right away, but more often than not you'll need to modify your selectors.

Xpath selectors are a syntax for selecting parts of an HTML document, and they're what Scraper uses to figure out what to select by default. You may want to reference an [Xpath cheat sheet](https://devhints.io/xpath) when using the tool.

You can also change the selector from Xpath to jQuery, which uses syntax that's more like css selectors, and which makes it easier to use the attributes of HTML tags in selecting content on a page. When a page has different kinds of content indicated by a class or id attribute, I find it easier to use jQuery selectors. When it doesn't, and you need to select the nth of some HTML tag on a page, I find it easier to use XPATH selectors. Taking a look at how a website works and figuring out the best tool for the job is a key part of web scraping, so let's take a look under the hood to see how this table is structured.

1. `//table[1]/tbody/tr/th/a`
2. `//table[1]/tbody/tr`
3. `table.wikitable > tbody > tr` (jquery)
    1. `th`
    2. `td[1]`
    3. `td[1]/a/@href`
    4. `td[2]`
    5. `td[3]/a/img/@src`
    6. `td[4]`
