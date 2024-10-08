+++
title = 'Exercise 2.2.3'
date = 2024-10-08
draft = false
math = true
+++

If I leave my house at 6:52 am and run 1 mile at an easy pace (8:15 per mile), then 3 miles at tempo (7:12 per mile) and 1 mile at easy pace again, what time do I get home for breakfast?
```
minutes = 9*60 + 12
TotalTime = minutes + 2*(8 + 15/60) + 3*(7+ 12/60)
print(int(TotalTime/60))
print(TotalTime - (int(TotalTime/60)) *60)

```