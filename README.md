# BigFoot
An exploratory data analysis on the relationship between fractional moon light, and the frequency of Big Foot sightings

# FINDING BIGFOOT BY FOLLOWING THE MOON									
Analysis by Sareenah Laing		
									
									
I began this project with the germ of an idea.  A silly idea,  fun, easy whip this off in two days kind of thing. 

I promptly fell down a celestial rabbit hole, and have been here for rather more than two days. 	
								
I started with a day dream of chasing Sasquatches across the Pacific North-West via my tableau.  Following this day dream, I stumbled upon my BIG QUESTION							
Actually, two big questions.									
									
# The first big question was:
Could I predict the likeliest dates for Bigfeet sightings by charting the moon?	
								
I've been tooling with data scraped from NUFORC and generously offered up on Kaggle, I figured this would fit the vibe of my small but growing portfolio.   									
My twitter bio proclaims I'm a data analyst with a taste of the obscure (or was that absurd?) Either way, it fits.									
									
Pretty quickly, I mean really quickly without collecting or cleaning any data I learned that yes, of course I could predict which phase of the moon is best to catch a glimpse of the elusive beast.									
I mean, people have been studying Yeti for centuries and apparently I am not the first person to ponder this question.  In this century, we have things like radar and isotopes and DNA analysis.  Of course people have peeked to see if the moon has any behavioural affects on the mighty Big Foot.									

I could have asked any hunter or farmer to learn this; the moon effects animals. Prey and predator alike are affected, however the effects do not always present as one might expect.									
    Song birds who come out on a full moon night and begin filling the air with full throttled love songs.									
    Certain predators avoid full moon nights because of their inability to hide, while their otherwise vigilant prey end up in trap lines on full moon nights.						

There are plenty of sightings, over 4,947 reports across North America between 1921-2021.	
But to date: no remains, no habitats, no DNA have been confirmed as belonging to the notoriously shy bi-pedal hominid we call The Sasquatch.									
Other parts of the world have counterparts, such as the Yeti of the Himalayan Mountains and still, no physical evidence of their existence.									
									
With these questions in mind, I began cleaning my data. (see notes on ETL in addendum for more info on that process)									
I got through some minor hurdles, was feeling good.  Had some idea's in mind.  Went a little deeper. Thats when I recognized the BIG ISSUE									
Thinking about how to solve the BIG ISSUE, brought me to my real BIG QUESTION.  Thinking on my big question brought me to my HYPOTHESIS.									
									
* The BIG ISSUE :
HOW to match the Lunar Cycle to Diurnal information when there is no record of TIME in the dataset?                                        									
This is where my determined nature paid off. I could have seen the issue with the time stamps and ditched the whole thing in favour of an easier, cleaner data set. But, that just isn't how I roll.  I like roads less travelled and poking mysterious things just to see what that might do. As far as I could tell, this data set was the one for me.														
									
* The BIG QUESTION:		
							
Can the date of a past event be determined by the fractional representation of Moon Light recorded on the day of the event?									
The answer is Yes!									
									
First, I determined DAY OF MOON by the fractional percentage of moon light on the geocode table.	Because Timothy Renner's data set had the fractional representation of moon shine, I could determine the moon_day according to the amount of moon shine measured (I am literally dancing in my seat with this discovery)									
Fractional amount of moon light is a more precise way to pinpoint the phase of the moon than day information as the lunar cycle varies around 30 - 24 hour periods, give or take several hours.									

I found a table that broke down the days of the month by the fractional percentage of moon shine.

I plopped those values into a column in a new sheet and did a nested IF statement to display the correct moon phase per moon_day (day 1 through 30)									
It worked!
									
						
The lunar cycle is approximately 30 days give or take several hours. Day 1 of the lunar cycle is the first day after the new moon.  And that day can fall anywhere within the calendar month.  For this reason, I can't use day and moon_day interchangeably nor can I use these fields on a join.									
This will cause some issues with months that have thirty days that I will have to solve.																
# CHAPTER TWO

The big big question is a bit out of the scope for this project. Which brings me to the planning stage of CHAPTER TWO
******HOW To determine A DATE by Moon Light									
The new moon repeats every 29.53 days which is slightly out of sync with its rotational period around us on earth (27.32 days)									
But if you know a past New Moon Date you can determine a future Full Moon date by determining how much time will have elapsed  between the two events and dividing that number by 29.53, the lunar period.									
I will need to use a DATEDIFF function to find the elapsed time									
Number of New Moons = Days since New / 29.53									
									
