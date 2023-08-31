# Discounted items old vs. new directive

Created: August 15, 2022 12:54 PM
Last edited: August 24, 2022 2:38 PM
Owner: mirka novakova, Peter Hupka
Status: Done
Engineer: Slava Gatin
Estimation: up to 2 hours

Hello Slava :) I have a question for you regarding the calculation of discounts. There is a new directive that changes the calculation and display of discounts in e-shops. We are currently working on how to apply it to Glami. And therefore I would need to find out the data for comparison before and after the change. So we need to compare:1. the number of products with the discount tag in the current variant, that is, the discount is applied to the price for the last 180 days

2. the number of products if we consider to count the discount from the price that is not more than 30 days oldOur main concern is that if we count this discount from the price for the last 30 days, we will quite possibly lose the discounted products and we want to know the difference.In the table, we basically need for both variants: % share of discounted products in the total catalog, average discount in the catalog, median discount in the catalog.The data would be from CZ and EE for the last 3 months.Would you be able to extract this data somehow? Ondra N. said that you have the ItemPriceHistory table available, so it should work. thanks a lot :)