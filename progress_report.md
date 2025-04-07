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


## 2nd/3rd Progress Report - 4/7/2025
Unfortunately other algospeak work got in the way of this algospeak work (my comps paper...), so this will kind of be a mish mash of both progress reports together. 

### Qualitative coding
For this step, I took the data I gathered for the first project report and qualitatively coded them by hand. There isn't really a good way to do this via Python, so I just used Excel unfortunately. In this project, I am looking at how people use algopseak, so my the codes listed in the mention_code column of my CSV/dataframe are split up into four categories of use. 
| Code      | Meaning                                                                                                               |
|-----------|-----------------------------------------------------------------------------------------------------------------------|
| a         | algospeak - The term is being used to censor another term                                                             |
| m         | mention - The term is being mentioned as an algospeak term but not used to censor anything. Can also stand for "meta" |
| n         | not algospeak - The term is not being used as an algospeak term                                                       |
| o         | other - Term is not present or something else                                                                         |

I explore the outcomes of this a little more in [my jupyter notebook](https://github.com/Data-Science-for-Linguists-2025/Algospeak-on-Bluesky/blob/main/coded_data_viz.ipynb). Mostly, it shows that there isn't that much metadiscourse on algospeak in this dataset, and over half of the dataaset is not using the term in an algospeak way. These results are still useful, as it shows that algospeak may not be as prevalent on Bluesky as it is on other social media platforms. That being said, if I want to do any computational analysis on it, I'm going to need more data that actually applies.

### Topic Modeling
At this point, I want to use this project as a bit of a proof of concept on if I can use topic modeling to guide sociolinguistic analysis. With the data I have, it's honestly not in a great state to do topic modelling on. I try to do a bit of topic modeling in [this jupyter notebook](https://github.com/Data-Science-for-Linguists-2025/Algospeak-on-Bluesky/blob/main/algospeak_topic_modeling.ipynb) but I was only working with 30 posts which is really not enough. However, the NMF method does seem to be showing some promise even with the really small dataset.

Going forward, I believe that I might need to get a larger dataset as doing the qualitative coding really didn't take all that long. I might go back and say get a dataset of ~200 posts for solely "unalive" as that's the most unambiguous term, code those posts, and then do some topic modelling on that. This should probably take only a couple hours so I can get this done before the project presentation.

### Files that have been modified/added
- [algospeak_top_posts.csv](https://github.com/Data-Science-for-Linguists-2025/Algospeak-on-Bluesky/blob/main/algospeak_top_posts.csv) - Existing, Added the column for the qualitative coding
- [coded_data_viz.ipynb](https://github.com/Data-Science-for-Linguists-2025/Algospeak-on-Bluesky/blob/main/coded_data_viz.ipynb) - New continuing, for some data exploration and vizualization
- [algospeak_topic_modeling.ipynb](https://github.com/Data-Science-for-Linguists-2025/Algospeak-on-Bluesky/blob/main/algospeak_topic_modeling.ipynb) - New continuing, some topic modeling on the data that I currently have

### Data sharing
I have decided to use the CC-BY-SA license, which I've just copied to [LICENSE.md](https://github.com/Data-Science-for-Linguists-2025/Algospeak-on-Bluesky/blob/main/LICENSE.md). I've chosen this licesnse because it is very open to people using my project and modifying it, but it does not allow for commercial uses. The thought of people using this project for a for-profit endeavor makes me a little uncomfortable so I'm not allowing it for now. However, if people want to use my code for their own personal research or scholarly endeavors, I welcome that! I, however, would want some attribution for my work. 