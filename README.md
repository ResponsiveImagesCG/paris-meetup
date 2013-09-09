# Responsive images meetup

##location and time
Date: Tuesday, 10th September, 2013. 
Time: 10am-6pm

Location:

```
16Bis Boulevard Montmartre
75009 Paris, France

(note: you want the 16 *Biz* entrance - not the 16... look for Mozilla on digital panel!)
```

<iframe width="425" height="350" frameborder="0" scrolling="no" marginheight="0" marginwidth="0" src="https://www.google.com/maps?sll=48.873288000000045,2.32527799999999&amp;sspn=0.010838193662898222,0.0219711170879061&amp;t=m&amp;q=16+Bis+Boulevard+Montmartre+75009+Paris,++France&amp;dg=opt&amp;ie=UTF8&amp;hq=&amp;hnear=16+Boulevard+Montmartre,+75009+Paris,+%C3%8Ele-de-France,+France&amp;z=14&amp;iwloc=A&amp;ll=48.871838,2.341121&amp;output=embed"></iframe><br /><small><a href="https://www.google.com/maps?sll=48.873288000000045,2.32527799999999&amp;sspn=0.010838193662898222,0.0219711170879061&amp;t=m&amp;q=16+Bis+Boulevard+Montmartre+75009+Paris,++France&amp;dg=opt&amp;ie=UTF8&amp;hq=&amp;hnear=16+Boulevard+Montmartre,+75009+Paris,+%C3%8Ele-de-France,+France&amp;z=14&amp;iwloc=A&amp;ll=48.871838,2.341121&amp;source=embed" style="color:#0000FF;text-align:left">View Map</a></small>

## About  
The purpose of the meetup is to discuss the proposed solutions (see below), 
assess the obstacles to their implementations, and build momentum behind the problem space. 
A little more detail:

