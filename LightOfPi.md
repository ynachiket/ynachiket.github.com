By 2020 50 billion devices would be connected (http://share.cisco.com/internet-of-things.html). We already monitor the human body, plants, the water in the oceans along with the smartphones and computers and thus generate enormous amounts of data every second. Today we can monitor our heartbeat and our movements soon we will be able to accurately deduce when we are going to be sick. Today plants can tweet when they need water (http://www.botanicalls.com/kits/ http://www.koubachi.com/features/system?locale=en ) soon the data collected from thousands of plants could be used to manage an entire supply chain of a fertilizer industry. 

Mark Liberman calculated the storage requirements for all human speech ever spoken at 42 zettabytes if digitized as 16 kHz 16-bit audio. In 2013 we produced approximately 5 Zettabytes of data that number would be 44 Zettabytes by 2020.


This blog post is to help you be a part of this connected world and have some hands on experience of building something that helps you collect data by monitoring something that you care about.

Let’s say you are interested in monitoring the garbage levels in certain bins around the city over a period of time to identify trends in people’s spending habits and deduce stock trading patterns from that (http://www.citylab.com/design/2012/07/how-garbage-pickers-athens-predicted-greek-economic-crisis/2425/ ). Or maybe you care about minimizing food wastage by immediately getting notified when the freezer in the basement loses power. (http://developer.rackspace.com/blog/using-rackspace-cloud-monitoring-to-help-reduce-food-waste.html). The possibilities are limitless. 

We at Rackspace cloud monitoring process 1.5 million metrics every minute from monitoring the IT infrastructure of hundreds of thousands of customers. We monitor our infrastructure too and know first hand that it can be a bit overwhelming to manage all the notifications from a cloud monitoring system. When you monitor an IT infrastructure you are used to getting a lot of notifications in various forms such as mails, SMS, push notifications etc : http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-notification-types-crud.html . You can monitor things such as the cpu and memory utilization or even time it takes to reach your webserver from a particular part of the world. You can set thresholds for what value of these data points you want to get alerted on. 

Ok so that is some heavy tech stuff. Let’s try and make this a bit fun. In the world of virtual farms and candies it feels good when you build something that you can touch and feel. So we will build a notification system, which will actually be something physical as opposed to a mail or a SMS.  In one of their presentations at Geekdom, Amy Lee from Codame blew our minds away with her presentation on the use of digital LEDs for artwork.( http://ani-web.com/etc/codame/leds/amylee_leds_20140512d.pptx  ). At Yahoo! Sports, Viktor Abovyan has used the Andon lights to provide instant visual notification of the health of the CI build system. These people and their work in this area are a motivation for this project.

What you need:

1: Digital RGB LED Weatherproof Strip32 LED : http://www.adafruit.com/products/306 

2: A raspberry pi : http://www.adafruit.com/raspberrypi 

3: Adafruit Assembled Pi Cobbler Breakout + Cable for Raspberry Pi (Optional): http://www.adafruit.com/products/914

4: Female DC Power adapter - 2.1mm jack to screw terminal block: http://www.adafruit.com/products/368

5: Breadboarding wire bundle (Optional):  http://www.adafruit.com/products/153


Boot up your pi http://www.raspberrypi.org/help/quick-start-guide/ . I installed Raspbian OS. 

Connect the LED strip to the raspberry pi. Use https://learn.adafruit.com/light-painting-with-raspberry-pi/hardware as a reference.

You will need a library that makes it easy for you to communicate with the strip using the SPI. http://en.wikipedia.org/wiki/Synchronous_Serial_Interface 


Use the https://github.com/labatrockwell/raspberrypi-experiments/tree/master/Led_Strip_Library and try executing https://github.com/labatrockwell/raspberrypi-experiments/blob/master/Led_Strip_Library/examples/simple_example/simple_example.py to see if you are able to send bits to the LED strip.

Install flask on the pi: http://flask.pocoo.org/ . Once you have a webserver running on the pi, you can now write a controller to accept POST payloads and control the LED strip based on the content of the payload. You can checkout https://github.com/ynachiket/halo/blob/master/server.py as an example of how you can use the Python ledstrip library to light up different lights based on the content of the POST payloads.

Now you can easily integrate with Rackspace Cloud Monitoring system by using the webhook notification type: http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-notification-types-crud.html#service-notification-types-webhook. And there you go; you now have a visual aid to help you see what the state of your infrastructure is. The lights will light up 1.5 minutes on an average before you receive the mail in your mailbox. The strip has 32 lights and would provide a timeline of the state of your system. 





