You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

Example 1:

> Input: prices = [7,1,5,3,6,4]
> Output: 5
> Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
> Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

Example 2:

> Input: prices = [7,6,4,3,1]
> Output: 0
> Explanation: In this case, no transactions are done and the max profit = 0.

```
function maxProfit(prices: number[]): number {
    if(!prices || prices.length < 2) return 0;
    let maxValue = prices[prices.length - 1];
    // [7,1,5,3,6,4] => [6,6,6,6,4,4]
    const maxValueAfterDay = [maxValue];
    for (let i = prices.length - 2; i >=0 ; i--){
        maxValue = Math.max(prices[i + 1], maxValue);
        maxValueAfterDay.unshift(maxValue);
    }
    let profit = 0;
    for(let i = 0; i < prices.length; i++){
        profit = Math.max(profit, maxValueAfterDay[i] - prices[i])
    }
    return profit;
};
```
