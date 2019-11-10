# METHODOLOGY: Introducing the unicorn index: defining player uniqueness

[Link to blog post.](https://dribbleanalytics.blog/2019/11/unicorn-index)

## Data collection

All data was collected from [Basketball-Reference](http://basketball-reference.com/) and [NBA.com/Stats](https://stats.nba.com/). I collected 70 different statistics from these two sources.

The table below contains stats from Basketball-Reference which can be found in the 2018-19 player advanced and per game stats.

|Basic shooting stats|Basic counting stats|Holistic advanced stats|Specific advanced stats|
:--|:--|:--|:--|
|FG|ORB|PER|TS%|
|FGA|DRB|OWS|3PAr|
|FG%|TRB|DWS|FTr|
|3P|AST|WS|ORB%|
|3PA|STL|WS/48|DRB%|
|3P%|BLK|OBPM|TRB%|
|2P|TOV|DBPM|AST%|
|2PA|PF|BPM|STL%|
|2p%|PTS|VORP|BLK%|
|eFG%|MP||TOV%|
|FT|||USG%|
|FTA||||
|FT%||||

The table below contains stats from NBA.com/Stats.

|General touch stats|Specific touch stats|Specific shooting stats|Defense stats|
:--|:--|:--|:--|
|TOUCHES|ELBOW_TOUCHES|DRIVE_PTS|DFGM|
|FRONT_CT_TOUCHES|POST_UPS|DRIVE_FG%|DFGA|
|TIME_OF_POSS|PAINT_TOUCHES|C&S_PTS|DFG%|
|AVG_SEC_PER_TOUCH|PTS_PER_ELBOW_TOUCH|C&S_FG%| |
|AVG_DRIB_PER_TOUCH|PTS_PER_POST_TOUCH|PULL_UP_PTS| |
|PTS_PER_TOUCH|PTS_PER_PAINT_TOUCH|PULL_UP_FG%| |
|||PAINT_TOUCH_PTS| |
|||PAINT_TOUCH_FG%| |
|||POST_TOUCH_PTS| |
|||POST_TOUCH_FG%| |
|||ELBOW_TOUCH_PTS| |
|||ELBOW_TOUCH_FG%| |

In the table above, the general and specific touch stats are under “player tracking touches”. The specific shooting stats are under “player tracking shooting efficiency”. The defense stats are under “player tracking defense.”

## Unicorn index creation

We classified all players into one of 3 positions: guards, wings, or bigs. Then, we did PCA on the 70 stats above to have the components explain at least 90% of the data's variance.

From the PCA, we computed each player's distance from the average stats for that position using the following metrics:

1. Euclidean distance
2. Manhattan distance
3. Chebyshev distance

After exploring the trends in the distances, we normalized them between 0 and 1. This lets us place them on the same scale so we can average them. The unicorn index is the average of the 3 normalized distances for each player.

As such, unicorn index is between 0 and 1, where 1 is the most unique player possible (highest distance in every metric) in a position.