# Final Project Plan
Sara Rosenau  
shr144@pitt.edu  
2/11/2025

## Algospeak on BlueSky
My current research projects for my first Comps paper concerns *algospeak*, a method of using language to avoid algorithmic suppresion. This includes replacing terms like "kill", "sex", and "gun" with terms like "unalive", "seggs", and "pew pew" respectively. My Comps study only looks at TikTok data, but I would like to expand this to other platforms in the future.  

I would like to look at BlueSky for several reasons:  
- BlueSky is primarily *not* algorithmically driven, a rarity for social media sites these days.
- It has a free API at possibly scraper packages out there already.
  - [This one](https://github.com/micahflee/skyscraper) exists but it's in JavaScript
- A lot of my survey respondants came from BlueSky

### Data
- Data would look like individual posts mined from a [search feed](https://bsky.app/search?q=unalive) hopefully
- Cleaning would be turning mined content into a dataframe containing username, post date, content of post, and other metadata such as amount of likes and comments if I see fit.
  - This may be in the form of an annotated corpus
- I don't believe there's any publically available corpora for Bluesky, so I'd have to scrape my own


### Analysis
- My research question for algospeak in general is "why do people react so negatively to algospeak?", so I could potentially do some topic modelling
  - I have done topic modelling a few years ago for a Digital Humanities seminar but I know much more about computational methods now
- I can also do a more traditional sociolinguistic/discourse analysis approach, but with scraped data
  - The question this always presents is how to do such with large amounts of data. There's a reason qualitative analysis uses smaller datasets.

### Presentation
- I don't have anything specific for this yet other than your typical Powerpoint presentation

