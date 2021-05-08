# surfs_up

## Overview 
W. Avy needed some more analysis to be done before he decided to invest in our Surf n' Shake Shop. He asked for the summary statistics on temperatures in June and December. By leveraging SQLAlchemy, we were able to provide the information he was looking for.

## Results
- The means are relatively close together
  -The mean temperature for June is less than four degree warmer than the mean temperature for December. With both the supposedly warmest and coldest months in the mid to low seventies, we can expect surfers to be in the water and even craving milkshakes year-round!

- December has a much larger range than June
  -Both month's max temperatures are in the mid-eighties. However, December's min gets down to 56. Knowing this, we should plan to include some wetsuits in our inventory!

- December has a higher standard deviation
  -Temperatures in December tend to fluctuate more than in June. We need to take that into account while budgeting for the year. Plan to bring in most of our revenue in the summer months, while it is consistently hotter, so that we have a buffer if we hit a cold streak in the winter.


## Summary
All in all, Hawaii seems to have the perfect climate for our Surf n' Shake Shop. The temperature stays fairly hot year round and after our analysis, we know to be aware of potential cold fronts in December and how to prepare for that with smart budgeting and supplying wetsuits for the surfers to stay warm.

Two additional queries I'd like to run would be the number of ideal surfing days there have been. I am defining "Ideal" as temperature of greater than or equal to 75 and less than half an inch of rain. This would look something like this query = session.query(Measurement.date, Measurement.tobs, Measurement.prcp).filter((Measurement.tobs >= 75) & (Measurement.prcp < .5)). I would then query the database with no filter and divide the "ideal days" by that number to get the percentage of ideal days where we can expect to bring in the most revenue. This comes out to be about 35%.

Second, I'd run a query to find the number of “unsurfable” days and find that percentage. I will define "unsurfable" as less than or equal to 65 degree and greater than three inches of rain. Running query = session.query(Measurement.date, Measurement.tobs, Measurement.prcp).filter((Measurement.tobs <= 65) & (Measurement.prcp > 3)) and turning it into a dataframe returns 6 records. .03% of unsurfable days! This will certainly encourage W.Avy to invest in our shop.
