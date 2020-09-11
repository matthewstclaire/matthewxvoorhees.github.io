---
layout: post
title:      "My First Ruby Project"
date:       2020-09-11 16:12:49 +0000
permalink:  my_first_ruby_project
---


**Let the record be known**

The particular details of the background of this project are worth noting. As we approached our first project I was nervous and excited. I could finally create my own project with original code. What sort of functionality could I provide? What roadblocks would I hit? Well certainly I hit roadblocks as well as hurricane speed winds. 

After looking through a few different API's I landed on the Ghibli Studios API. This would supply me with an exceptional amount of character data from films in the Ghibli universe. I set out to create a directory that would display this information at a user's request. This is about the time all of Salt Lake City lost power due to a massive storm we were wholly unprepared for. Fortunately, we only lost power for 2.5 days and I was able to make up lost time with some awesome support from my instructor. However, let it be known that this simple program exists despite the world's efforts to make it never see the light of day.

**Writing the program**

My goal when approaching this project was to focus on user experience and flow. My local UI team (my fiancé and 8 year old daughter) are harsh critics and always demand smooth flow of my programs. I kept them in mind when working through this project.

With a basic guide for how to proceed I set out making a simple version of my program would funcition. I knew I needed to extract information from the API, parse it, present it back in a way you'd want it to be displayed. At first this seemed relatively straightforward. Once I finally presented the information I realized that the information you'd actually want was buried in another URL. Currently I was only showing hair color, eye color, gender. Not the ideal data set. 

```
Name: Sen
Gender: Female
Films: URL:___________
```

Rather than present my user with a URL I needed the details that lived within that link. I went ahead and used some support from my instructor and was able to figure out a way to call the information through the method #character_films. This will act like my original scraping class, but one level deeper. It ended up being the same format I used originally to scrape from the API, with some tweaks. 

```
    def self.character_films(character)
        resp = RestClient.get(character.films[0])
        char_hash = JSON.parse(resp.body, symbolize_names:true)
        film = Films.new(char_hash[:title])
        film.director = char_hash[:director]
        film.description = char_hash[:description]
        CLI.display_films(film)
    end
```


This method works with my newly created #films class that will initialize the characters with a title. I then wrote attribute accessors for all of the details I wanted to pull in. The method interacts with the API by seeing the URL through my #character argument. Once it sees the link I am able to use a #.gets method to access information within the URL. At that point I am just working with a JSON file which I parse and present back to the user.

```
attr_accessor :title, :director, :description
```

Once I was able to get the information pulling in I was faced with a new issue which was how I display the new film data extracted from the second link with the data I already had. I had my original code block that looked like this:

```
def self.scrape_details(character)
    resp = RestClient.get(character.url)
    char_hash = JSON.parse(resp.body, symbolize_names:true)
    puts "Here is a little more about #{character.name}:".blue.on_white.bold
    character.gender = char_hash[:gender]
    character.age = char_hash[:age]
    character.hair_color = char_hash[:hair_color]
```
 
 By adding in a my new method of #character_films this information would now display with my original character details. Notice that this #scrape_details method is very similar to my #scrape_characters logic which is listed above. It was fascinating to see that despite this hiccup, the solution was already there, but needed to be reapplied. 
 
 `self.character_films(character)`
 
 At this point my code seemed to be functioning at the expectation I had. I discovered a gem through my classmates that allowed me to add color to what was being output to the user. This was exactly what I needed to woo my UI team. At this point I had a ton of fun messing with how the program flowed. I went a little nuts with coloring certain elements, but did manage to secure a good project review from my UI team.
 
 Overall I learned a ton in this project. It was a great experience and I loved the support I got from my classmates and instructor. Starting from scratch is a lot more fun in some ways when you get over the initimidating nature of it. 
