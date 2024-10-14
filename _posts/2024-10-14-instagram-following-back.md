---
title: Who’s Not Following You Back on Instagram? Here’s How to Find Out Safely
date: 2024-10-14 05:33:00 -500
categories: [Technology, Coding]
tags: [Tech]
---

### Introduction
Have you ever noticed a sudden drop in your follower count and wondered who is unfollowing you? Or perhaps you’re curious about identifying who isn’t truly a friend. I certainly was, so I did some digging into ways I could do this using Python. The primary objective is to retrieve your follower and following lists, then comparing the two lists to find out who isn’t following you back.

### Findings
There are several methods for gathering your Instagram follower data. One approach is to use the Instagram API, which allows you to retrieve follow and following lists. However, Instagram’s API has become more restrictive, and official access requires approval for non-public data. Using bots or scrapers can trigger Instagram’s security measures which can potentially lead to Instagram blocking or restricting access so caution is advised. 

Another option is to use web scrapers like Selenium to scrape the Instagram web interface for data. However, this approach may also trigger Instagram’s security measures.

The safest and most convenient method is to use the [instaloader](https://instaloader.github.io) Python library. Instaloader can fetch your followers and following lists without the need for Selenium or web scraping. Unlike Selenium, which requires logging into the site and simulating user actions, Instaloader utilizes Instagram’s public data, reducing the likelihood of triggering security features. Below are the steps on how to use Instaloader and the script you can run.

### Code

1. Install instaloadeer
```bash
pip install instaloader
```

2. Create Python script
```python
import instaloader

# Create an instance of Instaloader
L = instaloader.Instaloader()

# Login to your Instagram account
L.login("your_username", "your_password")

# Load the profile
profile = instaloader.Profile.from_username(L.context, "your_username")

# Fetch the list of followers
followers = set(follower.username for follower in profile.get_followers())

# Fetch the list of followees (people you are following)
followees = set(followee.username for followee in profile.get_followees())

# Find the difference between the two sets
not_following_back = followees - followers

print("Users not following you back:", not_following_back)
```

### Conclusion
• Instaloader is safe, more efficient, and likely won’t trigger security measures.

**Pros:**
• Instaloader uses Instagram’s public data, which reduces the risk of being flagged.
• It doesn’t require scraping the website using a browser, so it’s more efficient and clean.

**Cons:**
• You still need to log in to get your followers and followees, but the API usage is less likely to trigger security measures compared to browser automation.