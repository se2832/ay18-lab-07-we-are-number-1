##Issue Tracking
| Issue Number | Code Line | Description | Resolution |
| --- | --- | --- | --- |
| 1 | 94 | If symbol is not a valid symbol an InvalidStockSymbolException should be thrown but it throws a StockTickerConnectionError | Resolved |
| 2 | 97 | If quoteStockSource is null it should throw a NullPointerException but it throws an InvalidStockSymbolException | Resolved |
| 3 | 91 | If statement checking for if the symbol is valid inverts the result so only invalid symbols are accepted | Resolved |
| 4 | 166 | If the currentQuote is null an exception should be thrown but the if statement lets nulls get by | Resolved |
| 5 | 116 | Variable currentQuote was always being set to previousQuote which was always null | Resolved |
| 6 | 242 | Incorrect value is returned for the change between the current and previous quotes | Resolved |
| 7 | 218 | Incorrect value is returned for the percent change since open | Resolved |
| 8 | 135 | If statement incorrectly evaluates the change percentages and/or change amounts | Resolved |
| 9 | 138 | If statement incorrectly evaluates the change percentages and/or change amounts | Resolved |

##Boundary Value Analysis
| Test Number | Method Name | MCC | Test Case Values | Expected Results |
| --- | --- | --- | --- | --- |
| BA-01 | constructor | 3 | | |
| BA-02 | | | | |
| BA-03 | | | | |
| BA-04 | refresh | 2 | | |
| BA-05 | | | | |
| BA-06 | playAppropriateAudio | 5 | | |
| BA-07 | | | | |
| BA-08 | | | | |
| BA-09 | | | | |
| BA-10 | | | | |
| BA-11 | getSymbol | 1 | | |
| BA-12 | getPreviousOpen | 2 | | |
| BA-13 | | | | |
| BA-14 | getCurrentPrice | 2 | | |
| BA-15 | | | | |
| BA-16 | getChangeSinceOpen | 2 | | |
| BA-17 | | | | |
| BA-18 | getPercentChangeSinceOpen | 2 | | |
| BA-19 | | | | |
| BA-20 | getChangeSinceLastCheck | 3 | | |
| BA-21 | | | | |
| BA-22 | | | | |
| BA-23 | getCurrentQuote | 1 |  | |