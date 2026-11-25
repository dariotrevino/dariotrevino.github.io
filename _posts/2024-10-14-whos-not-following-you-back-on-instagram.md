---
title: Who’s Not Following You Back on Instagram? Here’s How to Find Out Safely
description: "See who doesn't follow you back on Instagram: the no-code, no-password way with Follower Analyzer, plus the original Python script using Instaloader."
date: 2024-10-14 05:33:00 -0500
categories: [Technology, Coding]
tags: [Tech]
redirect_from:
  - /posts/instagram-following-back/
---

### Introduction
Have you ever noticed a sudden drop in your follower count and wondered who is unfollowing you? Or perhaps you’re curious about identifying who isn’t truly a friend. I certainly was, so I did some digging into ways I could do this using Python. The primary objective is to retrieve your follower and following lists, then compare the two lists to find out who isn’t following you back.

### Update (November 2026): A Safer Way, No Code Needed
Since writing this post, I built [Follower Analyzer](https://followeranalyzer.io), a free web app that does the same comparison without any code. It fixes the biggest problems with the script below:

- **No password.** The script logs in to Instagram with your username and password, typed in plain text into a file. Logging in through a third-party tool is exactly the kind of thing that can get an account flagged. Follower Analyzer never asks for your password and never touches your account. It reads the data export Instagram itself gives you.
- **Your data stays on your device.** The export is read in your browser and never uploaded anywhere. The only thing on the page that uses the network is Google Analytics for visit counts, and it sees nothing from your export.
- **No setup.** No Python, no `pip install`, no terminal. Drop in the ZIP from Instagram and you get results in seconds.
- **More than one list.** The script only tells you who doesn't follow you back. Follower Analyzer also shows who you don't follow back and your mutuals, and you can sort, search, export to CSV, or copy the usernames.
- **See who unfollowed you.** Add an older export and it compares the two to show who unfollowed you and who's new since then.
- **Accounts for inactive profiles.** Instagram's export still lists accounts that were deactivated or deleted, which is why your numbers may not match the app. Follower Analyzer flags this and estimates how many of your "not following back" are actually inactive.
- **Free and unlimited.** No ads, no sign-up, check as often as you like.

To get your export: in Instagram, go to Accounts Center, then Your information and permissions, then Export your information. Choose only **Followers and following**, set the date range to **All time**, and download the ZIP when Instagram emails you. The [Follower Analyzer](https://followeranalyzer.io) page walks through each step.

The original Python approach is below if you want to see how it works under the hood.

### Findings
There are several methods for gathering your Instagram follower data. One approach is to use the Instagram API, which allows you to retrieve follow and following lists. However, Instagram’s API has become more restrictive, and official access requires approval for non-public data. Using bots or scrapers can trigger Instagram’s security measures which can potentially lead to Instagram blocking or restricting access to your account so caution is advised. 

Another option is to use web scrapers like Selenium to scrape the Instagram web interface for data. However, this approach may also trigger Instagram’s security measures.

The safest and most convenient method is to use the [instaloader](https://instaloader.github.io) Python library. Instaloader can fetch your followers and following lists without the need for Selenium or web scraping. Unlike Selenium, which requires logging into the site and simulating user actions, Instaloader utilizes Instagram’s public data, reducing the likelihood of triggering security features. Below are the steps on how to use Instaloader and the script you can run.

### Code

1. Install instaloader

```bash
pip install instaloader
```

2. Create Python Script

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

If you'd rather skip the script and keep your password to yourself, use [Follower Analyzer](https://followeranalyzer.io) instead.
