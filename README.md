# Bug-in-yfinance
Explanation and code of the bug in python

I have a problem using yf.download in python as it downloads different range of records from 3 different computers and locations. I explain in more detail, suppose that today is September 23 and that in all cases and imported yfinance as yf (import yfinance as yf), I download the TSLA data for today:

**1. This is the result of a computer using spyder on windows 11 located in Spain:**
```
yf.download("TSLA","2022-09-23",progress=True)['Close'] [*****100%] 1 of 1 completed

Date

2022-09-22 288.589996

2022-09-23 274.799988
```
**2. This is the result using python in google colab:**
```
yf.download("TSLA","2022-09-23",progress=True)['Close'] [*****100%] 1 of 1 completed

Date

2022-09-23 274.519989
```
**3. This is the output from a computer using spyder in Canada with windows 10:**
```
yf.download("TSLA","2022-09-23",progress=True)['Close'] [*****100%] 1 of 1 completed

Series([],Name:Close,dtype:float64)
```
As you can see in (1) it returns the data for the 23rd and the previous day, which is the 22nd. In (2) it returns only the data for the 23rd and does not give me the data for the 22nd. In (3) it does not it returns no value, it does not give me the data of 22 or 23. As you can see, the same line produces 3 different results, the commands were made almost at the same time, only spaced by a few minutes (that's why the price varies slightly since it was done during market hours, in fact it was also done after the close and the pattern of results was the same). If I ask for the data from the 22nd, the pattern is repeated, for (1) it returns the data from the 21st, for (2) the data from the 22nd (including the 23rd) and for (3) only the data from the 22nd ( does not give me the data of 23).
