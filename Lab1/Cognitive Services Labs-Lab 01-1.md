Cognitive Services Face API
============

> NOTE: this lab has been adapted from [David Giard's Hands-on Labs repository](https://github.com/DavidGiard/Cognitive-Services-Labs).

Microsoft Cognitive Services is a set of APIs that use the power of Machine
Learning to analyze, pictures, video, speech, and language.

Working through this set of exercises will help you understand how to call these
APIs, what data is required, and what data is returned.

Prerequisites: Azure Account and Editor
=======================================

This lab requires an Azure account. If you do not yet have an Azure account,
navigate to <https://azure.microsoft.com/>; click the [Start Free] button and
follow the instructions to sign up for a free Azure trial.

![](media/63ed4f948d4fce30f5224936792876ca.png)

You will need an editor for Exercise 4. I prefer Visual Studio Code, because it
is free, lightweight, and will run on Windows , MacOS, or Linux. You can
download Visual Studio Code at <https://code.visualstudio.com/>. But feel free
to use any editor with which you are comfortable.

Exercise 1: Get an API Key
==========================

In order to work with Cognitive Services, you will need an API key. Navigate to
the Azure Portal (<https://portal.azure.com>) and log in if prompted.

NOTE: If you do not have an Azure account, see the Prerequisites section above.

Click the [+ New] button in the left menu

NOTE: For some accounts, the word “New” is replaced by the words “Create a
resource”.

![](media/8c99e27f2f22b82aff257e484dc3cc90.png)

This will open the New Resource blade.

![](media/551833e9d93a1382ad6ddb508facdb5c.png)

In the “Search” box, enter “Emotion API” and press ENTER. The search results
should list “Emotion API (preview).

![](media/f6aa7b7dc5390d885d6b2ea91b94a0ef.png)

Click “Emotion API (preview)” to open the “Emotion API (preview)” blade.

![](media/c30615b1ae02257d9e131581f723af92.png)

Click the [Create] button to open the “Create Emotion API” blade.

![](media/c6eacedb7cab5bd99218d47073e145a8.png)

  
At the “Name” field, enter a name for this key.

At the “Location” dropdown, select “West US”.

At the “Pricing Tier” dropdown, select “S0”.

At the “Resource Group” field, select the “Create new” radio button and enter a
name for a resource group. A Resource Group is a logical container for Azure
resources.

Check the “Pin to dashboard” checkbox.

Check the checkbox to indicate you agree with whatever it says in the fine print
below it; and click the [Create] button to create a new Emotion API key.

After a few seconds, the key will be created and a shortcut will appear on your
desktop. Click the shortcut to open the newly-created Cognitive Services blade.

NOTE: You can also open this blade by “All resources” in the left menu and
selecting your newly-created Cognitive Service from the list.

![](media/08675f1ab51bcf493e72af1c29e01031.png)

There are 2 key pieces of information in this blade: the endpoint and the access
key. You can get to both from the “Overview” tab. Click the “Overview” link to
open the “Overview” tab.

![](media/bd2787b83b0fb969308ecffc5bab8d2d.png)

Record the Endpoint (probably
https://westus.api.cognitive.microsoft.com/emotion/v1.0). You can copy this
endpoint by clicking the Copy icon to the right of the URL.

![](media/2e25a80d3056fe6f6518f02936c5ddb7.png)

Click the “Show access keys…” link to open the “Manage keys” blade.

![](media/b44a32dc9db879c71c3bad9f28432347.png)

Record the value in KEY 1. You can copy this value by clicking the Copy icon to
the right of the key.

NOTE: Cognitive Services provides 2 keys in case one of the keys is compromised
and you need to re-generate it.

Exercise 2: Explore Cognitive Services
======================================

Open a new browser tab and navigate to the Cognitive Services home page at
<https://microsoft.com/cognitive-services>.

![](media/bbe58c9e1bd5959c593aecb841bbe11d.png)

Click the “Vision” link to display the Cognitive Services Vision page.

![](media/cb75ba0741b7955e6222b84fe0e752f1.png)

Click the “Emotion API” link to navigate the Emotion API page.

![](media/c112b3f738f9fa4ba89e047116272623.png)

Scroll down to below the “See it in action” section.

![](media/9ed897d97e5c884f805098d102d72604.png)

Click each of the images; observe the JSON returned from the API call. Note that
it always returns an array of faces, even though sometimes there is only one
face in the array. Note that each face includes a numeric score (between 0 and
1) for 8 different emotions.

Try it with one of your own images – either from your computer or from a web
search.

Exercise 3: Use the API Testing Console
=======================================

Near the top of the Emotion API page is a menu with links to documentation, the
API reference, and other useful information.

![](media/792c133e14564272df3a8e5a1a61966b.png)

Click the “API” link in this menu to navigate to the Emotion API page.

![](media/15d16716bf835fe7fc02481c64175e7d.png)

This page documents how to call the Emotions API web service, what parameters to
pass and what response to expect. By default, the “Emotion Recognition” method
is shown. Review this documentation.

Click the [Open API testing console] button to navigate to the Emotion API
Testing console.

![](media/2e4132e2f627f6fd048666dbe260cc77.png)

At the “Content-Type” dropdown, select “application/json”.

At the “Ocp-Apim-Subscription-Key” field, enter your Emotion API key from
Exercise 1.

At the “Request body” field, enter

{ "url": "
https://photos.smugmug.com/Tech-Community/GANGConf-2017/i-H2ZNBJT/0/c28d08df/L/IMG_7743-L.jpg"
}

NOTE: The URL above is a photo of the 5 mostly happy people below. You can
replace it with any image on the web that contains faces.  


![https://photos.smugmug.com/Tech-Community/GANGConf-2017/i-H2ZNBJT/0/c28d08df/L/IMG_7743-L.jpg](media/b480591c2740846148f08b55e745449c.jpg)

Details of the request will display at the bottom of the screen. Review these
details.

![](media/aca47ccd683fd5008d07713bf6579fb9.png)

Click the [Send] button to send an HTTP request. An HTTP request will be sent to
the web service URL and you will receive an HTTP response. The details of this
response will display at the bottom of the screen.

![](media/a76ecdf3b4ec88db733831e004ed0f97.png)

If everything worked properly, you should receive a response status of “200 OK”
and JSON with information about each face in the photo will display.

Review the response.

Any Response status of 400 or above indicates an error. Common errors are:

-   Entering an incorrect Ocp-Apim-Subscription-Key

-   Creating your key in the wrong region (This test is designed to work with
    West US)

-   Providing an image URL that either does not exist or is not publicly
    accessible

Exercise 4: Calling a Web Service from JavaScript
=================================================

In this exercise, we will write some JavaScript to call the Image Analysis API
and examine the data returned.

We will write JavaScript code to analyze the emotions of the faces in the photo
below (found online at
<https://photos.smugmug.com/Tech-Community/GANGConf-2017/i-H2ZNBJT/0/c28d08df/L/IMG_7743-L.jpg>.

![https://photos.smugmug.com/Tech-Community/GANGConf-2017/i-H2ZNBJT/0/c28d08df/L/IMG_7743-L.jpg](media/b480591c2740846148f08b55e745449c.jpg)

Create a folder named “CogSvcs” lab and navigate to this folder.

From this folder, launch Visual Studio Code the editor of your choice.

Create a file named “index.html”.

Add the following code to this index.html:

\<html\>

\<head\>

\<title\>Emotions API Demo\</title\>

\<script
src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"\>\</script\>

\<script src="script.js"\>\</script\>

\</head\>

\<body\>

\<h1\>Microsoft Cognitive Services\</h1\>

\<h2\>Emotions API Lab\</h2\>

\<div\>Image URL:\</div\>

\<input

type="text"

id="imageUrlTextbox"

class="urlInput"

value="https://photos.smugmug.com/Tech-Community/GANGConf-2017/i-H2ZNBJT/0/c28d08df/L/IMG_7743-L.jpg"\>

\<button id="analyzeImageButton"\>Analyze Image \</button\>

\<div id="ResultsDiv"\>\</div\>

\<div id="AngerDiv"\>\</div\>

\<div id="ContemptDiv"\>\</div\>

\<div id="DisgustDiv"\>\</div\>

\<div id="FearDiv"\>\</div\>

\<div id="HappinessDiv"\>\</div\>

\<div id="NeutralDiv"\>\</div\>

\<div id="SadnessDiv"\>\</div\>

\<div id="SurpriseDiv"\>\</div\>

\<div\>

\<img src="" id="imageToAnalyze"\>

\</div\>

\</body\>

\</html\>

Create a file named “script.js”

Add the following code to script.js:

\$(function () {

\$("\#analyzeImageButton").click(function () {

getImageInfo();

});

var getImageInfo = function () {

var subscriptionKey = "dc6d7936f86b4577bbb9750c91233f74";

var imageUrl = \$("\#imageUrlTextbox").val();

var webSvcUrl =
"https://westus.api.cognitive.microsoft.com/emotion/v1.0/recognize";

var resultsDiv = \$("\#ResultsDiv");

if (imageUrl) {

var body = '{ "url": "' + imageUrl + '" }';

\$.ajax({

type: "POST",

url: webSvcUrl,

headers: {"Ocp-Apim-Subscription-Key": subscriptionKey},

contentType: "application/json",

data: body

}).done(function (data) {

var scores = data[0].scores;

var angerScore = scores.anger;

var contemptScore = scores.contempt;

var disgustScore = scores.disgust;

var fearScore = scores.fear;

var happinessScore = scores.happiness;

var neutralScore = scores.neutral;

var sadnessScore = scores.sadness;

var surpriseScore = scores.surprise;

var angerText = "Anger Score: " + angerScore.toFixed(2);

var contemptText = "Contempt Score: " + contemptScore.toFixed(2);

var disgustText = "Disgust Score: " + disgustScore.toFixed(2);

var fearText = "Fear Score: " + fearScore.toFixed(2);

var happinessText = "Happiness Score: " + happinessScore.toFixed(2);

var neutralText = "Neutral Score: " + neutralScore.toFixed(2);

var sadnessText = "Sadness Score: " + sadnessScore.toFixed(2);

var surpriseText = "Surprise Score: " + surpriseScore.toFixed(2);

\$("\#AngerDiv").text(angerText);

\$("\#ContemptDiv").text(contemptText);

\$("\#DisgustDiv").text(disgustText);

\$("\#FearDiv").text(fearText);

\$("\#HappinessDiv").text(happinessText);

\$("\#NeutralDiv").text(NeutralText);

\$("\#SadnessDiv").text(sadnessText);

\$("\#SurpriseDiv").text(surpriseText);

\$("\#ResultsDiv").text("Success!");

}).fail(function (err) {

\$("\#ResultsDiv").text("ERROR!" + err.responseText);

});

}

};

});

Save both files. Open index.html in a web browser.

![](media/0bdee5f9ffb5e056c2af636f1118b052.png)

Click the [Analyze Image] button. You should see the scores displayed.

![](media/cbd5036796e50cdecaeccada334d9694.png)

If errors are reported, use the browser’s developer tools to step through and
find these errors. Pressing F12 brings up these tools in most browsers.

Search the web for more photos of faces with varying emotions and paste these
into the “Image URL” text box.

Exercise 5: Calling a Web Service from Python
=============================================

We can use the free Jupyter notebooks hosted on Azure to run Python code.

We will write Python code within a Jupyter notebook to analyze the emotions of
the faces in the photo below (found online at
<https://photos.smugmug.com/Tech-Community/GANGConf-2017/i-H2ZNBJT/0/c28d08df/L/IMG_7743-L.jpg>.

![https://photos.smugmug.com/Tech-Community/GANGConf-2017/i-H2ZNBJT/0/c28d08df/L/IMG_7743-L.jpg](media/b480591c2740846148f08b55e745449c.jpg)

Navigate to <https://notebooks.azure.com/>

![](media/40d1f00c146ed60c152403e6554ef6f2.png)

Click the [Get Started] button to display a *Sample Notebooks* library.

![](media/0b44d60d5e5daff86af3e9b2de2a9ca6.png)

  
Click the “Clone” link to create a copy of this library.

You may be prompted to log in with a Microsoft account (e.g., an outlook.com,
live.com, or hotmail.com login).

After you sign in, the “Clone Library” dialog displays.

![](media/3ec5fe00bfd6dd57a7a8207b9f553fc4.png)

Enter a descriptive name for the library and a url to access it. The URL may
contain only letters, numbers, and hyphens.

Click the [Clone] button to create a new library identical to the sample
library.

![](media/28bba9036dff5c42e42eb3374ba59f91.png)

Click the [+ New] link to open the “Add Items to Library” dialog.

![](media/7ba8c40013bf58607057f77354ea94fb.png)

At the “Item Name” textbox, enter “Emotion API demo”.

From the “Item type” dropdown, select “Python 3.6 Notebook”.

Click the [New] button to create a new Jupyter notebook and add it to this
library.

The newly-created notebook will now be listed in the library.

nb

![](media/f64e240ca59f14fb2a797d2d86c5278e.png)

Click the “Emotion API demo.ipynb” link to open this notebook. The notebook will
be empty except for an empty code box.

![](media/b79113d7aecb9d3e47fd415ea7998732.png)

  
  
Paste the following code into the code box:

import http.client, urllib.request, urllib.parse, urllib.error, base64  
headers = {  
\# Request headers  
'Content-Type': 'application/json',  
'Ocp-Apim-Subscription-Key': '*EmotionAPIKey*',  
}  
  
params = urllib.parse.urlencode({  
})  
  
try:  
conn = http.client.HTTPSConnection('westus.api.cognitive.microsoft.com')  
conn.request("POST", "/emotion/v1.0/recognize?%s" % params, "{'url':
'https://photos.smugmug.com/Tech-Community/GANGConf-2017/i-H2ZNBJT/0/c28d08df/L/IMG_7743-L.jpg'}",
headers)  
response = conn.getresponse()  
data = response.read()  
print(data)  
conn.close()  
except Exception as e:  
print("[Errno {0}] {1}".format(e.errno, e.strerror))  
  
Replace *EmotionAPIKey* with your Emotion API key created in Exercise 1.

Click the [Run] button on the toolbar.

If everything is correct, you should see JSON returned from the Emotion API
describing the image in the URL.

![](media/ce31d567894858c5c9deb7ceb820f970.png)

If an error is reported, review your code and correct the error.
