# Progress Report

## Report 0 - 2/11/2025
- Decided on going with the algospeak route because the idea of trying to wrangle other corpora that don't really have the info I need gives me hives. Also, I might be able to use the result of this for dissertation work!
- Created the repository with all the required elements

## 1st Progress Report - 2/25/2025
### Figuring out the API
The most difficult part here was figuring out the Bluesky API. I used the ATProto Python package as detailed in the [Bluesky documentation here.](https://docs.bsky.app/docs/get-started) However, beyond the most basic tasks like making a post and following other users, the documentation is very sparse. To make things more annoying, the documentation is spread over multiple websites such as [one for the protocol SDK](https://atproto.blue/en/latest/) and [one for the Python specific version](https://atproto.blue/en/latest/). The most helpful website was a github of Python specifc examples of code that I could reverse engineer, such as [this one to print out your following feed.](https://github.com/MarshalX/atproto/blob/main/examples/home_timeline.py)

Once I figured out how to do that much, I found the `app.bsky.feed.searchPosts` method [here](https://docs.bsky.app/docs/api/app-bsky-feed-search-posts), which works well for my desire to search for a given term and scrape the resulting posts. Again, there's very little documentation on what it actually does. After some trial and error, I found that this method returns me a Response type object built on the Pydantic library. I then found a way to convert this into a dictionary using the [`.model_dump()`](https://docs.pydantic.dev/2.10/api/base_model/#pydantic.BaseModel.model_dump) method. From there, it was pretty easy to get the data that I wanted by first printing out some posts, and then putting them into a dataframe [as seen here.](https://github.com/Data-Science-for-Linguists-2025/Algospeak-on-Bluesky/blob/main/getting_bsky_data.ipynb) 

### The Data
At this point, I'm just building a dataframe/csv of posts that include the five algospeak terms that I'm using in my other research project, seen in the table below. The dataframe contains the text of the post, the author, the date posted, and metadata that signals uptake such as likes, reposts, replies, and quote posts. You can see the dataframe in the [Jupyter Notebook](https://github.com/Data-Science-for-Linguists-2025/Algospeak-on-Bluesky/blob/main/getting_bsky_data.ipynb) or [the CSV.](https://github.com/Data-Science-for-Linguists-2025/Algospeak-on-Bluesky/blob/main/algospeak_top_posts.csv) 

| Algospeak Term    | Gloss                 |
| ----------------- | --------              |
| unalive           | kill, murder, suicide |
| seggs             | sex                   |
| grape             | rape                  |
| palm-colored      | white                 |
| watermelon        | Palestine             |

As you might notice, some of the above terms are just normal words. Going forward, I will code the data for a couple things, including:
- If they are using the term as algospeak
- Are they using it in earnest or just talking about it (use-mention distinction)
- How are they using it (positively, negatively, etc.)

Right now, I have 148 posts, but I may collect more if I need to.

### Data sharing plan 
Since my data comes from publically available sources, I believe it is necessary to keep my data public as well. Currently, I've shared [the entire CSV](https://github.com/Data-Science-for-Linguists-2025/Algospeak-on-Bluesky/blob/main/algospeak_top_posts.csv) on my GitHub Repo and I'll keep it up as I edit it. 
