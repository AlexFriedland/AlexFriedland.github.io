---
layout: post
title:  "CLI Data Gem Project"
date:   2017-08-01 14:28:27 +0000
---


	The goal of this project is to build a scraper based around a Command Line Interface (CLI) that the user can interact with to get and explore different data that the program pulls from a webpage (hence being called a scraper). For this assignment, we needed to be able to have our program ‘drill down’ to a second level of data.  Additionally, the scraper should utilize object oriented programming (OOP).
	
	I had a lot of fun with this project.  Initially, I chose to build a program that would pull the roster for the NY Mets (baseball team), because my dad raised us as Mets fans, and my brother worked for them not too long ago.  Once I had built most of the app, I realized that I should have just made it for all MLB teams, so I finished it for the mets and then went back and did it again for all teams (which again, I really enjoyed, as I had to refactor, or rework / improve my old code to be more meta and be flexible enough to work with multiple team links).  
	
	The first step in writing this program was scaffolding both the CLI and the scraper, and envisioning the way they’d work together.  Since this lesson focuses on OOP, I figured it should work something like this:

1.  Present CLI interface to the user (main menu), and get the input.

2.  Initially the presented options were going to be a list of positions to search by (or all players).  Once the user chooses that, the program scrapes the relevant data from the webpage and uses it to instantiate player objects. 

3.  The players are presented to the user in list form and the user then either selects a player to view more info on, or can go back to the first menu, or can quit.  If the user decides to drill down again to get more info on a player, the scraper engages again, this time by being passed the player’s URL, which then collects and presents more player info.

	The process here changed slightly once I decided to turn the Mets Scraper into the MLB Scraper.  I had to remove the hard-coded Mets URL and allow the scraper, and CLI, to present the user with a list of team options, and once selected, pass that team’s URL to the scraper as a variable when it’s instantiated to do it’s job.  This was actually my favorite part of the process; I enjoy making my code more versatile and flexible.
