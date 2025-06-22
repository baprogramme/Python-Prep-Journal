# Insert Video Ads in Meta's Newsfeed

You're on Meta (Facebook's) Newsfeed Ads Team, working on an experiment to increase the number of video ads served up in a person's newsfeed.

The newsfeed ranking team gives you a list of `feed_items` which denotes what type of content their algorithm is planning to serve a user.

- `0` denotes a normal post  
- `1` denotes a video  
- `2` denotes a non-video ad  

You want to insert `n` more video ads; however:
- You **can't place a video ad next to an existing video** (to avoid the feed being too video-heavy).
- You **can't place a video ad next to a non-video ad** (to avoid overwhelming users with consecutive ads).

Write a function to determine whether it is **possible to insert `n` more video ads** into the feed based on `feed_items`.

---

## Example 1

**Input:**  
`feed_items = [1, 2, 0, 0, 0]`  
`n = 3`

**Output:**  
`True`

**Explanation:**  
- The first video ad can be inserted between the third and the fourth elements.  
- The second video ad can be inserted between the fourth and the fifth elements.  
- The third video ad can be inserted at the end.  

Thus, we can insert 3 out of 3 video ads, so we return `True`.

---

## Example 2

**Input:**  
`feed_items = [1, 0, 2, 0, 1, 1, 0]`  
`n = 2`

**Output:**  
`False`

**Explanation:**  
The only place where we can place a video ad is at the end of `feed_items`.  
So we can't insert all 2 video ads as requested, hence we return `False`.

---

## Constraints
- You may only insert a video ad in a position where:
  - Both neighbors (if any) are normal posts (`0`), or it's at the boundary with only one neighbor being `0`.
 

```python

def can_insert_video_ads(feed_items, n):
    if n == 0:
        return True  

    count = 0
    length = len(feed_items)

    for i in range(length + 1):  # check between elements
        left = feed_items[i - 1] if i > 0 else None
        right = feed_items[i] if i < length else None

        if (left not in [1, 2]) and (right not in [1, 2]):
            count += 1
            if count >= n:
                return True

    return False
