---
title: How to create a subscribe form for Jekyll that actually works!?
desc: Subscribe form for Jekyll was not available because all forms tend to work with php code to send emails. But with this method we can add a subscribe form for Jekyll websites which works out of the box.
keywords: 
author: sharathdt
tags: Jekyll
image: jekyll-subscribe-form.jpg
layout: post
---

<img alt="jekyll subscribe form" title="subscribe form Jekyll" itemprop="thumbnailUrl" class="left half noborder" src="{{ site.url }}/thumbs/jekyll-subscribe-form.jpg">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>Subscribe form for Jekyll was not available because all forms tend to work with ```php``` code to send emails. But with this method we can add a subscribe form for Jekyll websites which works out of the box. I'm another step closer to compete with WordPress blogs!
{: .intro}

## Why use a subscribe form?
{: .clear}
Subscribe form is used basically to collect visitors' emails to provide them an update of new articles every time you post a new one. Also, a good way to get some initial traffic to a new post. 

Many bloggers use the mailing list for affiliate marketing. I don't think it is a bad idea. If a user is interested in the stuff blogger is selling, then it is a win-win. 

WordPress has an advantage with many plugins that can do the job without breaking a sweat. But, after moving all my blogs from WordPress to Jekyll I had to find an alternative for subscribe forms.

