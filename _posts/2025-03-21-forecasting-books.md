---
layout: post
title: Popular books on forecasting
---

Prediction and forecasting have always been interesting to me, first as personal intellectual curiosity, then as a professional concern for my job as a data analyst. Below are the notes I took as I read two books on forecasting written for a general audience: Nate Silver's _The Signal and The Noise_, and _Superforecasting_ by Philip Tetlock and Dan Gardner.

### The Signal and The Noise (2012)

Nate Silver is known among other things, for his work on the PECOTA sabermetric system, and later in forecasting elections through the now-defunct [FiveThirtyEight](https://en.wikipedia.org/wiki/FiveThirtyEight) project.

- The difficulty of assessing aggregate risk of bundled mortgage-backed financial assets precipitated the 2018 financial crises since these assets' market performance were often dependent on each other. Credit rating agencies used house prices going back 2 decades to assess their assets' risk. However, house prices 1980s - 2000s were always stable or increasing, precluding the possibility of small declines, let alone crashes. This is an example of an _out-of-sample_ problem.

- Political forecasters in the US are often fixated on broad stereotypes of what kinds of voters each of the two parties attract, rather than drawing on issue-specific polling to dissect smaller trends that sometimes run counter to party ideology. To me, Silver seems to endorse a Bayesian approach of continually collecting information about the data, and updating inferences accordingly. FiveThirtyEight operated via three principles: think probablistically, good predictions change and look for consensus.

- According to Silver, a good sabermetric system must (1) account for variables in player performance, (2) separate skill from luck and (3) account for the player's aging. For the first criterion, since MLB stadiums have non-uniform sizes, this is an obvious but often overlooked variable. The second criterion affects pitchers: their win-loss record is influenced by how their team's offense performs as much as their personal performance. Sabermetric data over time suggest that on average, baseball players peaks in their late twenties then decline, though Silver contends it is highly variable across players. This variability in the _age curve_ results in some teams recruiting players who are past their prime, yet are contractually obligated to keep them playing.

- Due to the number of variables and large spatial scale, minute changes in the initial state amplify to completely alter weather forecasts. This observation of the _butterfly effect_ was confirmed by [Edward Lorenz](https://en.wikipedia.org/wiki/Lorenz_system) in the late 1960s. The forecasts from the National Weather Service starts with computer predictions that are then fine-tuned manually by staff, like "seasoned pool players that work around the dead spots on their table". Data shows that these human predictors improve the accuracy of precipitation forecasts by 25% and of temperature forecasts by 10%, despite continual gains in computing power. Overall, NWS forecasts have improved steadily, errors in prediction of high temperature have dropped from 6 degrees Fahrenheit in the 1970s to <3 in the 2010s.

### Superforecasting: The Art and Science of Prediction (2016)

Philip Tetlock is a professor at the University of Pennsylvania who along with his wife and research partner Barbara Mellers was responsible for The Good Judgement project.

Compared to _The Signal and The Noise_, Superforecasting is written in a more academic style.  Interestingly, Nate Silver had met Tetlock and devoted a section in in _The Signal and The Noise_ to discuss Tetlock and Tetlock's ideas.

- Prior to World War II, many medical procedures were carried out despite dubious (or absence of) evidence for their effectiveness. Medical practice did not become evidence-based until randomized controlled trials were first seriously attempted in the late 1940s, advocated by [Archie Cochrane](https://en.wikipedia.org/wiki/Archie_Cochrane).

- News reports often state that stock markets rose or fell due to company announcements or press releases, but inspection of the timeline reveals that markets have closed by the time that announcement was made.
