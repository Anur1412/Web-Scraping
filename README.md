# Web-Scraping

import urllib.request
from bs4 import BeautifulSoup


class Scraper:
    def __init__(self, site):
        self.site = site

    def scrape(self):
        r = urllib.request.urlopen(self.site)
        html = r.read()
        parser = "html.parser"
        sp = BeautifulSoup(html,parser)
        for tag in sp.find_all("a"):
            url = tag.get("href")
            if url is None:
                continue
            if "articles" in url:
                print("\n" + url)

news = "https://abcnews.go.com/Business/wireStory/faa-us-airports-billion-pandemic-relief-78429944?cid=clicksource_4380645_1_heads_hero_live_headlines_hed"
Scraper(news).scrape()

