---
title: "Automated immigration solution"
layout: post
date: 2018-03-01 14:40
image: /assets/images/thumbnails/aeroplane.png
headerImage: true 
wide: true
tag:
- Angular
- C#
- Biometrics
- Complex
- Futuristic
category: project
subCategory: web
---

<style>
.centered{
    display:block;
    margin: 0 auto;
}
.app-pic{
    display:inline-flex;
    max-height:220px;
}
.demo-pic {
    display:block;
    margin: 0 auto;
   max-width: 250px;
}
</style>

## When
Nov 2017 - Mar 2018 

## What
 - __Redesigning the immigration control for air/sea ports__ by developing a prototype application to demonstrate a __seamless passenger flow__ on their way into the country - through either sea or air ports. This solution satisfies the comprehensive requirements specifications of a robust large scale system whilst also being an innovative, futuristic thinking product.  
 - Here we make use of __biometric facial recognition__ to remove a number of the physical barriers involved in the previous process by detecting and tracking travellers and providing direction based on their known data.  
 - Multilingual solution encompasses applications for the traveller, officers on duty in the aiport and managers of the system.

## Why
The current immigration process is not terrible, but certainly not seamless and definitely not future proof. With this prototyped solution we can:  

 - improve the travellers experience, create efficiencies and maintain security  
 - give the traveller a seamless, intuitive experience 
 - __streamline airport operations, lower staffing requirement and increase automation__
 - __utilise the individuals anchored biometric identity__ to allow for fast traveller analysis and the __early detection of Persons of Interest (POI) or high risk travellers__
 - reduce the current time consuming process and improve inneficiencies by capturing and maintaining traveller IPC data electronically
 - __remove bottlenecks__ by reducing reliance on manual checks at the Exit Marshall Points (EMP)


## My role
 - Development across full solution
    - __Specific focus on the capturing, handling and presentation of video and event stream data__
 - Leading others on best Angular practices
 - Contributing to solution architecture decisions
    - SCRUM, backlog selection, analysing considerations


## Development

### Team setup and methodology
 - Large corporation, lots of existing systems, methods and some red tape
 - 12-14 member large team of mostly intelligent, switched on individuals all __excited__ about the project
     - 6 devs, Testers, PM, BA etc
     - Remote locations with a central base (in which I reside)
 - __Strict agile__ methodology, two week sprints and daily stand ups
 - Satisfying list of specific functional requirements
     - Development according to __comprehensively designed moqups__
     - Goals in mind regarding performance, usability etc

### Concept and flow of solution
<a href="/assets/images/immigration/flow1.png" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/flow1.png" class="html5lightbox" style="width:49%;display:inline-block;" data-group="flow-diagrams" title="Traveller flow 1">
	<img src="/assets/images/immigration/flow1.png"/>
</a>
<a href="/assets/images/immigration/flow2.png" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/flow2.png" class="html5lightbox" style="width:49%;display:inline-block;" data-group="flow-diagrams" title="Traveller flow 2">
	<img src="/assets/images/immigration/flow2.png"/>
</a>

See the traveller flow diagrams above. Here we have created 3 apps:

 - Declaration submission app __(Point 1)__
    - Travellers can submit their declaration online via mobile app or using a kiosk counterpart
    - Data is logged and stored to pair with passport and watchlist details

<div style="text-align:center">
<a href="/assets/images/immigration/app/ap-2.png" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/app/ap-2.png" data-group="app" class="html5lightbox" title="Create a safety pin">
</a>
<a href="/assets/images/immigration/app/ap-3.png" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/app/ap-3.png" data-group="app" class="html5lightbox" title="Create profile via scanning of ticket">
	<img src="/assets/images/immigration/app/ap-3.png" class="app-pic"/>
</a>
<a href="/assets/images/immigration/app/ap-4.png" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/app/ap-4.png" data-group="app" class="html5lightbox" title="Create a profile">
</a>
<a href="/assets/images/immigration/app/ap-5.png" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/app/ap-5.png" data-group="app" class="html5lightbox" title="Homescreen after profile creation">
</a>
<a href="/assets/images/immigration/app/ap-6.png" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/app/ap-6.png" data-group="app" class="html5lightbox" title="Create your declaration">
	<img src="/assets/images/immigration/app/ap-6.png" class="app-pic"/>
</a>
<a href="/assets/images/immigration/app/ap-7.png" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/app/ap-7.png" data-group="app" class="html5lightbox"  title="Submit declaration - either online or via barcode">
	<img src="/assets/images/immigration/app/ap-7.png" class="app-pic"/>
</a>
<a href="/assets/images/immigration/app/ap-8.png" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/app/ap-8.png" data-group="app" class="html5lightbox" title="Submit via barcode">
</a>
</div>


 - Traveller view app __(Point 5)__ 
    - Travellers look into the live video screen and are assigned to either red or green channel, based on their IPC, Passport details amongst other criteria

<a href="/assets/images/immigration/travellerView.png" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/travellerView.png" class="html5lightbox centered"  title="Traveller channel color overlines their head and directs them">
	<img src="/assets/images/immigration/travellerView.png" class="demo-pic"/>
</a>

 - __Authorised Officer (AO) app (Point 5)__ 
    - __AO can view live video feeds of travellers with live channel information assigned to them__
    - AO __recieve notifications about travellers__, Persons of Interest, Travellers in wrong lane
    - AO can manually change persons channel and add events to their details
    - AO can __view details of passenger__, their group, and a list of all events that passenger has taken part in
    - AO can identify passengers with covered faces not in the system and direct them
    - AO can view traveller analytics

__*Note - these images are mockups where the final version contained video feeds and faces as opposed to blue boxes*__

