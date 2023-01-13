# surfs_up
### Data Storage, Retrieval, and Analysis
analysis on the viability of a surfing/ ice cream shop.


## Resources
This analysis was performed with
* Jupyter Notebook 6.5.2
* SQLite
* Pandas
* numpy
* Flask

## Overview
### What and why

This analysis was prompted by a recent trip to Hawaii and a surfing lesson that ignited a passion. I became an obsessive seeking to get back
to that incredible place and somehow open a shop to outfit folks like myself, looking to experience the ocean in a way that you truly cant
explain in a way beyond **life changing**. I also thought what better way to reward yourself after a long day on the water than with a sweet
frozen treat, I am of course talking about ice cream! I reached out to noted investor and surfing fanatic **W. Avy** to see if he could provide
any insight or advice. As luck would have it, he was interested in pursuing a similar passion. So we agreed to sit down and hash out a business
plan for a Surf n' Scoop Shop on Oahu.

One of W. Avy's terms was that a weather analysis needed to be done to assess the viability of the ice cream sales because the surfing would
always be choice but the weather would affect the ice cream sales so much more. So, to do this I put recently acquired skills with **SQLite** to
good use. W. Avy wanted to see that there would be warm enough temperatures year-round to justify what would be a considerable expenditure,
especially when considering the cost of materials.

## Analysis
### The how

### June data
The first step was to activate **Jupyter Notebook** and open the starter code that W. Avy provided to me. In it I initialized the dependencies
that I would need **numpy, pandas, and SQLAlchemy**, I then created the engine through which all of the data would run, this engine ran off
of a **SQLite** database again provided by W. Avy. This database pulled from weather stations across Oahu several times a day giving us a
great idea what normal temps are like.

The first analysis was to query what the weather would be like in the month of June at the start of what is the start of the summer and thus
the beginning of the high season. To this a query was written to the engine (hereafter referred to as "session") for data from the month of
June. That query looks like this:

```
june_temps = session.query(Measurement.date, Measurement.tobs).\
    filter(extract('month', Measurement.date)==6)
```

This code first declares the variable name **june_temps** is a query of **session** for dates all dates in the database and their corresponding
temperatures. The next line then refines our search to specifically the 6th month. The next section of code turns this query into a list, then
after that the list is converted into a Dataframe. From the DataFrame (june_results_df) the descriptive stats are gathered from which you can
see that there are 1700 data points in the query making this data statistically significant and worthy of consideration. From this data we can
see that for the month of June the mean temperature is a balmy 74.94 degrees with a low of 64 and a high of 85.

### December data
The second request from W. Avy was for data from the month of December. This query was written in largely the same way with minor adjustments made.
The variable was named **dec_temps** and the month filter was set to 12. The process for turning this query in to a DataFrame was similar to what
was done for June with again slight differences, that code is shown below:

```
dec_results_df = pd.DataFrame(dec_temps, columns=['date', 'temperature'])
dec_results_df.head()
```

What this code shows is that the name for the DataFrame is **dec_results_df** and that the DataFrame will pull information from the query named
**dec_temps** with the columns labeled **date** and **temperature**. The second line then instructs the code to print off a small portion of the
DataFrame to make sure that the DataFrame was converted correctly. From there another request was made for the descriptive stats of the DataFrame.
What the descriptive states show us is that the mean temperature for the month of December is again in the 70's at 71.04 with a low of 56 and a
high of 83.

## Summary
### moving forward
It is in my opinion that we should move forward with our potential partner W. Avy to build this **Surf 'n Scoop Shop** on Oahu because there is
a clear pattern with the weather that temps will more likely than not be in the 70's and by having two different means of income we will provide
a different niche than any other surf or scoop shop in town. In fact, we could offer coupons for folks who either side of the business. I think
that great promotion would be to get 10% discount on a banana split for folks who either take a lesson or rent a board through the shop, to 
celebrate the end of the day.

I also think that there are more queries that could be performed on this data that could be used to drive sales, particularly for the **Scoop Shop**

The first of those would be to offer a "Happy Hour" like discount to encourage folks to come in and grab a sweet treat while the sun sets because
I for one can think of few things better than to have an ice cream while watching the sun set on a beach.

Another potentially useful query would be to track when the waves at closest beach tend to be at their peak and turn that in to an event opportunity.
A great way to drive business would be to sponsor a competition around when we can expect the waves to be the largest. With W. Avy's connections we
can leverage that in to World Surf League stop and having a competition on the surfing equivalent of Formula 1 would provide a huge boost.