This is one of those things I always wanted in Jekyll but did not know how to execute. This idea hit me while I was having a shower! Initially, I tried to create a form with [FormSpree](http://formspree.com){:rel='nofollow'}{:target="_blank"} similar to [how I created a contact form](/how-to-add-form-option-to-jekyll-websites/){:target="_blank"}. It was a painful experience. FormSpree requires verification. This verification is URL specific. If the form is on all the pages of the website then I have to verify an email for every single page! FormSpree is good if you are using it on a specific page but not for all pages. What clicked to me in the shower is that SimpleForm can be used to make a contact form which works on all pages!

What I'm showing here is an email collector. So it just collects users' emails. I think that is what a basic subscriber form does. You can also setup an auto-reply option. Auto-reply can help if you are offering an e-book for a subscription. I haven't tried it yet but it should work.

But before collecting emails you should have an email id. You can use any email id but it is a good idea if you use a domain email. If you don't have one, then get a [free domain email using ZOHO](/free-domain-email-zoho/){:target="_blank"}.


## How to make a subscribe form on Jekyll blog?

We are using a free service called [**SimpleForm**](https://getsimpleform.com/){:rel='nofollow'}{:target="_blank"} to create our form. SimpleForm is a service similar to Formspree which I discussed in [How to make a contact form in Jekyll](/how-to-add-form-option-to-jekyll-websites/){:target="_blank"}

I'm not using Formspree because it doesn't work on all pages. Formspree is URL specific. If you want your subscribe form to be on all the pages(which is usually the case), SimpleForm has to be the logical choice.

### Step 1: Get an API Token from SimpleForm
![Jekyll subscribe form](/images/jekyll-subscribe-form-simpleform.jpg){: .full}

Enter the email address you want to use in the input field and click on **Send me a token**

You should receive an email with the token similar to this one
{% highlight css %}
Your form api token is c7b404f97b2e45f982ffed4995bf42af
{% endhighlight %}

{% include adsense-inside-post.html %}

### Step 2: Create a form
![Jekyll subscribe form](/images/jekyll-subscribe-form.jpg)
{: .right}

Now create a form in Jekyll with only email input in it and change the action according to SimpleForm documentations. You can create it in a separate page so that users will go to that page and subscribe or you can create it in the default layout so that the form is available on all pages.

{% highlight html %}
<form action="https://getsimpleform.com/messages?form_api_token=c7b404f97b2e45f982ffed4995bf42af" method="post">
    <li class="contact-li">
        <input type="email" placeholder="Your email" id="email"/>
        <input type="submit" value="Subscribe" id="submit"/>
    </li>
</form>
{% endhighlight %}


### Step 3: Create a success page
Once the user enters his email in the form and hits subscribe, he should be shown a message that he has successfully subscribed to the updates. Create a thank you page in Jekyll and redirect users to that page after successful submission.

**Form with redirection**
{% highlight html %}
<form action="https://getsimpleform.com/messages?form_api_token=c7b404f97b2e45f982ffed4995bf42af" method="post">
  <!-- the redirect_to is optional, the form will redirect to the referrer on submission -->
    <li class="contact-li">
        <input type="email" placeholder="Your email" id="email"/>
        <input type="submit" value="Subscribe" id="submit"/>
    </li>
         
   <!-- the redirect_to is optional, the form will redirect to the referrer on submission -->
    <input type="hidden" name='redirect_to' value="/path/to/thank-you.html"/> 
         
</form>
{% endhighlight %}


**Typical thank you page**
{% highlight html %}
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Thank you</title>
    </head>
    <body>
        <h1>Thank you. Your entry has reached us!</h1>
    </body>
</html>
{% endhighlight %}


### Step 4: Success!
That's it. Now collect emails and make a list. I use mail-chimp and I send an update to the list using campaign every time I make a new post.

Here is a working example: <a href="http://redgadget.github.io/form-jekyll/" target="_blank" rel="nofollow">Sample Subscribe Form</a>

I hope that helped. I'm using feed-burner for subscriptions. I will make a post on how to do that as well. Don't forget to subscribe to my updates!

## Update 1 - Automated subscription list

[steven_nc](https://disqus.com/by/steven_nc/){:rel='nofollow'}{:target="_blank"} commented that there should be an un-subscription option for users, which is a valid question because users may want to opt out of your mailing list. Thanks to him for bringing up this topic.

As I have mentioned in the article this is a completely manual subscription handling. But what if someone wants a automated list generation? where after subscribing the email will be collected automatically and if someone wants to un-subscribe, they can do that as well.

Many a times, emails that you send to your subscribers should have an unsubscribe link. Otherwise, email providers may mark it as spam. Since it is not practical to create a un-subcsribe link and include it every time you send an email, you can opt some third party email subscription handlers.

I prefer these two email subscription handlers - Aweber or MailChimp. I suggest MailChimp for beginners. [Create an account in MailChimp](http://eepurl.com/bWHZgb){:rel='nofollow'}{:target="_blank"} for free.

MailChimp has an option to [create a list](https://us10.admin.mailchimp.com/lists/new-list/){:rel='nofollow'}{:target="_blank"}(which will be automatically updated upon new subscriptions and un-subscriptions), an option to create a form for normal websites and an embeddable form for static websites.

For Jekyll websites one must choose embeddable forms. Here is how the code looks like

{% highlight html %}
<!-- Begin MailChimp Signup Form -->
<link href="//cdn-images.mailchimp.com/embedcode/classic-10_7.css" rel="stylesheet" type="text/css">
<style type="text/css">
	#mc_embed_signup{background:#fff; clear:left; font:14px Helvetica,Arial,sans-serif; }
	/* Add your own MailChimp form style overrides in your site stylesheet or in this style block.
	   We recommend moving this block and the preceding CSS link to the HEAD of your HTML file. */
</style>
<div id="mc_embed_signup">
<form action="//redgadgets.us10.list-manage.com/subscribe/post?u=210acce5db69d3d4a04b0e25d&amp;id=a268d63442" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
    <div id="mc_embed_signup_scroll">
	<h2>Subscribe to our mailing list</h2>
<div class="indicates-required"><span class="asterisk">*</span> indicates required</div>
<div class="mc-field-group">
	<label for="mce-EMAIL">Email Address  <span class="asterisk">*</span>
</label>
	<input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL">
</div>
	<div id="mce-responses" class="clear">
		<div class="response" id="mce-error-response" style="display:none"></div>
		<div class="response" id="mce-success-response" style="display:none"></div>
	</div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_210acce5db69d3d4a04b0e25d_a268d63442" tabindex="-1" value=""></div>
    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>
    </div>
</form>
</div>
<script type='text/javascript' src='//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js'></script><script type='text/javascript'>(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
<!--End mc_embed_signup-->
{% endhighlight %}

I have a working form as well!

<!-- Begin MailChimp Signup Form -->
<link href="//cdn-images.mailchimp.com/embedcode/classic-10_7.css" rel="stylesheet" type="text/css">
<style type="text/css">
	#mc_embed_signup{background:#fff; clear:left; font:14px Helvetica,Arial,sans-serif; }
	/* Add your own MailChimp form style overrides in your site stylesheet or in this style block.
	   We recommend moving this block and the preceding CSS link to the HEAD of your HTML file. */
</style>
<div id="mc_embed_signup">
<form action="//redgadgets.us10.list-manage.com/subscribe/post?u=210acce5db69d3d4a04b0e25d&amp;id=a268d63442" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
    <div id="mc_embed_signup_scroll">
	<h2>Subscribe to our mailing list</h2>
<div class="indicates-required"><span class="asterisk">*</span> indicates required</div>
<div class="mc-field-group">
	<label for="mce-EMAIL">Email Address  <span class="asterisk">*</span>
</label>
	<input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL">
</div>
	<div id="mce-responses" class="clear">
		<div class="response" id="mce-error-response" style="display:none"></div>
		<div class="response" id="mce-success-response" style="display:none"></div>
	</div>
    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_210acce5db69d3d4a04b0e25d_a268d63442" tabindex="-1" value=""></div>
    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>
    </div>
</form>
</div>
<script type='text/javascript' src='//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js'></script><script type='text/javascript'>(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
<!--End mc_embed_signup-->


<p>Once you enter the details, hit subscribe key. You should receive an email right after the subscription</p>

<p>I hope that covers almost all types of subscriptions possible. Let me know which one you implemented and for what reason.</p>

<p>Thanks for reading!</p>
