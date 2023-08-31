# Dynamic pricing formula: CPC simulation

Created: November 9, 2021 9:20 AM
Last edited: August 23, 2022 12:35 AM
Owner: Tibor Kese
Status: Abandoned
Software: Tableau, keboola
Engineer: Slava Gatin
Estimation: more than a week
Priority: low

Documentation for the original task:

[Simulace Dynamic pricingu: Frekvence a look-back window](https://www.notion.so/Simulace-Dynamic-pricingu-Frekvence-a-look-back-window-e53d6af4567240328729b30fab28c42e?pvs=21)

Gitlab:

[](https://gitlab.devklarka.cz/users/sign_in)

Details and how-tos:

[How To Build Dynamic Pricing Simulation Dashboard](https://www.notion.so/How-To-Build-Dynamic-Pricing-Simulation-Dashboard-d476ba756b034de580e96196ab9f07f7?pvs=21)

Add. comments:

![Untitled](Dynamic%20pricing%20formula%20CPC%20simulation%20e160746ba1254a4bb342f68cb1bdbab0/Untitled.png)

### Final graph:

- target COS
- old calculated COS based on dynamic_cpc_calculated (not the real one)
- simulated COS based on the full new formula, i.e. window frames, daily restrictions etc.

Scenarios to test:

- [x]  **New line to COS graph - “realCOS_old_cpc”** - corresponds to red CPC line
- [x]  **Cosmetic changes**
    - Change colour of tCOS from red to something else
    - Change names of lines to “cpc_old_default_actual” - red, “cpc_old_default_calculated”,  “cpc_old_default_normalized” , “cpc_new_default_simulated”
        - simCOS_old_calculated_cpc
        - simCOS_new_simulated_cpc
- [x]  1) Look-back window - nic-to-have as parametrs, default value 14
- note- change to yesterday, not today (done)
- [x]  2) Min/max daily change - nice.to-have as parametrs to change, default value 2%
- [x]  **3) With or without dividing by BM** - this could be two different lines
- Add option “without BM” to the BM filter
- [x]  4) Testing what desktop CPC - nice-to have different graph
- additional separate columns for desktop
- divide as filter
- add desktop GMV instead of mobile GMV
- [x]  **5) Paid exits only -** what if we filter out free exits
    - Technical fix
- [x]  **6) Non-AutoCOS exits only -** what if we filter out AutoCOS exits
- [x]  7) Non-tracked exits
- what if we include non-tracked exits
- [ ]  8) add adjustable boundaries to all variables of the formula
- [x]  9) **Improve filters for category and tag id**
- [x]  10) **Categories combined - try to make it work for all categories selected in a GEO**
- [x]  11) **COS table**
- [x]  12) **Make realCOS line responsive to device filter**
- [x]  13) **Make oldCOS_calculated line in accordance to mobile multipliers**
- calculate the all devices old_calculated_COS based on the weight of exits
- [x]  14) **BM filter - add option “without”, and rename "normalized" to "multiply (normalized)”**
- [x]  15) **Correct the date dependancy of the window functions (LOD?)**
- [x]  16) **Add filter "1/(Paid/All exits)"**, similar function as the BM filter:
- [x]  17) BUG: **Correct bug with purple line going to zero when autocos = no**

![Untitled](Dynamic%20pricing%20formula%20CPC%20simulation%20e160746ba1254a4bb342f68cb1bdbab0/Untitled%201.png)

18) BUG: Max change seems not to be working right - when I enter low number, for example 0.0001, the line doesnt change that much - but it should, because if such small change is possible, it should be almost flat, right?

19) Send Tibor the case where Paid exits ratio seemed to be low - so that we can investigate

20) **Categories combined - try weighting components by exits**

- current problem: blue and purple lines are not similar eve when they should be, also spike in November

old_actual CPC - tCOS in Vaseks graph

- BM = 1, multiply
- higher by human interventions

old_dynamic_cpc_calculated - blue

- BM = 1, multiply

New_simulated_divBM - purple

- BM = 0.8, divide by it