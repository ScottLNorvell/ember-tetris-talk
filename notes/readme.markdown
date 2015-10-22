# Ember Tetris Talk

- Title Slide
- About Me
    + contact
    + CNÉ
- Work on TheScene
    + video site
    + built on ember 2.1.0
- As of Yesterday
    + 201-created/isaac shoutout
- Team issued a tetris challenge
    + build tetris in the language of your choice
    + sounds like fun
    + Hmmm wonder if i could do it in ember?
- Tetris === Reuseable components
    + each piece is a component
    + built of little square components
    + the next piece is a commonent etc
- Approach
    + pure ember (no 3rd party libs)
    + no reading other people's implementations
    + SVG
- SVG 
    + decided svg would probably be more straight-forward than dom elements
    + inspired by conversation with:
- This guy 
    + Matt Beale
    + consultant in ember
    + hire him!
- Ember used to be full of these
    + metamorph monster
- Whoops these:
    + metamorph tags
- Wait these are less scary
    + pre-htmlbars SVG impossible
    + still needed some work that Matt helped with
    + When I told him I was using them he was like:
- Matt smiling pic
    + nice, someone's using them
    + then false humility: I hope it works!
- Research
    + just play alot of tetris?
    + I actually did that and then
- Tetris Wiki
    + learn some fun facts
- Fun Facts
    + called tetrominos
    + each piece is named after the letter it represents (pic)
- Installation
    + after all my hard work I decided to refactor it into an addon
    + who wouldn't want to drop a tetris game into their app?
    + use cases
        * error pages (send a socket when api is back up?)
        * loading route (clear 4 lines and go to next page)
- DEMO
    + feel free to shout out suggestions
    + problem with building tetris => as you get further along, smoke testing takes longer and longer because this game is addicting!
    + Still in beta even though I don't know how to put something into beta
    + I owe you docs
    + want to make styles extendable
    + animations! (Edward Faulkner???)
- DEEP DIVE (back to slides)
    + going to do a deep dive
    + hopefully I don't include any
- Weird Tricks You Can Stop Using in Ember 2.0
    + let's get started
    + first thing
- Hard Code a bunch of info about your tetrominos
    + best way
    + explain properties
- Bind to transform properties
    + setup controls to affect x/y coords and rotation
    + bind to them
    + point to code (mention scale)
    + this gets you tetrominos that will freely move anywhere
    + SVG doesn't care if something is 5000 pixels off the board
- What about Collision detection?
- Fake slide about get bound properties with jQuery
    + almost gave up cause I was like "Ok this just got too hard"
- Just Kidding 
    + remembered Erik Bryn's PooPoo about selector-based programming
    + back to demo
    + each square is "1"
    + don't care about edges
    + can represent that on a much simpler grid
    + if this square occupies "9", then it will collide right
- willCollide (back to slides)
    + explain code
    + check if any squares occupy your outer bounds
- What about other collisions? (back to demo)
    + did we collide with pieces at the bottom
    + how do we get these squares "played" and regenerate another piece
- Custom Data Structure
    + use ES6 Set (curious, show of hands how many have found a use case for any of these cool new data structures?)
    + push in as a string representation (for uniqeness sake)
    + wanted to use a map
    + "squares" is an array of objects {x, y, type}
    + basically the "model" for each component
    + now we pass that model into here and get some cool stuff happening
    + we need to look at it 3 ways and it turns out that's really efficient in Ember...
- so willCollide becomes
    + move point and check for inclusion in squareSet
    + splain it
- there's also cannotRotate
    + go back to example
    + positions vs locations (raw positions vs locations on the board)
- _applyTransformation? what's that????
    + trickiest math in project
- call mom
    + turns out rotation around origin involves swapping x and y values and making them negative
    + you have subtract origin and then add it back
    + great mom! that seems to work so I hid string representations here
- Implement _applyTransformation
    + recognize these variables from the previous slide?
    + let's just eval the proper string
    + move it
    + return new array (so we can use sugar on it!)
- Done with Deep Dive
    + questions?
- Up Next
    + Ember Ms PacMan
- The End
    + We're hiring!
