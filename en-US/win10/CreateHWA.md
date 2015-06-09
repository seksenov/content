---
layout: default
title: CreateHWA
permalink: /en-US/win10/CreateHWA.htm
lang: en-US
---

#Create a Hosted Web App

Learn how to quickly create a Hosted Web App for Windows 10 starting with your website URL. All you'll need to do is add your site url to a Windows xml manifest, set your image resources to use for app tiles and store discovery and pacakge it up. Continue by adding native platform integration from JavaScript hosted on your servers in a matter of minutes. 

##What you need
1. **Windows 10 Insider Preview** - make sure to install the Windows 10 SDK
2. **Visual Studio RC 2015** - to build the appx package that you submit to the store

##Follow these steps to convert a Website into an Web App on Windows

1. **Start with a website url**
	* If have an existing website that will work great as a single page app and preferably you are the owner/developer of the site so you are able to make chages.
	* If you don't have an url in mind the tutorial will walk you through using this [Codepen Example](http://codepen.io/seksenov/pen/wBbVyb/?editors=101) (http://codepen.io/seksenov/pen/wBbVyb/?editors=101) as the URL
	* Copy your URL or the Codepen URL above to use throughout the tutorial

	<br>

2. **Launch Visual Studio**
	* At minimum you will need Visual Studio 2015 RC released for //BUILD with the SDK installed
	* Launch Visual Studio
	* Click "File -> New Project" and choose "JavaScript -> Windows -> Windows Universal -> Blank App (Windows Universal)" 

	<br>
	**Choose the blank JavaScript Template**
	<img src="{{site.baseurl}}/images/CreateHWA/BlankJSTemplate.PNG">

	<br>

3. **Delete unnecessary pacakged content**
	* Since this is a hosted web app where the content is served from a remote server you won't need most of the local app files that come standard from the JavaScript temple.
	* Go ahead and delete the local html, JS and CSS resources. All you'll need to keep is the appx manifest (Where you configure the app) and the image resources to be displayed in the store, start menu and on the taskbar.

	<br>
	**Delete hihglighted folders/files**
	<img src="{{site.baseurl}}/images/CreateHWA/DeletePackagedContent.PNG">

	<br>

4. **Set the Start Page URL in the appx manifest file**
	* Open the package.appxmanifest file
	* Under the <Application> node find the StartPage="default.html" tag
	* Replace "default.html" with "http://mysite.com/"
		* In this tutorial we'll use: http://codepen.io/seksenov/pen/wBbVyb/?editors=101 

	<br>

5. **Define the boundaries of your Application**
	* Add the Apllication Content URI Rules (ACURs) tag in the manifest in order to definte the URLs that are part of your app. If users click on URLs that aren't defined int he ACURs they will open in the default browser.
	* In the ACURs you are also able to define URLs that can access native platform APIs directly. To do this use the WindowsRuntimeAccess tag as outlined below.
	* There are three levels of access "none" for no access (default value), "AllowForWeb" access to local in package runtime components, "all" access to the Windows namespace from remote code.

	<br>
	**Appx Manifest Additions**
	<img src="{{site.baseurl}}/images/CreateHWA/ManifestAddition.PNG">

	<br>
	
6. **Hit run!** 
	* At this point you have a fully functioning native Web App on Windows that is able to access platform APIs
	* Click or touch the System Prompt button to access the Windwos namespace from the script in the codepen

	<br>

7. **Add toast notifications** 
	* Just copy and paste the JavaScript code for Toast Notifications directly into the JS editor of the codepen
	* A button to invoke the showNotification() function was alredy presen, so go ahead, click it and watch the site display and toast notification

	<br>
	**Toast notifications**
	{% gist 2a08ea82483a0578d1aa %}
