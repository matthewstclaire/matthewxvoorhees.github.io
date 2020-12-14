---
layout: post
title:      "The Pitfalls of CSS: A Caution Tale"
date:       2020-12-14 06:45:10 +0000
permalink:  the_pitfalls_of_css_a_caution_tale
---

Like many people I am a visual person. My understanding is that most people desire strong visualization of a topic to properly learn and store the information. For this reason, topics that require logic without physical representation tend to be harder topics to fully comprehend. When programming I have always desired a certain look for the programs I have built. Recently I learned a hard lesson of how much CSS can complicate a project and nearly steered an important project into an early grave.

Like many people first starting to learn what Software Engineering is, I began with HTML and CSS. HTML rarely produced anything of interest and was quick to pick up. Once I was able to add CSS into my small home-grown projects, I felt a real love for programming. Soon my focus mainly revolved around CSS almost completely negating any back-end languages. 

My time at Flatiron began and instantly CSS found its way to the backburner. Going from command line interfaces projects to simple Ruby apps, I grew an appreciation for the backend. Of course, my love for CSS still existed. When a project finally permitted, I found ways to add beautiful and robust CSS to my code which quickly made my project look as if I was an advanced programmer. The problem with this was that I did not understand it. With the code I brought from Bootswatch(premade code in the Bootstrap framework)came many ID's, class names, divs and more. Many could be interpreted quickly, while others were not. Let me show an example below of basic HTML that makes sense.

```    hogHTML(){
      let checked = this.greased == true ? "checked" : ""
      return `
        <a href="/hogs/${this.id}"><h2 class="header">${this.name}</h2></a>
        <img src="${this.image}" width="100" />
        <p>Specialty: ${this.specialty}</p>
        <p>Weight as a ratio of hog to LG - 24.7 Cu. Ft. French Door Refrigerator with Thru-the-Door Ice and Water: ${this.weight}</p>
        <p>Highest medal achieved: ${this.highest_medal_achieved} </p>
        <p>Greased: <input data-id="${this.id}" class="toggle" type="checkbox" value="greased" ${checked} ></p>
        <button class="delete">DELETE ME???</button>```
				
				
Above is code that was given as an example for my last project. Every bit of this code is methodical. From class names to HTML tags, there is purpose for every piece of this. I took heavy inspiration from this code, but layered on CSS that made it extremely difficult to understand. When asked questions about my code I was stuck sifting through useless tags trying to see what I needed. When asked why I used radio buttons I had no response. The real answer was "Because they look nice?"

The problem finally peaked when I wasn't able to correctly use a form. I have successfully built many forms at this point. How could a strong skill like form building now cripple me? I explored many avenues such as my back end, my fetch methods and more less conventional routes. Finally, thanks to a good friend of mine looking through my code for an exceptional amount of time, he was able to point me in the right direction. Thanks to my multitude of useless tags he pointed out that one single piece of information on my form wasn't matching my backend.

I built ugly forms with no effort to make it DRY. (Don't Repeat Yourself) It added a ton of time and took away from my understanding of how my code was working. All of this because I wanted my application to be pretty. I end this personal experience with a takeaway that I hope any new developer can take in a digest. 

> Write code that you understand. Don't focus on the visual until you understand what it is doing. It can all be added in later in abundance. Your simple website that isn't centered is beautiful as long as you understand what happens when your user starts to interact.

