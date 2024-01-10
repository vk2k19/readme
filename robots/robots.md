# Reading & Writing Robots.txt

Robots, also known as spiders, ants, bots, search engines, and crawlers, play a crucial role in web crawling. To control their access and actions on your site, you can employ the robots.txt file.

[!TIP] If you intend to create a robots.txt file for benevolent bots, place it at the root level

> https://www.example.com/robots.txt

## Understanding Robots.txt

Robots.txt uses straightforward rules to communicate the owner's intentions regarding bot access and restrictions to pages, paths, and content. 

A rule comprises:

- Bot(s) for which this rule is (user-agent)
- access or restrictions to path(s) (allow/disallow) 
- re crawl gap in seconds (crawl-delay)
- Master list of all pages/paths (sitemap)
- Comment and spaces for additional meaning and ease of human reading

## Syntax

Typically, rules in robots.txt consist of directives as field and value pairs, separated by a colon and space for better readability. Comments provide additional insights.

> \<Field>: \<value> # comment


[!CAUTION] Bots may interpret these syntaxes differently, and not all directives are universally supported.

### User-agent

``` txt
User-agent: user-agent-string 
```

The user-agent is the first piece of information for the rules, indicating which bots should adhere to the rule.

For Example:

``` txt
User-agent: * # Rules for all bots
```

``` txt
User-agent: google # Rules only for googleBot
```

### Allow

Allow instructs the bot on paths it should access and interpret for indexing. Paths are relative links. Multiple allows are possible in one rule.

``` txt
Allow: / # allow all path
```

[!INFO] paths are case-sensitive and support wildcards (*, $ , ?).

### Disallow

Disallow instructs bots to avoid indexing specific paths. Paths are relative links, and multiple disallows are possible in one rule.

``` txt
Disallow: / # disallow all path
```

[!INFO] paths are case sensitive


### Sitemap

List your sitemap, a comprehensive list of paths your application supports. Multiple disallows are possible and are usually added post all rules.

``` txt
Sitemap: https://www.example.com/sitemap.xml # path must be absolute path
```

### Crawl-delay

Bots should wait for specified seconds before re-accessing the site.

``` txt
Crawl-delay: 20 # Bing bot waits for 20 second to recrawl.
```

[!HELP] Not supported by google

## EXAMPLE RULES

```txt
User-agent: GoogleNews
Disallow: /private-news/ # GoogleNews bot should not go through page(s) starting with https://www.example.com/private-news/

User-agent: *
Allow: / # All bots have access to all pages
Disallow: /*.gif$ # Do not access gif images

# [!HELP] All bots are allowed access to all pages by default so above rule can be omitted

Sitemap: https://www.example.com/sitemap.xml
```

## BEST PRACTICE

- Use Robots.txt to exclude media content from being indexed.

> [!NOTE] do not exclude media if it adds meaning to the page as bot also need to understand your page for search ranking.

- Use Robots.txt to exclude path which should not be indexed.

> [!CAUTION] path/pages might still be index if other pages have references to it and they are part of indexing.

- Use if you want to restrict access to content.
- decrease visits by bots saving your page visiting budget.
- hide private pages from indexing.

> [!IMPORTANT] You may not need robots.txt if all contents should be indexed.

## REFERENCES

[Why Robots.txt matters for SEO](https://www.semrush.com/blog/beginners-guide-robots-txt/)

[Read about wildcards at an article by kathryn owens](https://www.seerinteractive.com/insights/how-to-read-robots-txt)

[Google's article on robots.txt and there interpretation of it](https://developers.google.com/search/docs/crawling-indexing/robots/robots_txt)

[See if robots.txt can be processed by google bots](https://support.google.com/webmasters/answer/6062598?hl=en)

[Bing's article on robots.txt](https://www.bing.com/webmasters/help/how-to-create-a-robotstxt-file-cb7c31ec)

[Validate your robots.txt at Bing's](https://www.bing.com/webmasters/help/robotstxt-tester-623520ca)


***

[&#128218; Readme list](../) ¦ [:arrow_backward: Why we need robots.txt](./readme.md) ¦ [&#x1F3E0; Vijayendra's Protfolio &#124; vk2k19](/) 
