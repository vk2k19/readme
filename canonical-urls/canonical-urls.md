# Boost Your Website Rankings with Canonical URLs

## Understanding the Power of Canonical URLs

Duplicate content on the internet doesn't just include pages with identical versions. It also encompasses situations where multiple URLs lead to the same content, regardless of whether it's intentional or unintentional.

Your pages can have duplicates for several reasons. Here are some examples:
- Support both http and https urls 
- Offering pages with or without "www."
- Allowing inconsistent slashes like having url ending with or without "/"
- Supporting non-case-sensitive URLs
- Having links to same page urls with and without query parameters
- Having similar content for example having seprate pages for same product with variations in color or sizes, etc.

## The Impact of Duplicate Content on Your Website

This duplication can be a real buzzkill for your website! When search engines find the same or similar pages on your site, they might show multiple links for the same thing, which confuses users and weakens your ranking power. Remember, lower ranking means less visibility, so keeping your content unique and focused is key to getting your pages seen.

While we've seen the importance of deduplication, removing pages or URLs overnight might not be the best first step. But fear not! We can take a simple, effective approach that immediately improves your page results and performance,

## Get Started with Canonical URLs

A canonical URL is a piece of code within a webpage that tells search engines which version of the page is the "preferred" one for indexing. This helps avoid issues where multiple URLs with the same or similar content appear in search results, potentially harming your website's ranking and confusing users.

### Adding a Canonical URL: Simple Steps to Boost Ranking

1. Locate the <head> section of your page's HTML code. This is typically found between the <html> and </html> tags.
1. Inside the <head> section, add a <link> tag with the following attributes:
    1. rel="canonical": This tells search engines which URL is the preferred version of the page.
    1. href="URL_OF_PREFERRED_PAGE": Replace URL_OF_PREFERRED_PAGE with the actual URL of the page you want search engines to consider the primary version.

### Additional tips:

- Ensure the specified URL is accessible and crawlable by search engines.
- Only use one canonical URL per page.
- Consider using a plugin for your content management system (CMS) if available. This can simplify the process of adding canonical URLs.


```html
    <link rel="canonical" url="https://example.com" />
```

I hope this insight helps you with SEO and improves site performance.

***

[&#128218; Go back to readme list](../) ¦ [&#x1F3E0; Vijayendra's Protfolio &#124; vk2k19](/)
