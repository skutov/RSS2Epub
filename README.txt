RSS2Epub
=============

Contact
----------------------
You can contact the authour of this program by email on RSS2Epub@rg-gosset.co.uk If you wish to get involved then please make contact with what areas you're skilled in and what you'd ilke to do to help. The full source code will be avaliable at https://github.com/skutov/RSS2Epub as and when it becomes real.

Purpose
----------------------
This is an app that will allow users to be emailed an epub file of their RSS feeds on a regular basis. This will include the ability to seperate them into different categories, specify length of time between emailings. Have them emailed to a distributor, eg to amazon accounts to be placed onto kindle readers. The program is still in initial conception stages so things like programming language and such are undecided yet, however there is a base idea of the layout of the program.

Basic Concept
----------------------
The program will have 3 parts.
1 - A web based front end that takes care of people configuring their choices, notifications, email frequency, feeds, etc. Will probably be PHP based.
2 - A backend that gathers RSS content, parses it into a database, then out into epubs to be emailed to each user. Probaly will use C++, may change depending on avaliability of skill.
3 - A MySQL database to store account information, feed content and to allow the frontend and backend to talk to each other.

A potential element to the backend is at https://code.google.com/p/feed-reader-lib/ which is a RSS parser that places code into XSL files that could be used to do a large portion of the processing. This would take a lot of effort out of parsing feeds into the database.

Definitions
----------------------
feed - an single RSS/Atom/other feed of content from a website that may be added by multiple users
page - one piece of content from a feed, may include text, HTML etc.
epub - a file for an ereader that contians information stored as text and/or images
series - a definition of one series of epub files to be sent out including frequency, which feeds to include, where to send etc.
issue - on epub file that gets sent out to a user, includes a number of pages from the feeds specified in the series for the issue

Database Structure
----------------------
This is provisional and will probably change as development occurs.
Format:
table name
	-field name - format
	

accounts
	-account uid - int PK
	-email - string
	-auth info - various
	-name - string
	
categorys
	-category id - int PK
	-category name - string
	-account uid - int
	
feeds
	-feed id - int PK
	-feed url - string
	-name - string
	-ttl - int

pages
	-page id - int PK
	-feed id - int
	-date/time published - date/time
	-content - HTML or links to XSL files
	
series's
	-series id - int PK
	-account id - int
	-frequency - int or time
	-address - string (email address to send to, eg amazon distribution email address etc)

issues
	-issue id - int PK
	-series id - int
	-date - date/time
	
account-feeds
	-account uid -int PK
	-feed id - int PK
	-category id - int
	
series-feeds
	-series id - int PK
	-feed id - int PK
	
issue-pages
	-issue id - int PK
	-page id - int PK
	
account-pages
	-account id - int PK
	-page id - int PK
	-read - bool
	-vetod - bool
	
Changelog
----------------------
0.0 - Added readme and began design process

Roadmap - Functionality
----------------------
1.0 - Base functionality - Backend

	1.1 - To be able to read and parse RSS feeds.
	1.2 - To be able to create epub files from feed content.
	1.3 - To be able to send epubs by email.
	1.4 - To have this process happen automatically on a regular basis.
	1.5 - To have the resultant content from parsing be saved into the database.
	1.6 - To keep track of which pages have been read or sent out.
	
2.0 - Base functionality - Frontend

	2.1 - To use google accounts/some other api for authentication. (more secure than developing own password system, also, who needs more accounts?)
	2.2 - To allow users to select frequency of mailings, eg, daily, weekly, on specific days, when there's n unread articles, etc.
	2.3 - To show un-sent articles for users to read/veto
	2.4 - To give the option for users to have an epub sent out sooner that scheduled.
	2.5 - To show the contents of 
	
3.0 - Multi-user optimisation - Database and Backend

	3.1 - To keep database of articles and keep record of which ones have been sent to each user.
	3.2 - To keep database of feeds and which articles are from each feed, to be updated frequently that users picks are chosen from.

To-Do
----------------------
1. Database
	- Finish design
	- Create dev database
	- Populate database with users and feeds

2. Backend
	- Create base application for backend
	- Get backend connecting to database
	- Get backend parsing feeds into a database
	- Automate parsing to happen based off ttl for feed
	- Get backend creating epub files from pages in database (issues)
	- Get backend selecting pages based off user selections
	- Get backend emailing epubs to users
	- Automate publishing issues based off user preference (time delay)
	- Add option for users to have epubs sent when x unread pages in feeds.
	
Terms and Conditions
====================

This program is open source however, anyone who wishes to take full credit for the development of the program will be removed from the project. Anyone who tries to delete whole sections with being given consent, will be removed from the project.

Before you make a commit, please contact the program admin/author (skutov) and alert him of any chamges or additions so that at later dates, the program admin/author can work on the program themselves without having a clue as to whatchanges have been made, where to start, and what goals have been completed.

Thank you for reading, and happy coding.

Licensing
====================

This work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-nc-sa/4.0/deed.en_US.
If you wish to license this work for commercial purposes then please contact RSS2Epub@rg-gosset.co.uk and mention licensing in your subject line and include the purpose of the license, how you wish to use it and how many users you expect to recieve.

The software is provided "as is", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the software or the use or other dealings in the software.