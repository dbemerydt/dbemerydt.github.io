---
layout: page
title: 
---

Suicide rates have [risen sharply since the turn of the decade](https://www.cdc.gov/vitalsigns/suicide/), and that increase is especially alarming for young people. It's now the second most common way for [people between the ages of 15 and 35 to die](https://www.cdc.gov/injury/wisqars/pdf/leading_causes_of_death_by_age_group_2015-a.pdf).

Fortunately, this trend does seem to be getting attention in popular culture, perhaps most notably in hip hop. One notable example was last year, when Logic released a track specifically aimed at suicide prevention, titled "1-800-273-8255", the phone number for the National Suicide Prevention Lifeline. In the months following [the lifeline's traffic rose enormously](https://www.teenvogue.com/story/logic-alessia-cara-song-drive-national-suicide-lifeline-calls). 

[![Logic - 1-800-273-8255 ft. Alessia Cara, Khalid](http://img.youtube.com/vi/Kb24RrHIbFk/0.jpg)](http://www.youtube.com/watch?v=Kb24RrHIbFk "Logic - 1-800-273-8255 ft. Alessia Cara, Khalid")

It makes sense that this was so powerful. Hip hop must have a lot of influence over the U.S. population, considering that it [just became the most listened-to genre in the country](https://www.forbes.com/sites/hughmcintyre/2017/07/17/hip-hoprb-has-now-become-the-dominant-genre-in-the-u-s-for-the-first-time/#437dba335383). Additionally, [many other prominent hip hop artists have recently taken to addressing mental health in their music](https://www.youtube.com/watch?v=3JTL5WgdDYk). 

I recently found myself captivated by this apparent uptick in mental health discussion in hip hop. It's well documented that [suicide spreads as a socially contagious phenomena](https://www.ncbi.nlm.nih.gov/books/NBK207262/), but what about rappers talking about suicide, and mental health in general?

To help answer this question, the website [Genius.com](www.genius.com) seemed particularly useful. Genius is not only a user-friendly database for song lyrics, but it also contains crowd-sourced annotations that explain the meaning behind the lyrics. This is useful from a computational perspective because it's very difficult for a computer to detect symbolism and other devices rappers use to encode meaning. Take this Lupe Fiasco lyric and accompanying annotation, for example. 

![photo](https://uvm.edu/~bfemery/mental_health_rappers/lupe_annote.png)

I probably couldn't find a way to get my laptop to detect that Lupe is convincing himself not to pull the trigger, but from the annotation, at least we can pull out the word "suicide".

So wrote a Python script that pulled every annotation on every song for all of the listed [hip hop musicians](https://en.wikipedia.org/wiki/List_of_hip_hop_musicians) and [hip hop groups](https://en.wikipedia.org/wiki/List_of_hip_hop_groups) on Wikipedia. Constructing this script was an extreme challenge and is worthy of its own blog post, but I probably won't write one for that. I do, however, plan on doing the good human thing and making a Git repo out of it. We'll see if that ever happens.

From there, I flagged every annotation that talked about suicide, depression, loneliness, anxiety, or just had the phrase "mental health". Being interested first in how rates of this discussion change over time, I counted up the number of these flagged annotations for each year, and then divided by the number of tracks for that year. This is what I came up with for the normalized rate of discussion (accompanied by the unnormalized rate and total number of tracks).

![photo](https://uvm.edu/~bfemery/mental_health_rappers/MH-timeseries.png)

![photo](https://uvm.edu/~bfemery/mental_health_rappers/MH-timeseries-unnormalized.png)

![photo](https://uvm.edu/~bfemery/mental_health_rappers/songs-timeseries.png)