<a href="/assets/images/immigration/nfv-live.png" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/nfv-live.png" class="html5lightbox" style="width:49%;display:inline-block;" data-group="nfv-pics" title="AOs can see live feeds of travellers, channel colors and notifications">
	<img src="/assets/images/immigration/nfv-live.png"/>
</a>
<a href="/assets/images/immigration/nfv-notifications.png" data-fullscreenmode="true" data-group="nfv-pics" data-thumbnail="/assets/images/immigration/nfv-notifications.png" class="html5lightbox" title="Recieve notifications for warnings, persons of interest etc">
</a> 
<a href="/assets/images/immigration/nfv-changechannel.png" data-fullscreenmode="true" data-group="nfv-pics" data-thumbnail="/assets/images/immigration/nfv-changechannel.png" class="html5lightbox" title="Change the channel of a traveller">
</a> 
<a href="/assets/images/immigration/nfv-identify.png" data-fullscreenmode="true" data-group="nfv-pics" data-thumbnail="/assets/images/immigration/nfv-identify.png" class="html5lightbox" title="Manually identify a traveller">
</a>
<a href="/assets/images/immigration/nfv-person.png" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/nfv-person.png" class="html5lightbox" style="width:49%;display:inline-block;" data-group="nfv-pics" title="AO can select a traveller to view all their details">
	<img src="/assets/images/immigration/nfv-person.png"/>
</a>   
<a href="/assets/images/immigration/nfv-personsolo.png" data-fullscreenmode="true" data-group="nfv-pics" data-thumbnail="/assets/images/immigration/nfv-personsolo.png" class="html5lightbox" title="Individual traveller">
</a> 

<a href="/assets/images/immigration/nfv-cameras.png" data-fullscreenmode="true" data-group="nfv-pics" data-thumbnail="/assets/images/immigration/nfv-cameras.png" class="html5lightbox" title="Set the traveller view directions">
</a> 

### Architecture and Technology
<a href="/assets/images/immigration/nfvflow.jpg" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/nfvflow.jpg" class="html5lightbox" style="width:58%;display:inline-block;" data-group="com-flow-diagrams" title="Flow of traveller tracking solution">
	<img src="/assets/images/immigration/nfvflow.jpg"/>
</a>
<a href="/assets/images/immigration/declaration.png" data-fullscreenmode="true" data-thumbnail="/assets/images/immigration/declaration.png" class="html5lightbox" style="width:38%;display:inline-block;" data-group="com-flow-diagrams" title="Flow of initial declaration submission">
	<img src="/assets/images/immigration/declaration.png"/>
</a>


#### Traveller tracking solution
 - __CameraEyeLib__ (Outputs jpeg stream and retrieves facial and channel data from watch service)
    - C# service
 - __Camera Event Service__ (Sends processed frame event data off to client and conductor)
    - C# Web API to access camera config etc
    - SignalR to broadcast processed frame info
 - __SignalR Service__ (Brokers messages)
 - __Conductor__ (Handles detected heads in frame, raises any notifications and updating traveller details/logs accordingly, Handles API requests to access/update traveller info)
    - .Net 4.6.1
    - SQL Server DB (14.0.3008)
    - EntityFramework (6.1.3)
    - LINQ
    - C# Web API (5.0.0)
    - Ninject (3.3.0)
    - Multiple C# Services (handle frame events to update person info)
 - __Officer View__ (Handles event stream to display channel icons on travellers, allows officer to access, update and asses any traveller on camera or by search)
    - Angular 4.4.x, CLI 1.6.5, Material 2.0.0-beta.16, rxjs ^5.5.6, SignalR
    - Structured, modular codebase
 - __Traveller View__ (Basic app which draws the boxes on the travellers heads and tells them which way to go)
    - Same stack

#### Declaration submission solution
App allows creation of IPC, and submission to a database which can then be used to assign a travellers channel.

 - __Db__
    - SQL Server
 - __Declaration API__
    - C# .NET Web API (5)
 - __Management__
    - Angular 4.4.x app, SurveyJs for form creation and management
 - __Declaration App__
    - Ionic (4.5.x) [native storage, barcode scanner], Angular 4.4.4 app,surveyjs], 
        - multilayer barcode creation, sql-storage, offline capability
 - __Kiosk__
    - Same as declaration app


### Deployment
Having multiple environments, for testing, staging, locally etc allows us to have complete control of what we are testing. It lets us test individual components and omits the reliance on seperate parts of the system.

 - Each module shown in diagram above performs __continuous deployment__
     - __Windows server__ to store environments and builds and to run the windows services
     - __TeamCity__ for automated builds
     - __Octopus__ to deploy out to multiple environments


### Challenges
- Accomodating for and __optimising the amount of processing power required__ to handle multiple simultaneous facial detection cameras and keep the stream __delay to an absolute minimum__
- Modifying system and ensuring rigorous testing has been conducted when pushing features or fixes to live
- __Handling of multi threaded services__ and resolving hard to debug threading issues
- Getting head around project with lots of moving parts, each with multiple environments and settings
- Adjusting to corporate culture and contributing positively within a team of 10+ senior people in a time constrained environment


### What I found fun
- __Handling the real time face processing and turning this into an interactive video feed__, drawing boxes and outlining information on the view
- The final rush to deliver the prototype seen all the developers converge to one location - real team spirit and felt like a hackathon
- Having a tangible output to the project, and one which was impressive and highly regarded


## Conclusion
- Good to work on complex, challenging project with a tangible output
    - __Inspired me to work on products that provide value__ and not just programming for its own sake
- Working is more thrilling when everybody is excited and working hard to deliver a product



