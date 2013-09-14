# Paris Responsive Images Meetup

## What the meeting was about
For the last couple of years, various folks have been working towards finding a way to bring 
responsive images to the Web. Although we 
have numerous proposals on the table, it has been difficult to get sufficient momentum behind browser implementations that would let the market 
decide which solutions address the [use cases](http://usecases.responsiveimages.org) 
most effectively.

In the mean time, developers are making due with custom pollyfills that often prevent 
browsers from loading the image resources until after the DOM has loaded 
and Javascript has run. This directly hinders the performance work browser engineers have done 
over the years to optimize resource loading (e.g., Webkit's Preload Scanner). 

Responsive Images can be broken down into three main use-cases:

 1. DPR Switching: Serving higher res images only to devices with higher device pixel ratio (aka Retina devices)
 2. Viewport Switching: Serving smaller images to smaller or lower-resolution screens
 3. Art Direction: Serving a different (often cropped) version of an image to a smaller screen, highlighting the important parts given the smaller space.


##Participants 


## Meeting agenda
1. Developer's perspectives
  * Overview of the problem - Mat Marquis (remote presentation) 
  * [BBC's approach to responsive images](https://speakerdeck.com/integralist/bbc-news-responsive-images) - Mark McDonnell
  * Akamai's approach to responsive images - Guy Podjarny
2. Introduction to each of the proposed solutions:
  * The srcset attribute - Ted O'Connor
  * [The picture element](https://dl.dropboxusercontent.com/u/38490906/respimg/index.html) - Marcos Cáceres
  * Client Hints - Ilya Grigorik
  * [New image format](http://yoavweiss.github.io/respimg-paris-presentation/) - Yoav Weiss 
  * [SVG switch renaissance](berjon.com/presentations/20130910-ricg-switch/) - Robin Berjon
3. Implementors feedback on the solutions for each of the use-cases
  * [DPR switching](http://usecases.responsiveimages.org/#resolution-switching)
  * [Viewport switching](http://usecases.responsiveimages.org/#resolution-switching)
  * [Art direction](http://usecases.responsiveimages.org/#art-direction)
4. Overlap among solutions
5. Related specs
  * [lazyload and postpone](https://dvcs.w3.org/hg/webperf/raw-file/tip/specs/ResourcePriorities/Overview.html). 
5. Next steps


## Session - Developer's perspectives

### Overview of the problem

Presented by: Mat Marquis, Filament Group, Chair of the Responsive Images Community Group 

The day started off with a pre-recorded presentation of the problem at hand from the RICG‘s Chair, Mat Marquis. Mat Described the history of responsive images from a developer's perspective, and gave an overview of how the RICG was formed - he also described how discussions between developers and the WHATWG led to srcset. During his presentation, Mat showed research that, on average, 60% of data of a Website is images - and that the trend is continuing to increase. This negatively impacts users - particularly those on lower-end mobile phones and those on limited/metered/capped data connection. Mat also showed research that claims 72% of websites send the same data to both desktop and mobile users.  

### [BBC's approach to responsive images](https://speakerdeck.com/integralist/bbc-news-responsive-images)

Presented by: Mark McDonnell, BBC

Mark McDonnel discussed the BBC's approach to responsive images. The BBC has 83 million monthly views (2.6 millions views per day), and, since 2011, they have benn been using a custom solution to handle responsive images. This solution is based on device capabilities, what Mark called a "cut the mustard" test: it checks for certain feature support to determine how capable the browser is. This allows the BBC to degrade gracefully on all devices.

### Akamai's approach to responsive images

Presented by: Guy Podjarny

Guy Podjarny explained Akamai’s sophisticated content delivery acceleration techniques including smart delivery (with Edge Device Characterization) using patterns of characteristics drawn from a database of mobile devices, front-end optimization, the still-in-beta image converter allowing art direction, and adaptive image compression taking into account the network conditions to define the quality of the served content.

Guy Podjarny wrote a [blog post](http://www.guypo.com/mobile/responsive-images-meetup-a-subjective-summary/) summarizing his thoughts about the workshop. 

## The proposal
Right now, no browser supports any of these proposals, but there has been some progress in their implementation. There are JavaScript polyfills for picture and srcset, and code patches for Chrome & Firefox were written or are underway. Client Hints is a bit behind, but also has a Chrome Extension to simulate it and a Chrome “intent to implement”.

However, srcset has been getting significant traction. Both WebKit & Firefox implementations of srcset for DPR only (no viewport) are “almost ready”. The Apple rep there couldn’t confirm (or deny), but I got a strong sense that this feature will show up in Safari soon enough.
We also briefly discussed the Resource Priorities proposal, discussed in the W3C Web Perf working group, which suggests new “postpone” and “lazyload” attributes on various elements. Resource Priorities includes a way to avoid downloading hidden images, making it very complementary to srcset (which offers no such method). Note that Resource Priorities is only in draft mode, and has no implementations I’m aware of.


### The srcset attribute

Presented by: Ted O'Connor, Apple
Ted, who is the Editor of the srcset spec at the W3C*, explained that Webkit is supporting a limited version of srcset (DPR selection via the Nx syntax). Webkit chose to implement DPR-selection first, as an incremental improvement to the platform and addresses the most pressing use cases.Marcos Caceres, Mozilla, indicated that there is interest to support the DPR-based selection via srcset in Gecko. 

Ted explained that art direction can be addressed on a platform level, not just responsive images. Ted also explained that most art direction use case can be addressed using using css (e.g., cropping the image). Shane Hudson, an invited expert, commented that user generated images could not use CSS. Reply was basically that the images would not be widely different.
A question was asked about the intrinsic size of images when no image dimensions are given, but the DPR is greater than 1. The answer is that webkit will scale the image appropriately.

* the srcset specification is derived form the WHATWG version of HTML. 

### The picture element 
Presented by: Marcos Caceres 
The picture element was received a negative reception by the implementers. It was seen as a “kitchen sink” proposal, which tries to address every possible use-case for this specific need.

### Client hints 


https://docs.google.com/a/marcosc.com/document/d/1gWy8ZpRcZjt6_00ISxTo3j2umrLEUQI_kutTCFEqOB4/