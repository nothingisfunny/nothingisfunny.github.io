---
layout: post
title:      "sf_coffee Ruby Gem "
date:       2017-11-14 22:48:39 +0000
permalink:  sf_coffee_ruby_gem
---


This is a short blog post about my first Flatiron school project, for which I chose to build a CLI application for searching coffee shops locations in San Francisco. 
I chose three main coffee chains such as Pett's Coffee and Tea, Philz Coffee, and Starbucks. In order to collect information from the first two I used gem Nokogiri and simply scraped the necessary data from the websites. As for Starbucks, which website didn't allow scraping data, I spent quite some time searching for their well hidden API, which can be accessed here:
https://openapi.starbucks.com/location/v1/stores?apikey=7b35m595vccu6spuuzu2rjh4
Next I created a simple Command Line Interface that allows performing the search by ZIP code. The returned information includes name, address, and phone number for all of the stores in the requested area. In order to make data more readable in the console, I used gem 'colorize', that I highly recommend for applications of such sort.

To install and use the gem, please follow the links below:
https://github.com/nothingisfunny/sf-coffee-cli-gem
https://rubygems.org/gems/sf_coffee

