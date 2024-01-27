# Sitemap

Search Engine optimization is not mandatory but it's a must for those who wants to have more visitors on there website. As based on SEO an application will be listed at top or below in the results of the search, worst it may not even be listed even though its very relevant to user search.

- There are multiple activities to do for SEO improvements:
- A way is to have right [robot.txt](https://vk2k19.github.io/readme/robots)
- Another way is to have a sitemap besides other ways. Let's talk about sitemaps.

## What is a sitemap?

Simply put a sitemap is collection of URLs that your application have and other information about your organization and these URLs.

## Example sitemap

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    <url>
        <loc>https://www.example.com/url1</loc>
        <lastmod>2024-15-1</lastmod>
        <changefreq>weekly</changefreq>
        <priority>0.8</priority>
    </url>
    <url>
        <loc>https://www.example.com/page3</loc>
        <lastmod>2024-15-1</lastmod>
        <changefreq>weekly</changefreq>
        <priority>0.8</priority>
    </url>
    <!-- Entries for other pages -->
</urlset>

```

## Content of sitemap xml

XML includes various tags designed to represent site structure and information, aiding crawlers in prioritizing and crawling pages efficiently. However, it's important to note that while XML assists in facilitating the crawling process, it does not directly contribute to increasing the ranking of a page in search engine results. Ranking factors are determined by numerous other elements, such as content quality, relevance, backlinks, and user engagement metrics, which XML alone does not influence.

### urlset

The "urlset" tag is obligatory as it encapsulates the file and denotes the current protocol standard being referenced.

### url

The "url" tag is essential as it serves as the parent tag for each URL entry, encapsulating the following tags to provide information about each URL.

#### loc

The "loc" tag is indispensable as it specifies the location of the page and is nested under the "url" tag. The URL typically begins with the protocol (e.g., "http", "https").

#### lastmod

The "lastmod" tag is optional and contains the date when the page content was last modified for the given URL. The value of "lastmod" should adhere to a valid W3C format Date, which allows for the omission of time.

#### changefreq

This represents the anticipated frequency at which page content may change. However, it's important to note that bots may have their own interpretation of change frequency, and they may not strictly adhere to the specified intervals for crawling. For instance, even if the change frequency is set to 'Hourly', the crawler might not execute precisely every hour; there could be a slight delay of close to an hour or more before the crawling occurs.

- always
- hourly
- daily
- weekly
- monthly
- yearly
- never

#### priority

The "priority" tag is an optional element within a sitemap XML. It specifies the priority of scanning relative to other pages listed in the sitemap. The value ranges from 0.0 to 1.0, with a default value of 0.5. This value enables crawlers to prioritize the crawling of one URL over another based on their assigned priority level.

## References

- [Auto generate the sitemap](https://www.xml-sitemaps.com/)
- [About Sitemaps](https://www.sitemaps.org/)
- [Google doc on sitemap](https://developers.google.com/search/docs/crawling-indexing/sitemaps/overview)
- [Wiki sitemap](https://en.wikipedia.org/wiki/Site_map)
