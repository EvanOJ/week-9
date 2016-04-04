# Final Project Proposal

Your assignment this week is to write a detailed proposal for your final
project. In proposing your final, try to address each of the following
areas.


## Problem / Question

Applications are ultimately just tools. What problem or question does
your application attempt to resolve or grapple with? How does your
application speak to this problem/question?

Question 1.
  "What is my theoretical level of comfort at my location based on real time weather data?"

  Maybe not a widespread question, but I have often found myself wondering "Why do I feel so cold, the weather
  app on my phone says its 65° outside?!" So I open up the psychrometric chart app on my phone, punch in the temperature
  relative humidity and make some determinations on the psyiological degree of comfort being experienced at that precise moment.
  I though it might be interesting to use the html5 geolocation feature, or the ability to punch in any location, get the real time
  weather for that location and feed it into the psychrometric chart calculations. Both the chart calculations and weather data are
  available on github including the necessary js/html/css files. It would be just a matter of linking them and plotting it on a map
  website. One might even be able to use weather station locations as a way to 'score' different areas in the region at a given time
  for comfort for a certain activity (comfort depends on your clothing level and activity level).

Question 2.
working on idea2*

## The data

Geospatial applications are all about working with data. What datasets
would you plan/like to use? If the data you'll be working with isn't
already stored in a way that you can use, how will you be storing your data?

Question 1.

I found this jquery plugin that gets basic weather data for a given location in 'realtime' (short delay involved). I've experimented
with methods like this in rhino/grasshopper before but using xml feeds from NOAA, which might be an option as well as this plugin was
having difficulty when changing locations. At any rate, it supports HTML5 geolocation which could be used, otherwise a geocoded user input
could perhaps be used instead.

https://github.com/EvanOJ/jquery.simpleWeather
http://w1.weather.gov/xml/current_obs/seek.php?state=hi&Find=Find

Regarding the psychrometric calculations, I have found two sources. One is the CBE Thermal Comfort Tool, which is a standalone
website for plotting comfort based on user inputs. The idea would be perhaps to have some version of this in a sidebar or bottomrocker
type bar, below a map of your current location.

http://comfort.cbe.berkeley.edu/

The other is a d3 application that incorporates the calculations listed above and has the js/html/css requied. I repeatedly received
an error when tryin to run this application,

*"d3.js:2 XMLHttpRequest cannot load file:///C:/Users/EvanJ/Box%20Sync/backup/CPLN690/psych-chart-d3/data/rh-curves.json. Cross origin requests are only supported for protocol schemes: http, data, chrome, chrome-extension, https, chrome-extension-resource."*

which I think is a result of faulty pathwork to the chart.json referenced file (tried downloading it as well as doing an ajax call to my
  github raw link).

https://github.com/EvanOJ/psych-chart-d3



## Technologies used

Which technologies covered in class (or discovered on your own!) do you
plan to use? How do you anticipate using each of these technologies?  

Review the APIs/online examples of leaflet, turf, jQuery, underscore (or
any library not explicitly covered in class) for functions/uses which
you'd like to explore. Briefly describe how you might use them.

see above^^
    - psychrometric chart
    - realtime weather data

## Design spec

#### User experience

At a high level, how do you expect people to use your application?
- Who are the users?
- What do they gain from your application' use?
- Are there any website/application examples in the wild to which you can compare your final?

Question 1.

Users would be people, like myself, design professionals with an interest in environmental design and understanding the actual
forces involved--not just how temperature, RH, and wind speed interact on a chart but how do YOU perceive it. That is the only
surefire way to understand psychrometrics, undoubtedly one of the hardest concepts in environmental design and engineering in general.

Regarding interfacing, the user would input his/her clothing level (a simple scale 0-1, 0 being little to no insulation value, 1 being
  a 3-piece suit), and activity level/metabolic rate (0-1, 0 being doing nothing, 1 being running, etc.). The app would then reference the nearest weather station data available for a given location and fill in the other requirements (wind speed, relative humidity, drybulb temperature).

The output is a physiological perception rating: cold, cool, slightly cool, neutral, slightly warm, warm, hot. This could then possibly be transferred to nearby regions, giving a score to each (perhaps coloring the marker) based on these values. Such a feature could anwer questions like "Which city or location would feel more comfortable to sit and read, or run and play, or lay in a field and sleep, etc."


#### Layouts and visual design

So far, we've built all our applications with a side bar for
representing non-map content and navigation. This is not the only
successful design. Extra content could be displayed in a top bar,
through modals, through side bars on both sides, and any combination of
these as well as a number not mentioned. Try to describe your
application's visual layout. Conceptually (no need for extensive CSS
here), what will this design require?

A few ideas that have been in the back of my head, these first are a long shot but I like the idea/visualization. I have no idea how this is done, but since they look quite similar I imagine they are referencing the same data/visualization method?
https://www.windyty.com/?2016-03-29-00,39.960,-75.197,6
http://earth.nullschool.net/#current/wind/surface/level/orthographic=-77.21,35.82,446
http://hint.fm/wind/

On a more practical level, I imagine an achievable product similar to a hexgrid overlay of the greater region with a scoring system based on the desired activity. Perhaps something similar to this, but on a larger scale:
http://epro.maps.arcgis.com/apps/StorytellingSwipe/index.html?appid=73c96c2d13bf457faf4d604a2ea82d11

It would be awesome to tap into that wind visualization method, which does some work interpolating between known data sources. I am not sure what format that data is in, but perhaps it would be possible to take this generalized data approximation and perform a spatial query to grab that data and use it to plug into the app, producing a resultant score.
One of the main determining factors in perceiving comfort is wind speed, especially given high levels of relative humidity. So, with just this piece of information it could be extrapolated to do large scale/city-wide heat-map-style mapping for determining levels of comfort given a relatively fixed temperature/RH from the airport/weather station but varying primarily by wind.


       MOBILE                         WEBSITE
--------------------                  ---------------------------------------------------------------------
:                  :                  :                                                   :      USER     :
:                  :                  :                             ................      :     INPUTS    :
:       MAP        :                  :                             .     Psych    .      :               :
:                  :                  :                      @ .... .     chart    .      :  ...........  :
:                  :                  :                   location  .     popup    .      :  ...........  :
--------------------                  :                             ................      :  ...........  :
:                  :                  :                                                   :  ...........  :
:                  :                  :                                                   :  ...........  :
:    PSYCH CHART   :                  :                                                   :               :
:                  :                  :                                                   :               :
:                  :                  :                     MAP                           :               :
:                  :                  :                                                   :               :
--------------------                  ---------------------------------------------------------------------
//with a button, similar to wk9
lab that opens sidebar with user
input options

## Anticipated difficulties

Thinking about weaknesses can be useful. What do you anticipate being
most difficult about this project? How will you attempt to cope with
these difficulties? For example, asynchronous behavior (ajax, events)
are hard to use and think about. Global variables are a strategy for
coping with that difficulty by breaking data out of the asynchronous
context.

Question 1.

Difficulty 1.
The resolution would be limited to available weather data, which is typically at the city scale, or at best the city-airport scale. However, given that the user can override the data (let's say you had a thermometer in your window, etc.) it might circumvent this problem.


Question 2.
working on second idea*

## Missing pieces

We've only managed to scratch the surface of the available technologies
by which you could construct an application. What use-cases haven't we covered
that you think would be useful? What technologies not covered seem exciting to
you (you don't necessarily have to fully understand what they're for,
this is a chance for you to get our help interpreting a technology's
purpose/usage).
