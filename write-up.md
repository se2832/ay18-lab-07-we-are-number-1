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
| BA-01 | constructor | 3 | symbol = null, StockQuoteGeneratorInterface = mock(StockQuoteGeneratorInterface.class), StockTickerAudioInterface = mock(StockTickerAudioInterface.class) | throws InvalidStockSymbolException |
| BA-02 | | | symbol = "F", StockQuoteGeneratorInterface = null, StockTickerAudioInterface = mock(StockTickerAudioInterface.class) | throws NullPointerException |
| BA-03 | | | symbol = "F", StockQuoteGeneratorInterface = mock(StockQuoteGeneratorInterface.class), StockTickerAudioInterface = mock(StockTickerAudioInterface.class) | a new StockQuoteAnalyzer is created |
| BA-04 | refresh | 2 | StockQuoteGeneratorInterface = an unavailable source, currentQuote = null, previousQuote = null | throws StockTickerConnectionError |
| BA-05 | | | StockQuoteGeneratorInterface = mock(StockQuoteGeneratorInterface.class), currentQuote = null, previousQuote = null | previousQuote is set to currentQuote and currentQuote is updated |
| BA-06 | playAppropriateAudio | 5 | audioPlayer = null, getPercentChangeSinceOpen = 0.0, getChangeSinceLastCheck = 0.0 | all code in method is skipped over |
| BA-07 | | | audioPlayer = invalid state, getPercentChangeSinceOpen = 0.0, getChangeSinceLastCheck = 0.0 | error tone is played |
| BA-08 | | | audioPlayer = mock(StockTickerAudioInterface.class), getPercentChangeSinceOpen = 2.0, getChangeSinceLastCheck = 2.0 | happy tone is played |
| BA-09 | | | audioPlayer = mock(StockTickerAudioInterface.class), getPercentChangeSinceOpen = -1.0, getChangeSinceLastCheck = -2.0 | sad tone is played |
| BA-10 | | | audioPlayer = mock(StockTickerAudioInterface.class), getPercentChangeSinceOpen = 0.0, getChangeSinceLastCheck = 0.0 | no tone is played |
| BA-11 | getSymbol | 1 | StockQuoteAnalyzer constructor is passed "F" for symbol parameter and StockQuoteAnalyzer is created successfully | "F" is returned |
| BA-12 | getPreviousOpen | 2 | currentQuote = null | throws InvalidAnalysisState |
| BA-13 | | | currentQuote != null | returns currentQuote.getOpen() |
| BA-14 | getCurrentPrice | 2 | currentQuote = null | throws InvalidAnalysisState |
| BA-15 | | | currentQuote != null | returns currentQuote.getLastTrade() |
| BA-16 | getChangeSinceOpen | 2 | currentQuote = null | throws InvalidAnalysisState |
| BA-17 | | | currentQuote != null | returns currentQuote.getChange() |
| BA-18 | getPercentChangeSinceOpen | 2 | currentQuote = null | throws InvalidAnalysisState |
| BA-19 | | | currentQuote != null | percentage change is returned |
| BA-20 | getChangeSinceLastCheck | 3 | currentQuote = null, previousQuote != null | throws InvalidAnalysisState |
| BA-21 | | | currentQuote != null, previousQuote = null | throws InvalidAnalysisState |
| BA-22 | | | currentQuote != null, previousQuote != null | returns currentQuote.getChange() |
| BA-23 | getCurrentQuote | 1 | StockQuoteAnalyzer is created successfully and refresh() is called | the currentQuote is returned |