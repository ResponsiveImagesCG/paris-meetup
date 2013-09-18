# Paris Responsive Images Meetup

##Meeting report

On Tuesday, the 10th September, 2013 various W3C members and folks from the developer community got  together at Mozilla's Paris offices to try to agree on a way forward for responsive images. As no official minutes were taken during the meetup, this meeting summary is based on the following unofficial notes and blog posts from attendees: 

 * [Responsive Images Meeting Notes](http://www.shanehudson.net/2013/09/10/responsive-images-meeting-notes/), by Shane Hudson.

 * [Responsive Images Meetup – A Subjective Summary](http://www.guypo.com/mobile/responsive-images-meetup-a-subjective-summary/), by Guy Podjarny.

 * [Responsive images meetup - Paris Sept 12](https://docs.google.com/document/d/1gWy8ZpRcZjt6_00ISxTo3j2umrLEUQI_kutTCFEqOB4/edit?pli=1#), by Ilya Grigorik.

 * [Responsive Images Meetup: Coming together is a beginning](http://shoogledesigns.com/blog/blog/2013/09/13/responsive-images-meetup-coming-together-is-a-beginning/), by Flo Preynat.

Many thanks to the authors above for allowing their text to be reused here.

## Meeting outcomes

* Browser vendors agree that `srcset` + DPR-switching is the right initial step forward (i.e., the `2x`, `3x`, etc. syntax). 

* Agreement to then consider `srcset` + viewport size after some implementation experience (possibly drop height syntax from `srcset` spec). If not implemented, Width/Height syntax to possibly be marked at risk in `srcset` spec.  

* Browser makers acknowledge the art-direction use case, but still think `<picture>` is not the right solution.

* Adding new HTTP headers to the platform, as Client-Hints proposes to do, has had negative impact in the past - so Client Hints might need to be reworked at bit before it becomes more acceptable to browser verndors.

## What the meeting was about
Responsive Images can be broken down into three main use-cases:

 1. [DPR Switching](http://usecases.responsiveimages.org/#resolution-switching): Serving higher res images only to devices with higher device pixel ratio (aka Retina devices).
 2. [Viewport Switching](http://usecases.responsiveimages.org/#resolution-switching): Serving smaller images to smaller or lower-resolution screens.
 3. [Art Direction](http://usecases.responsiveimages.org/#art-direction): Serving a different (often cropped) version of an image to a smaller screen, highlighting the important parts given the smaller space.
 
For the last couple of years, various folks have been working towards finding a way to bring 
responsive images to the Web. Although we have numerous proposals on the table, it has been difficult to get sufficient momentum behind browser implementations that would let the market 
decide which solutions address the [use cases](http://usecases.responsiveimages.org) 
most effectively.

In the mean time, developers are making do with custom pollyfills that often prevent 
browsers from loading the image resources until after the DOM has loaded 
and Javascript has run. This directly hinders the performance work browser engineers have done 
over the years to optimize resource loading. It also negatively impacts users, as they are not able to benefit from these performance optimizations. 

## Companies that attended 

Present in Paris were the following companies/organizations:

 * Adobe
 * Akamai
 * Apple
 * BBC
 * Drupal
 * Ekino
 * Google
 * GPAC
 * Mozilla
 * W3C
 * Opera
 * PMLA
 * Shoogle designs
 * WOPE-framework
 * Braincracking

Although we had 40 registered remote participants, Mozilla's video infrastructure failed - so only a limited number of people were able to join remotely.  

## Meeting agenda and presentations

1. Developer's perspectives
  * [Overview of the problem](http://vimeo.com/74380964) - Mat Marquis 
  * [BBC's approach to responsive images](https://speakerdeck.com/integralist/bbc-news-responsive-images) - Mark McDonnell
  * Akamai's approach to responsive images - Guy Podjarny
2. Introduction to each of the proposed solutions:
  * The `srcset` attribute - Ted O'Connor
  * [The picture element](https://dl.dropboxusercontent.com/u/38490906/respimg/index.html) - Marcos Cáceres
  * Client Hints - Ilya Grigorik
  * [New image format](http://yoavweiss.github.io/respimg-paris-presentation/) - Yoav Weiss 
  * [SVG switch renaissance](http://berjon.com/presentations/20130910-ricg-switch/) - Robin Berjon
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

** Presented by: ** Mat Marquis, Filament Group, Chair of the Responsive Images Community Group. ([presentation](http://vimeo.com/74380964)). 

The day started off with a pre-recorded presentation of the problem at hand from the RICG‘s Chair, Mat Marquis. Mat described the history of responsive images from a developer's perspective, and gave an overview of how the RICG was formed - Mat also described how discussions between developers and the WHATWG led to `srcset` (proposed by Apple as a solution). During his presentation, Mat showed research that, on average, 60% of data of a Website is images - and that the trend is continuing to increase. This negatively impacts users - particularly those on lower-end mobile phones and those on limited/metered/capped data connection. Mat also showed research that claims 72% of websites send the same data to both desktop and mobile users.  

### BBC's approach to responsive images

**Presented by:** Mark McDonnell, BBC. ([slides](https://speakerdeck.com/integralist/bbc-news-responsive-images))

Mark McDonnell discussed the BBC's approach to responsive images. The BBC has 83 million monthly views (2.6 millions views per day), and, since 2011, they have been using a custom solution to handle responsive images. This solution is based on device capabilities, what Mark called a "cut the mustard" test: it checks for certain feature support to determine how capable the browser is. The BBC also relies on a RESTFul server side solution, called ImageChef. The BBC has been doing responsive images since 2011, but does not support serving images specifically for any pixel density. 

### Akamai's approach to responsive images
**Presented by:** Guy Podjarny, Akamai ([slides](https://github.com/ResponsiveImagesCG/paris-meetup/raw/master/slides/Akamai-Responsive-Images-Sep-2013.pdf))

Guy Podjarny explained Akamai's sophisticated content delivery acceleration techniques including smart delivery (with Edge Device Characterization) using patterns of characteristics drawn from a database of mobile devices, front-end optimization (using some JavaScript), an still-in-beta image converter that allows for a degree of art direction, and adaptive image compression taking into account the network conditions to define the quality of the served content. Guy's presentation served to demonstrate the kind of needs CDNs have for a standardized solution - specially at Web scale.  

Guy Podjarny wrote a [blog post](http://www.guypo.com/mobile/responsive-images-meetup-a-subjective-summary/) summarizing his thoughts about the meetup. 

## The proposed solutions 
As of when the meeting took place, the following specifications were being considered for standardization: 

 * [The `srcset` attribute - An HTML extension for adaptive images](http://www.w3.org/html/wg/drafts/srcset/w3c-srcset/)
 * [The picture element](http://picture.responsiveimages.org)
 * [Client hints](https://github.com/igrigorik/http-client-hints)

Although no browser supports any of the proposed solutions, there has been some progress in the implementation of `img srcset`. See: 

 * Webkit - ["Improved support for high-resolution displays with the `srcset` image attribute"](https://www.webkit.org/blog/2910/improved-support-for-high-resolution-displays-with-the-srcset-image-attribute/)
 * Chromium - [Intent to Implement and Ship: HTMLImageElement's `srcset` attribute (DPR switching)](https://groups.google.com/a/chromium.org/forum/#!msg/blink-dev/SVQxmsJRa9c/qfd55y_86HEJ) 
 * Mozilla - [Implement `srcset` attribute on `img`](https://bugzilla.mozilla.org/show_bug.cgi?id=870021)
 
Client Hints has an "[intent to implement](https://groups.google.com/a/chromium.org/forum/#!topic/blink-dev/c38s7y6dH-Q)" announcement as well as a patch for Blink, but discussions seem to be ongoing. There is at least a Chrome Extension that serves as a prototype.

### The `srcset` attribute
**Presented by:** Ted O'Connor, Apple

Ted, who is the Editor of the `srcset` spec at the W3C, explained that Webkit is supporting a limited version of `srcset` (DPR selection via the Nx syntax). Webkit chose to implement DPR-selection first, as an incremental improvement to the Web platform and addresses the most pressing use cases. Marcos Cáceres, Mozilla, indicated that there is interest to support the DPR-based selection via `srcset` in Gecko. 

Ted explained that art direction can be addressed on a platform level, not just responsive images. Ted also explained that most art direction use case can be addressed using CSS (e.g., cropping the image). Shane Hudson, PMLA, commented that user generated images could not use CSS. Reply was basically that the images would not be widely different. A question was asked about the intrinsic size of images when no image dimensions are given, but the DPR is greater than 1. The answer is that WebKit will scale the image appropriately.

### The picture element 
**Presented by:** Marcos Caceres, Mozilla. (no slides - "live coded" presentation). 

Marcos explained that the reason that `picture` exists is because `srcset` cannot address the art direction use case. Marcos gave a history of `picture` and explained that `picture` initially tried to address all the use cases (which is why it's a bit of a “kitchen sink”), and how it was now being stripped down to the bare essentials. Ideally, most developers would use `srcset` and only use `picture` just for art direction and for discriminating on supported formats (e.g., WebP).  This case is important as it allows browsers to do content negotiation on the client-side based on what image formats they support. The picture element is also being designed to be pollyfillable - so that it can be used in legacy browsers. 

During the presentation, a question was asked about the priority of the use cases being addressed. The answer was that the `picture` element was being simplified to only address art direction right now. Support from Canvas and an API might be added later. 
                
Another question raised was, what do large content providers think of the syntax of picture? Mark McDonnell, BBC, responded that anything marginally more complicated than `srcset` would result in convoluted markup that is hard to maintain (i.e., `picture`, as currently specified, is not very maintainable because of the reliance on in-line CSS media queries). 
   
Simon Pieters, from Opera, criticized the `picture` element for being too hard to implement and maintain. Simon, who quality assured HTML's video element, argued that the current markup pattern will lead to a lot of issues - as it did with the `video` element. Issues were also raised about how it would interact with a browser's prelaod-scanner. Yoav Weiss, who has investigated the area, argued that that should not be a big problem. But there are edge cases. Others also commented that the picture element makes interactivity, such as slideshows, slightly awkward. Involving loops etc.

### Client hints 
**Presented by:** Ilya Grigorik, Google ([slides](https://docs.google.com/presentation/d/1vyoo9KNuaVCFcVJzH-3fisjGmkTSj-8SH1VTCJUqvr4/edit?usp=sharing)).

Client hints defines a HTTP-based solution that would enable browsers to "hint" to servers information about the user's device - this could enable a simple way to do content negotiation based on, for instance, the DPR of a device. This solution serves as an alternative to `srcset` and solves the "ugly markup" problem by not requiring any changes to HTML's `img` tag.

As elegant as the solution sounds, there are a number of issues with the solution. For one, it would mean sending additional data with each HTTP request. It's also susceptible to breakage because of intermediaries such as proxies dropping or changing the content of headers, etc. There was push back against adding new HTTP headers - particularly from Mozilla. One explicit statement was that “while we (browser implementers) aren't saying we'll never add new headers, we're only one step away from that”. They pointed out that while some header-based content negotiation techniques worked in the past (e.g. Accept-Encoding), many failed (e.g. Accept-Language, Accept-Charset), leaving a sense that this is a wrong approach. That said, an opt-in mechanism for Client Hints moght mitigate much of the concern.

Ilya also wrote a [blog post about the meeting](
https://docs.google.com/document/d/1gWy8ZpRcZjt6_00ISxTo3j2umrLEUQI_kutTCFEqOB4/edit?pli=1). 

### New image format
**Presented by:** Yoav Weiss, Responsive Images Community Group ([slides](http://yoavweiss.github.io/respimg-paris-presentation/#/)).

Approaches the responsive images problem from a different angle - a file format solution.

The file's structure:
- A container with multiple layers and an offset table on top
- Layers are residual images, including repositioning, which allows addressing both resolution switching and art-direction using a single format
- Tested with WebP, should work with JPEG-XR
- Cannot work JPEG since the residual images are too big

This solution needs a fetching mechanism that relies on HTTP ranges. Intermediate caches must support ranges better than they do today, but there's no reason why they can't.
The browser starts off by fetching an initial range for the image URLs it encounters. Later on it fetches the rest of image gradually, as it knows more about the resource's byte ranges and (possibly) about the image's layout.

The fetching mechanism can be optimized with a manifest, declaring the resolution-offset table of the page's resources.

Advantages
- Markup left untouched
- Browser can easily fetch extra layers needed if/when orientation changes
-  Image editors could easily support creating these layers. CMSs can also  provide a nice UI that'd enable the uploader to control the layers.

Disadvantages
- Decoding performance was not yet tested. Decoding multiple layers (upscaling, etc) can mean that decoding time is an issue
- Fetching mechanism can create delay for HTTP/1.1, needs to be tested. With HTTP/2.0, this is not a concern.
- This is not a short-term solution. We need a solution in the mean time while this is being developed since it will take a long time to define and implement. Can co-exist with srcset, picture etc.

John Mellor's demo:
- Using progressive images enables the browser to fetch image data in parallel, showing low quality images all over the page first, instead of a single high quality image. Results in better overall user experience.
- That is only possible with SPDY/HTTP2, otherwise the delay impact would be significant.

### SVG switch renaissance
**Presented by:** Robin Berjon, W3C ([slides](http://berjon.com/presentations/20130910-ricg-switch/)). 

Robin Berjon, W3C, demonstrated how SVG `switch` element behaves very much like the proposed `picture` element. As such, it might be able to make some minor extensions to `switch` in order to get it to support media queries. Limitations are that it only works in an SVG context. Other noticeable criticism of this approach are the reliance on `xlink:href`, and not being able to discriminate by supported media type. Having said that, there is good compatibility except in IE8 and Android 2.2. This solution would also be used to "responsify" other elements, not just images.

David Baron, Mozilla, pointed out that although `switch` has support in browsers, to modify it in the way Robin proposes would not be trivial - hence it's probably not a good alternative.   

## Discussions 
For an excellent summary of the discussion that took place, we encourage you to read the blog posts from the participants. We could repeat a lot of it here, but they've summed it up much more elegantly than we could. Again, the links are:

* [Responsive Images Meeting Notes](http://www.shanehudson.net/2013/09/10/responsive-images-meeting-notes/), by Shane Hudson.
* [Responsive Images Meetup – A Subjective Summary](http://www.guypo.com/mobile/responsive-images-meetup-a-subjective-summary/) by Guy Podjarny.
* [Responsive images meetup - Paris / Sept 12](https://docs.google.com/document/d/1gWy8ZpRcZjt6_00ISxTo3j2umrLEUQI_kutTCFEqOB4/edit?pli=1#
) by Ilya Grigorik.
* [Responsive Images Meetup: Coming together is a beginning](http://shoogledesigns.com/blog/blog/2013/09/13/responsive-images-meetup-coming-together-is-a-beginning/) by Flo Preynat

## Acknowledgments
The organizers would like to thank Mozilla's Paris office for hosting the event - and the participants for making it out to the meeting. Also, big thanks to Dominique Hazael-Massieux for encouraging the RICG to organize this event. 