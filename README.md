# algoline-public
Try it on my [website](https://www.sharpecal.me/Algo_Line)!  
Partly based on the explanation of algolines described [here](https://www.reddit.com/r/RealDayTrading/comments/rf6crv/what_are_algo_lines/)

## How i calculate trendlines here
1. For each stock in my dataset, determine eligible starting points. Eligible starting points has:
   - High Volume (Volume above 50 day MA)
   - A wick (For a trendline connecting highs, the high should be reasonably far away from the body of the candle)
   - No earnings on that day
2. Get the gradient and intercept from each starting point to every high value after that point (For trendline connecting highs)
   - For a 10-year dataset, one can see how this will take a long time to compute
   - Hence i make use of numpy vectorised calculations whenever i can
3. Check that between each start and end point, the trendline has not been breached (High price < trendline value for each day)
4. For the trendlines that satisfy step 3, further extend the trendline to the latest date of my dataset. Check where the trendline gets breached, if at all (close price > trendline value).
5. Calculate the number of touches this trendline has.
   - Define a touch as high price being sufficiently close to the trendline (Does not need to be exactly touching)
7. Get useful information of these trednlines, such as start date, breach date, gradient, intercept, trendline length, number of touches

## What does this code do?
1. [data_collection.ipynb](https://github.com/elliotchung/algoline-public/blob/main/data_collection.ipynb) pulls the required data from wrds and transform the data suitable for calculating trendlines.
2. [app.ipynb](https://github.com/elliotchung/algoline-public/blob/main/app.ipynb) outlines the code which calculates the trendlines

### Graphical representation of code:
[streamlit-app-2024-04-17-22-04-72.webm](https://github.com/elliotchung/algoline-public/assets/101564632/834412fa-bb6e-4e1b-9a65-3ea48f203b35)
