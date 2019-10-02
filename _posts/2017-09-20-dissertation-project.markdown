---
title: "Providing mobile access to clinical data in challenging environments"
layout: post
date: 2016-07-20 14:40
image: /assets/images/diss/logo.jpg
headerImage: true 
wide: true
tag:
- Ionic
- Location based content
- Offline access
- SQL
category: project
subCategory: web
---

<style>
 .diagram{
	 width:100%;
	 max-width:640px; 
	 display:block;
	 margin: 0 auto;
 }
</style>


## When
Dec 2015 - Jun 2016

## What
I teamed up with my previous employers [Clarity Informatics](https://www.clarity.co.uk/) to develop a cross platform mobile solution that would enable users of their [Clinical Knowledge Summaries (CKS)](https://www.clarity.co.uk/clinical-knowledge-summaries/) to access the provided content, particularly accounting for those users with intermittent or non functioning network connections. 


## Why
It was the third year of my BSc Comp Sci and for my dissertation I wanted to get some experience developing mobile apps. I contacted Clarity, with whom I had built a good relationship the previous year on placement, who described to me their problem and offered to put me back on the books.   
Essentially Clarity produce a large amount of high quality clinical data in the form of [CKS](https://www.clarity.co.uk/clinical-knowledge-summaries/) topics (e.g. Asthma, Meningitis) which are used by primary health care professionals globally to assist their day to day work in making informed diagnosis and prescribing of patients (some cases in crucial or time constrained environments). So we have a large amount of structured information which requires an active internet connection to view, and the possibility of users needing urgent access in the presence of intermittent or non functioning networks. My job was to develop a prototype solution that will allow users even in complex environments to have the information they need to treat their patients. Merely downloading all topics at once was not feasible due to their size and constant update process.
You can read more on the context of the problem [in my project proposal](/assets/documents/Project_Proposal.pdf) or [in my full dissertation](/assets/documents/Dissertation.pdf).

## Development

### Methodology
An Agile development methodology was adopted here, beginning with system planning and rapid prototyping in order to get the app into a somewhat workable state. I then compiled a list of the possible complex end user scenarios, analysed the functionality requirements needed to serve content to the user, and then iteratively satisfied each use case, as outlined <a href="/assets/images/diss/agile-plan.png" class="html5lightbox" title="Figure 1" data-description="Agile development plan">in this diagram.</a> 

### Architecture and Technology
In order to achieve cross platform compatibility, the core of the application was developed using __[Ionic v1](https://ionicframework.com/)__ and __[Cordova](https://cordova.apache.org/)__ which allow you do develop hybridly using __HTML, CSS and AngularJS__ and then build native packages for __Android, iOS and Windows__ (Note: A second version of the app was developed in __Ionic 2__ - detailed [in another post]({{ site.url }}/UX-rework)).  
The content for the CKS topics was stored in a __SQL__ database and accessed via a __C# .NET Web API__ both hosted in an __[Azure](https://azure.microsoft.com/en-gb/services/app-service/web/) service__, allowing for fast retrieval of data and easy API updates.  
In order to save data internally, for caching and UX purposes, I made use of a __SQL plugin__ [SQLite](https://ionicframework.com/docs/native/sqlite/). Raw SQL was used here to create structured tables with a memory limit and fast retrieval time.  
*Keywords: HTML, CSS, JavaScript, AngularJS, Ionic, Cordova, C#, .NET Web API, SQL, Azure*

<a href="/assets/images/diss/architecture.png" class="html5lightbox" title="Figure 2" data-description="System architecture">
	<img src="/assets/images/diss/architecture.png" class="diagram"/>
</a> 

### How I solved the problem
 - Caching to reduce request frequency
	- After <a href="/assets/images/diss/db-comp.png" class="html5lightbox" title="Figure 3" data-description="Database comparison">analysis</a> of various internal DB options, SQLite was installed in order to cache each topic that was requested. If a topic was already in the cache, it would load from memory instead of sending a GET request 
 - Breaking down HTTP response size
	- CKS Topics have 11 base sections, which I <a href="/assets/images/diss/topic-breakdown.png" class="html5lightbox" title="Figure 4" data-description="Breakdown of topic sections">divided up into 4 chunks</a> to minimise the size of the response, which was found to be the most optimal separation(see here). Updating the SQL DB and API, I was able to allow the user to only request the section they were wishing to view. The internal storage was updated for this new format and optimised by introducing a max amount of storage 
 - Saving and bookmarking of content
    - Making use of the underlying technology for caching, I added functionality to let the users save particular topics to an un-capped persistent SQL DB for quick and easy access. They can also bookmark particular sections within these topics for fast access
 - __Location based push functionality__
	- It was seen as a very useful service for us to be able to inform users of outbreaks or epidemics within x miles of their geolocation, with the aim to ensure that not only are primary healthcare professionals aware of the outbreak, but they have the correct knowledge and tools to make the most informed decisions
	- Upon loading the app, each users mobile details alongside GPS co-ordinates were <a href="/assets/images/diss/push-save.png" class="html5lightbox" title="Figure 5" data-description="Workflow to save users details">sent to our user storage DB on Azure</a>. If an outbreak was to occur, I could query the API with some co-ordinates and a search radious and it would return us a list of the user tokens within that range. A script could then be run to create a POST request containing the push notification and its payload, which would then be sent out to all of the users in the area, making use of Ionics native push notification plugin.
 - Persisting of evidence
	- As the content is evidence based clinical guidance information, users will need to gain access to it in order to fact check what they are reading. I added a simple network connection check, if the user was offline then they would be prompted to save the evidence link to their reading list for future use  

You can view code snippets for most things mentioned above in my [dissertation - see ch 3.4 and corresponding appendix figures](/assets/documents/Dissertation.pdf)


### Testing
A bottom-up testing approach was executed and [detailed in my dissertation](/assets/documents/Dissertation.pdf), beginning with unit testing of all items in the application. These units were then compiled together and each feature or piece of functionality present in the application was tested. Following these tests End-to-End testing was conducted to ensure that the whole system was compliant and friendly with each other and worked as expected.


### Challenges overcome
 - Learning Ionic and Cordova from scratch, especially close after release without too much documentation. The time it takes to make mistakes and learn in development can quickly add up. During development Ionic deprecated a lot of their Beta code on v1 release which set me back
 - Accounting for and analysing all potential use cases
 - Restructuring of the large amount of data held by Clarity. When implementing features like 'onclick' methods into the html for topic navigation, the data itself had to be edited. A pipe is needed to transform old data into an app acceptable version
 - Ensuring web services were up and running and could operate in a test environment
 - Displaying a large amount of content on the page in a structured manner. While I struggled with this in the first iteration, a [UX rework]({{ site.url }}/UX-rework) conducted in a less time constrained environment produced better results

## Conclusion
Overall I ended up with a good prototype - fit for purpose. The location based push functionality proved to be the most useful when it came to alerting users in need. Time constraints meant I could not refine the UI although luckily I [came back to it later]({{ site.url }}/UX-rework). I learned a lot through this project and it was so beneficial to gain experience building an app from start to finish!



## Files
<a href="/assets/documents/Dissertation.pdf" download>:file_folder:Dissertation PDF</a>  
<a href="/assets/images/diss/project-poster.jpg" class="html5lightbox">
  :page_facing_up:Dissertation project poster
</a>

<a href="/assets/images/diss/architecture.png" class="html5lightbox" title="Figure 2" data-description="System architecture">
	<img src="/assets/images/diss/architecture.png" class="diagram"/>
</a> 