# Back to the task at hand
###### The Hypothesis!									
My hypothesis:  the rate of probability for Big Foot sightings can be measured and predicted based on the fractional representation of moon light falling on the earth on any given day.									
									
					
The null hypothesis:  There is NO significant relationship :(								
Alternative hypothesis: There IS a significant relationship :)								
								
SIGNIFICANCE 								
To determine what, if any significance there is between the fractional representation of lunar light and the day of reported sightings, 		I calculated the mean, median, mode, standard deviation, variance, zscore and quartiles using google sheets	

Measures of Central Tendency								
fractional moon light	MEAN	0.3358059972						
fractional moon light	MEDIAN	0.3358059972						
fractional moon light	MODE	0.3358059972						
						
Measures of Dispersion								
fractional moon light	STD. DEV	0.2884055785						
fractional moon light	VARIANCE	0.08317777772	

QUARTILES								
fractional moon light	1st Quartile	0.0986315154		the least sightings				
fractional moon light	2nd Quartile	0.196357416						
fractional moon light	3rd quartile	0.2818494667						
fractional moon light	4th quartile	0.3358059972		The most sightings	

								
# Full Moon Light								
The highest recorded value in the data set, is 1. 								
On the 4,395th day of the data set, we find the single sighting to have occured during a full moon								
We know it was a full moon because the fractional moon light value was recorded as 1. 1 is the highest possible value which only happens under the conditions of a full moon.								
The sighting took place downriver of Telogia Creek in Wakulla County, Florida.								
It's interesting to note even though there was a full moon that winter night, there was 98% cloud cover.								
								
# This calls for a Z-test								
(the high value ) - (the mean) / std.deviation = zscore								
In this case as follows: 1.0-0.3358059972/.2884055785=zscore								
if the value of z is greater than 1.96 or less than -1.96, the null hypothesis is rejected. 								
The null hypothesis states that there is little to no significance between the two variables								
								
###### The Z-Test								
1.0-0.3358059972/.2884055785=zscore								
ZScore =	2.302985976							
###### Outcome is Very Significant, the alternative hypothesis is accepted!						
								
# Lets look at some visualizations							
								
![Mean of moon shine per moon phase](https://github.com/sarifeenah/BigFoot/blob/e3aa691784af800252a60b73c4df877edf09a4c0/1.%20Mean%20of%20Moon%20Shine%20per%20Moon%20Phase.png)
![Mean of moon shine per lunar day](https://github.com/sarifeenah/BigFoot/blob/e3aa691784af800252a60b73c4df877edf09a4c0/2.%20Mean%20of%20Moon%20SHine%20per%20Lunar%20Day.png)
![Mean of moon shine per sighting](https://github.com/sarifeenah/BigFoot/blob/e3aa691784af800252a60b73c4df877edf09a4c0/3.%20Average%20Moon%20Shine%20per%20Sighting%20.png)
									
								
1. We can see the fraction of moon light remains constant throughout the lunar phases.								
2. By confirming how perfectly the lunar days match to the phases of the moon, we can confirm the new moon falls around the 20th of each lunar month and the full moon on the 5th								
								
3. We can also see that the average fraction of moon shine per sighting remains between .44 and .54								
And can predict the most sightings will fall during the first quarter phase and the waning gibbous phase								
We can also predict the least sightings will take place outside of this range.								
								
Looking at our quartiles, we can determine that the least sightings occur during the periods with the least light, on the new moon								
Remembering what we learned about the highest moon shine value in the set, 1.0 indicating the full moon, we also know that only one sighting ever occurred on the full moon.  								
And that was during a winter night with 98% cloud cover. 								
This tells us the brightest and the darkest time of the lunar period are the least likely times to sneak a peek of our hairy friend.	

Please visit my tableau visualizations at the link below, or take a look at the image files, below.

([Find Bigfoot by Moonlight](https://public.tableau.com/views/BigFoot_16363096439910/Story1?:language=en-US&:display_count=n&:origin=viz_share_link))


![Tableau1](https://github.com/sarifeenah/BigFoot/blob/ed4f8bed4b5e6083e2c0220fa5468180d5313e52/EDA.png)

![Tableau2](https://github.com/sarifeenah/BigFoot/blob/e10ed1a8db9925befee4abcf6e796d0f2ebdd5fb/Story%202.png)								
			
					
								
								
								
								
								
