At some point we will have O(3000) pixel LVDS links that all need to be locked and run error free. For the cosmic run, it is O(300), still something of an UI challenge. The O(300) links can be shown on one page that fits on a decent screen with quite fine-grained information. For the final setup, we will need to summarize and then fold out details.

## Current implementation ##

The pixel LVDS status is written to the PCLS bank, which in turn is displayed on the Pixel LVDS custom page:

![LVDS_Status.png](https://bitbucket.org/repo/7zKBgbq/images/157943921-LVDS_Status.png)

The features are on a snippet of two links, for ease of view:

![LVDS_Status_Snippet.png](https://bitbucket.org/repo/7zKBgbq/images/1651458846-LVDS_Status_Snippet.png)

* On the left is the 4-bin arrival time histogram. If the MuPix PLL is properly locked, hits will arrive only every 4th 125 MHz cycle and at a fixed phase, i.e. only one bin should be filled. The maximum bin is displayed in green, the others red. Note that bins with > 0 entries are scaled to be at least one pixel (i.e. visible).
* The histogram is followed by the link name (currently hardcoded in the JavaScript, could eventually be taken form the ODB if we give our pixels fancy names).
* Below the name are two "LED" indicators for locked (L) and ready (R)
* Rightmost are two counters. The upper one is the LVDS disparity counter (should be 0) and the lower one is the hit counter. The counters are implemented as difference counters, i.e. show the change with regards to the last webpage update. Note that JavaScript uses signed 32 bit ints per default, things might look weird if counters go above 2^31 - if that is a serious issue, we will look at it again.