For the last couple of years, various folks have been working towards finding a way to bring 
responsive images to the Web, with significant interest from Web developers. Although we now 
have 3 proposals on the table (
[srcset](http://www.w3.org/html/wg/drafts/srcset/w3c-srcset/),
[`picture` element](http://picture.responsiveimages.org )
and [client hints](https://github.com/igrigorik/http-client-hints)), we've had 
trouble getting sufficient momentum behind browser implementations that would let the market 
decide which solutions fulfills the [use cases](http://usecases.responsiveimages.org) 
most effectively.

In the mean time, developers are makig due with custom pollyfills that often prevent 
browsers from loading the image resources until after the DOM was (at least partially) loaded 
and Javascript has run. This directly hinders the performance work browser engineers have done 
over the years to optimize resource loading, and get requests on the wire as soon as possible ( 
according to their priority). That leaves developers with the dilemma: "Do we stall the image load?, 
or download unnecessary image data which will slow down the overall load time and inflate 
the user's bills?"

## Proposed agenda
1. Developer's perspectives
  * Overview of the problem - Mat Marquis (remote presentation) 
  * BBC's approach to responsive images - Mark McDonnell
  * Akamai's approach to responsive images - Guy Podjarny
2. Introduction to each of the proposed solutions:
  * The srcset attribute - Ted O'Connor
  * The picture element - Marcos Cáceres
  * Client Hints - Boris Smus or Ilya Grigorik
  * New image format? - Yoav Weiss 
3. Implementors feedback on the solutions
  * [DPR switching](http://usecases.responsiveimages.org/#resolution-switching) - relatively easy.
  * [Viewport switching](http://usecases.responsiveimages.org/#resolution-switching) - harder.
  * [Art direction](http://usecases.responsiveimages.org/#art-direction) - hardest.
4. Overlap among solutions
  * [lazylaod and postpone](https://dvcs.w3.org/hg/webperf/raw-file/tip/specs/ResourcePriorities/Overview.html). 
5. Next steps

Lunch @ ~12:30 - provided by Mozilla. Resume at 1:30pm. 

We will go out for dinner/drinks afterwards to
[Le Zinc des Cavistes](http://www.tripadvisor.com/Restaurant_Review-g187147-d1058405-Reviews-Le_Zinc_des_Cavistes-Paris_Ile_de_France.html).
If you want to joing us, [please let us know](http://doodle.com/2mep2k4u474cfhkw)!

## Proposed solutions
 * [The srcset attribute - An HTML extension for adaptive images](http://www.w3.org/html/wg/drafts/srcset/w3c-srcset/)
 * [The picture element](http://picture.responsiveimages.org)
 * [Client hints](https://github.com/igrigorik/http-client-hints)

## Who is attending?
Representatives for the following companies and organizations have registered: 

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
 
The event is on
[Lanyrd](http://lanyrd.com/2013/responsive-images-meet-up/) if you'd
like to make your attendance more public. 

Please note that you cannot register through the Lanyrd page.
If you'd like to register for either remote or in person
attendance, please contact the organizers listed below)

## Remote participation 
Note the meeting starts at 10AM Paris time. 
[See the meeting planner](http://www.timeanddate.com/worldclock/meetingtime.html?iso=20130910&p1=195&p2=179&p3=224)
for a time near you. 

** Please [sign up to participate remotely](https://github.com/ResponsiveImagesCG/paris-meetup/issues/5) - we will email you a link on the day **

To participate, you will need to install the [Vidyo client]( http://www.vidyo.com) 
to access the video stream (similar to what you have to do with G+ hangouts). 
The Vidyo client is available in the Apple App store, in the Google Play Store 
and also for Mac OX, Windows and Linux platforms.

* IRC - please join us IRC for backchat and minutes - irc://irc.w3.org:6665/#respimg

## Organizers contact info
* [Yoav Weiss](mailto:yoav@yoav.ws)
* [Marcos Caceres](mailto:marcos@marcosc.com)

# Getting to town 

### Bus from Charles de Gaulle

From Paris-Charles de Gaulle Airport (CDG) you can take the RoissyBus for 10
Euros to get downtown, about a ten minute walk from the office. It departs from
Terminals 1 and 2; buy your tickets just before the doors outside. The bus is
non-stop from CDG to downtown and stops near Palais Garnier. From there you can
walk to the office or many hotels nearby.

### Metro from Gare du Nord

If you come into Paris at the Gare du Nord you can take:

* Metro <b>line #4</b> (pink line) in the <b>direction of Porte d'Orleans</b>,
  change after two stops at <b>Strasbourg St Denis</b>.

* then Metro <b>line #8</b> (purple line) in the <b>direction of Balard</b> to
  <b>Grands Boulevards</b>.

The Grands Boulevard Metro is on the same road as the Office. You can buy a
Metro ticket from automated machines at all metro stops. You just need a regular
Billet. The price is 1.70Eur and is valid in all directions for one Journey.
This journey takes about 10 - 15 mins start to finish. You can pick
up a map of Paris on the Eurostar itself.

### Taxis G7 
Book by phone: 
 * +33 1 47 39 00 11 (to book in French) <br>
 * +33 1 47 39 82 28 (for an English speaking Agent)<br>

Book by internet:
https://www.taxisg7.com/abonne/commande-taxis<br>

### Wifi for guests

The Paris offices have a wifi network dedicated for guests. The SSID is "Mozilla
Guest" and we wil give you the password on arrival.


## Accomodation

### Hotels
[Hotel Tryp Francois](http://www.solmelia.com/hotels/france/paris/tryp-francois/home.htm). 
Across the street from the Mozilla office. If you ask for a quiet room, it is a
good hotel. Rooms clean. Internet included (from LAN cable, no WiFi).

[Holiday Inn - Paris Opera - Grands Blvds](http://www.holidayinn.com/hotels/us/en/paris/parpp/hoteldetail)

[Hotel Mercure Opera Cusset](http://www.accorhotels.com/gb/hotel-1614-mercure-paris-opera-cusset/index.shtml).
Internet is not included. About 5 mins walking to office via the main street.

[Hotel Bergere Opera](http://www.astotel.com/uk/hotel-bergere-opera-paris.php) 
nice hotel, small rooms but not bad.

[Hotel Acadia Opera](http://www.astotel.com/uk/hotel-acadia-opera-paris.php)

[Radisson Blu Ambassador](http://www.radissonblu.com/ambassadorhotel-paris)
5 minutes walk. Very nice.

[Hotel Corona Opera](http://www.paris-hotel-corona-opera.com/en/home/) 
Nice enough hotel; really close to the office. Staff are nice and helpful
and the rooms are nice, but the internet can be bad.

