# COPYRIGHT NOTICE

This is the work of Bill Byrne, Karthik Krishnamoorthi, Saravanan Ganesh, Amit Dubey, Kyu-Young Kim and Andy Cedilnik from Google LLC, made available under the Creative Commons Attribution 4.0 License. A full copy of the license can be found at https://creativecommons.org/licenses/by/4.0/

# DESCRIPTION OF DATA

## NUMBERS
The Taskmaster-2 dataset consists of 17,289 dialogs in seven domains:
* restaurants (3276)
* food ordering (1050)
* movies (3047)
* hotels (2355)
* flights (2481)
* music (1602)
* sports (3478)

## COLLECTION METHODOLOGIES
Unlike [Taskmaster-1](../TM-1-2019), Taskmaster-2 consists entirely of two-person, spoken conversations. In addition, while Taskmaster-1 is almost exclusively task-based, Taskmaster-2 contains a good number of search- and recommendation-oriented dialogs, as seen for example in the restaurants, flights, hotels, and movies verticals. The music browsing and sports conversations are almost exclusively search- and recommendation-based. 
All dialogs in this release were created using a Wizard of Oz (WOz) methodology in which crowdsourced workers played the role of a 'user' and trained call center operators played the role of the 'assistant'. In this way, users were led to believe they were interacting with an automated system that “spoke” using text-to-speech (TTS) even though it was in fact a human behind the scenes. As a result, users could express themselves however they chose in the context of an automated interface. 

## INSTRUCTIONS
As with Taskmaster-1, crowdsourced workers and agents alike were given instructions prior to being connected in order to set up the role play scenario and to explain additional details. In most cases users and assistants alike were given free reign to make the conversation as realistic and typical as possible by basing their ideas and results on real flight data from the Internet instead of being restricted to a small knowledge base. However, in some cases certain variables such as location were restrcited to a handful of choices to make it easier for the worker playing 'assistant' to respond results in a rasonable time frame. In other words, knowing ahead of time which cities are in play for a given search makes it easier to anticipate and search for results. Note that, even though dialogs for each domain are consolidated in just one json file, there are actually many versions of each type of dialog which correspond to slight variations in the instructions. You can identify each set within a given domain by searching for "instruction_id". For example, in food ordering Below we give additional details about the instructions for each domain:
* **Restaurants**: Most dialogs in this set involve the user asking for recommendations for a particular type of cuisine in a given city. Users were asked to ask for  2-3 choices up front and then compare them by asking the assistant questions about price, atmosphere, menu items and the like.
* **Food ordering**: Users pretended they were ordering take-out using an automated assistant for a particular cuisine choice. (One cuisine was randomly generated for each set of instruction to ensure variety.) They discussed dishes or items, size, toppings, etc.
* **Hotels**: As with flights below, users choose from a list of cities to anchor their search. They are encouraged to compare several different hotels using typical preferences such as ratings, price, availability, and other amenities.
* **Flights**: Users typically choose from a list of cities or continents for round trip or multi-city flights and based their final choice on a number of additional preferences such as dates, flight time, price, layovers, seating class, airline, etc.
* **Movies**: This domain consists mostly of recommendation dialogs where users are trying to find a movie to watch in theaters or using a streaming service at home. 
  * In theaters: instruction_id = movie-{2-7, 9-12 14-15, 17, 20-22, 24e, 25-26, 30, 31e, 33e}
  * At home: instruction_id = movie-{8, 18, 19, 27-29}
* **Music**: For the music domain, users were asked to browse (i.e. listen to) several tracks based on their choice of artist, track, album, or genre, and then comment on each one. To recommend tracks, agents were able to send users Youtube videos which they in turn could control once launched. The dialogs do not include when the links, however.
* **Sports**: Sports dialogs are informational conversations discussing facts and stats about players, teams, games, etc. in the English Premiere League (EPL), Major Leage Baseball, Major League Soccer, National Basketball Association, and National Football League. Dialogs for each can be selected by the following prefixes: league epl, mlb, mls, nba, nfl.
  


