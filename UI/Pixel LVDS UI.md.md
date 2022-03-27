At some point we will have O(3000) pixel LVDS links that all need to be locked and run error free. For the cosmic run, it is O(300), still something of an UI challenge. The O(300) links can be shown on one page that fits on a decent screen with quite fine-grained information. For the final setup, we will need to summarize and then fold out details.

## Current implementation ##

The pixel LVDS status is written to the PCLS bank, which in turn is displayed on the Pixel LVDS custom page:

![LVDS_Status.png](https://bitbucket.org/repo/7zKBgbq/images/157943921-LVDS_Status.png)