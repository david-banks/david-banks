---
layout: post
title: SSL/TLS Local Development IIS
subtitle: Setting up a local IIS SSL/TLS website
date: 2019-07-11 08:00:00 +0000
thumb_img_path: "/images/https-logo.png"
content_img_path: "/images/https-logo.png"
excerpt: 'Intercepting HTTP/2 on a Local IIS '

---
# Setting Up IIS

Create a standard, plain text website on IIS. Mine just contains an `index.html` which displays _Hello World!._ I've also added an entry to my `HOSTS` so I can pretend that it's a real website.

**This may not be the best practice way to achieve this. It's certainly not secure and not suitable for production.**

We'll create a self-signed certificate. There are several ways to do this, I think this is the easiest way.

Open IIS Manager and select the server.

![Select the Server Configuration option from the server features.](/images/IIS-ServerFeatires.PNG "IIS Server Features")

Double-click on the _Server Certificates_ feature.

![IIIS Server Certificates Feature](/images/IIS-ServerCertificates.PNG "IIS Server Certificates Feature")

Select the _Create Self-Signed Certificate_ action on the right.

![](/images/IIS-SpecifyFriendlyName.PNG)

Give your certificate a meaningful name and return to the manager window and select your site. Not select the _Bindings_ action on the right.

![Site Bindings dialogue](/images/IIS-WebSIteBindingsHttp.PNG "Site Bindings dialogue")

Click _Add_ to add a new binding.

![Add Site Binding Dialogue](/images/IIS-AddNewHttpsBinding.PNG "Add Site Binding Dialogue")

Set the _Type_ to `https`, give the host name and select the certificate you just created and click _OK_.

Now navigate to your site in your browser (over HTTPS).

![](/images/Chrome-HttpsBackToSafety.PNG)

You'll get a warning telling you that the certificate can't be validated. This is OK because we know we're using a self-signed certificate that isn't secure.