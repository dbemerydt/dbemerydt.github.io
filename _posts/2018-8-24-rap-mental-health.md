---
layout: page
title: A data-driven preliminary look at mental health in hip hop
---

## Some motivation

Suicide rates have [risen sharply since the turn of the decade](https://www.cdc.gov/vitalsigns/suicide/), and that increase is especially alarming for young people. It's now the second most common way for [people between the ages of 15 and 35 to die](https://www.cdc.gov/injury/wisqars/pdf/leading_causes_of_death_by_age_group_2015-a.pdf).

Fortunately, this trend does seem to be getting attention in popular culture, perhaps most notably in hip hop. One notable example was last year, when Logic released a track specifically aimed at suicide prevention, titled "1-800-273-8255", the phone number for the National Suicide Prevention Lifeline. In the months following [the lifeline's traffic rose enormously](https://www.teenvogue.com/story/logic-alessia-cara-song-drive-national-suicide-lifeline-calls). 

[![Logic - 1-800-273-8255 ft. Alessia Cara, Khalid](http://img.youtube.com/vi/Kb24RrHIbFk/0.jpg)](http://www.youtube.com/watch?v=Kb24RrHIbFk "Logic - 1-800-273-8255 ft. Alessia Cara, Khalid")

It makes sense that this was so powerful. Hip hop must have a lot of influence over the U.S. population, considering that it [just became the most listened-to genre in the country](https://www.forbes.com/sites/hughmcintyre/2017/07/17/hip-hoprb-has-now-become-the-dominant-genre-in-the-u-s-for-the-first-time/#437dba335383). Additionally, [many other prominent hip hop artists have recently taken to addressing mental health in their music](https://www.youtube.com/watch?v=3JTL5WgdDYk). 

I recently found myself captivated by this apparent uptick in mental health discussion in hip hop. It's well documented that [suicide spreads as a socially contagious phenomena](https://www.ncbi.nlm.nih.gov/books/NBK207262/), but what about rappers talking about suicide, and mental health in general?

## Don't sweat the technique

To help answer this question, the website [Genius.com](www.genius.com) seemed particularly useful. Genius is not only a user-friendly database for song lyrics, but it also contains crowd-sourced annotations that explain the meaning behind the lyrics. This is useful from a computational perspective because it's very difficult for a computer to detect symbolism and other devices rappers use to encode meaning. Take the highlighted Lupe Fiasco lyric and accompanying annotation, for example. 

![photo](https://uvm.edu/~bfemery/mental_health_rappers/lupe_annote.png)

I probably couldn't find a way to get my laptop to detect that Lupe is convincing himself not to pull the trigger, but from the annotation, at least we can pull out the word "suicide".

So wrote a Python script that pulled every annotation on every song for all of the listed [hip hop musicians](https://en.wikipedia.org/wiki/List_of_hip_hop_musicians) and [hip hop groups](https://en.wikipedia.org/wiki/List_of_hip_hop_groups) on Wikipedia. Constructing this script was an extreme challenge and is worthy of its own blog post, but I probably won't write one for that. I do, however, plan on doing the good human thing and making a Git repo out of it. We'll see if that ever happens.

## We're not just making this up

From there, I flagged every annotation that talked about suicide, depression, loneliness, anxiety, or just had the phrase "mental health". Being interested first in how rates of this discussion change over time, I counted up the number of these flagged annotations for each year, and then divided by the number of tracks for that year. This is what I came up with for the normalized rate of discussion (accompanied by the unnormalized rate and total number of tracks).

![photo](https://uvm.edu/~bfemery/mental_health_rappers/MH-timeseries.png)

![photo](https://uvm.edu/~bfemery/mental_health_rappers/MH-timeseries-unnormalized.png)

![photo](https://uvm.edu/~bfemery/mental_health_rappers/songs-timeseries.png)

Neat! Unlike a D&D game, this phenomenon is taking place in more than just our collective imaginations. But who is doing the most talking about mental health, and what shape does the distribution have? To answer this I counted up the flagged annotations for each artist, ranked them in descending order of how many such annotations they had, and plotted the number of annotations against their rank on a [glog-scale](https://twitter.com/dbemerydt/status/939998137757954049) to deal with the heavy tail.

![photo](https://uvm.edu/~bfemery/mental_health_rappers/MH-zipf-icons.png)

Now if you don't want to go get your magnifying glass out of your fanny pack, which is probably all the way across the room, I can just tell you who's in those icon-sized photos. Our leaders are Kid Cudi, Eminem, Death Grips, Kendrick, XXXtentacion, Aesop Rock, Kanye, Mac Miller, Tyler, and Tech N9ne. 

## Enter Mr. Solo Dolo

I also did plenty of staring at this distribution for individual years, and started wondering about how the diversity of artists talking about mental health (i.e. how much the distribution is dominated by a few artists versus how evenly spread out the distribution is) has changed over time, and how that corresponds to the volume of the discussion. And how might a computational social scientist measure the diversity of a relative frequency distribution. I could think of one way: [Shannon's entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory)). This of course only made sense for the years when the number of flagged annotations is reasonably high, so I chose to compute it for just the current millenium. The entropy (AKA diversity) is shown below, plotted alongside the normalized rate of discussion.

![photo](https://uvm.edu/~bfemery/mental_health_rappers/rate+entropy-timeseries.png)

My attention upon seeing this was drawn to the right-hand side of the figure, where entropy drops in 2008 and remains low from there on. The individual responsible for that initial drop is none other than Mr. Rager himself. 2008, 2009, and 2010 are all dominated by songs that were released either on Kid Cudi's debut mixtape, "A Kid Named Cudi" or on his first studio album, "Man on the Moon: End of Day". In the years that follow, various other artists take the lead, although he does take it back yet again when he drops his 2016 album, "Passion, Pain, and Demon Slayin'". I can't help but think that Cudi was a critical player in opening the floodgates to this now ubiquitous element of hip hop, which is somewhat satisfying knowing that his mission has always been to ["help kids not feel alone and stop kids from committing suicide"](https://hiphopdx.com/news/id.27910/title.kid-cudi-says-he-wants-to-help-kids-not-feel-alone-and-stop-kids-from-committing-suicide#). To me this looks like Mr. Solo Dolo enters the party, the hip hop community embraces the martian, and the rest is history.

If you've gotten this far, I applaud and thank you for bearing with my rambling and geeking out over all this stuff. That's what I have so far, but there's a ton more to explore here. I'll be back soon with topic modeling, more information theory, and almost definitely wordshifts, so stay tuned. Or don't. I don't know what you want. ¯\_(ツ)_/¯ 

### PEACE


