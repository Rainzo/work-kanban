# Expected COS metric in WBR - Update definition

Created: April 28, 2023 3:05 PM
Last edited: June 8, 2023 3:21 PM
Owner: Tibor Kese
Status: Done
Engineer: Slava Gatin

**Current definition:**

- AutoCOS COS target (GMV weighted)

**New definition:**

- Use these rules / failover methodology:
    - 1) Use Expected COS field per provider (if we have it filled in)
        - Calculate it by taking an average of daily snapshot for the selected period
        - Values in table `DataProviderExpectedCOS` available in Keboola
    - 2) If we dont have it, use = [AutoCOS target] * [autoCOS correction coefficient]
    - 3) If not on AutoCOS, use Core Pricing default geo COS level
    - 4) If non-tracked shop, use nothing nothing
- The Expected COS on GEO level doesn’t need to be weighted from provider level Expected COSes, because you can calculate is as Expected COS = Expected Revenue / GMV (see in example below). No weighting needed.

**Example 1:**

- This is a sketch of the selection process on fictional example of 3 shops and 3 days. Each shop uses different rule:
- [https://docs.google.com/spreadsheets/d/1mN7yJCIl9u7tqa-azoqDIi5qcuY8WecdIR1AnEHNAQY/edit#gid=0](https://docs.google.com/spreadsheets/d/1mN7yJCIl9u7tqa-azoqDIi5qcuY8WecdIR1AnEHNAQY/edit#gid=0)

**Example 2:**

- This is how EXPECTED COS would look like with real numbers calculated for April 1.-17.4., Bartek calculated this from database
- [https://docs.google.com/spreadsheets/d/1SMvsKr0nOoLaBjxt_0ETsYDaHDDQN0Ex4egdaUykVpo/edit#gid=2068522257](https://docs.google.com/spreadsheets/d/1SMvsKr0nOoLaBjxt_0ETsYDaHDDQN0Ex4egdaUykVpo/edit#gid=2068522257)

**Tips on Aggregation from Bartek:**

![Untitled](Expected%20COS%20metric%20in%20WBR%20-%20Update%20definition%204b54a37e5b804ba596ab6b6b0574eed5/Untitled.png)