---
layout: post
title: "What is Amethyst Grid?"
description: "Answering the whats and hows and whys."
category: existence
tags: [grid, amethyst]
imagefeature: whatgrid.jpg
share: true
comments: true
featured: true
author: io
---

![](/images/grid.svg)

I haven't been to a lot of networking events, nor have I met with a lot of startup
guys but I have talked to the people around me. There's a lot
less pressure while answering their questions. Except for the million dollar one.

>What are you building? What exactly is Grid?

My answer involves wrenching guts, sweating palms, and a fake smile. It is not that I don't
have a definition of Grid, I do, but that definition is not what people want to
hear. What they really want to know is _What am I building for them?_ or _What value
does my product bring to them?_. And THAT is a tough question. Tough, because Grid
does not do just one thing, it has myriad applications. And when someone asks `What
does Grid do?`, it is like a brain system crash. We really needed to sort this out,
and we did. This post answers all the questions, and clears the air around Grid.

##What are we building?

If you were to go back to the year 1974 and claim that the computers are going to change the way
we live our daily lives, that each person should own a PC, you probably would seem like this guy.

![BUY A PC!!!](/images/ein.jpg)

Those were the days when computers were seen as some scientific machines only to be used by scientists or wizards.
The mere thought of owning a PC was simply impalpable. But then it happened. 1977, Apple 2 is launched, and the world
loses it. The year heralded the era of personal computing.


We live in the age of data, where everything that surrounds us is linked to a data source and everything in our lives is captured digitally. Now just take a minute to think about all the ways you are using this data.

Well, my list was just blank. The applications I use, the websites I visit, all of them track my data and make their service adapt to my
taste or style. But, the intimacy, it's just shallow. It's always about suggested friends on social networks or "_Here's what others bought..._" kind of suggestions. The data always affects you in an **indirect** way.

Not that I can, but I too don't bother to consume the data around me. It's just there, but I don't have a way to reach it. I am fine with google now cards and suggested pages on facebook. But what if there was a way to reach this mid air floating data? What if you could know all about your vicinity? Say, know if the inbound bus is crowded or not so that you could take the metro. Or, how long is the token queue at the metro station? Or, just about anything related to your surroundings?

We are building a future where you use data **directly**, where you don't think it's for just scientists and wizards.
<br/>
<br/>
<br/>

##What exactly is Grid?
<br/>
If a good sounding portmanteau of words AI and Network existed, we would have gone for that as the name over `Grid`. But sadly there isn't one.

Grid can be seen as a mobile application which does just 4 things. **First**, it uses your phone's Bluetooth and WiFi to build a decentralized p2p network. **Second**, it acts as a platform so that other apps built by developers can use this network. **Third**, it lets you query your surroundings. For eg:*"Find a coffeehouse near me with the least crowd"*. **Fourth**, learns your preferences and style and gives you notifications on that basis.
**But since
it's a P2P network, this data stays on your phone only. No cloud, no servers, not even a scratch to privacy.**


![system](/images/csystem.jpg)

<br/>

Each of the 4 features, rather services, disrupt the way you consume data or connect. The P2P network acts as a backup
to the Internet. It can work when there is no signal or no connection to Internet. And the AI/Data system built over it gives you immense amount of power and a real sense of control. The system could be used as a **Vehicle to Vehicle communication** module. It could alert you about speeding vehicles coming from behind or could help you avoid accidents in 0 visibility scenarios. The possibilities are infinite. Everything depends on how you decide to use it.


##The customary API

Grid would be absolutely useless if one can not build applications for it. And for that reason, we have built a framework
which makes it possible for developers to craft unique experiences on Grid. The plugins(applications for Grid) are normal
applications which can interact with the main Grid app through IPC. A `get started` will be added very soon, so that
you can begin with the development.

####Sample code which looks dead easy to use
{% highlight java %}
@Override
    public void onLoad() {
         /*What to do when the plugin loads. Here, we will simply Log the loading,
           because have nothing to intialize.*/

        Log.i(LOG_TAG, "onLoad: Plugin Loading.");
    }

    @Override
    public void run() {
        /*This is where you plugin really starts running. Configurations are complete
        and now you can "do the tango".
        For this example, we will launch an activity called "PluginActivity".
        This is your launcher activity.*/

        Log.d(LOG_TAG, "run: Running ChatterPlug. Starting Activity");
        Intent intent = new Intent(getBaseContext(), PluginActivity.class);
        intent.setFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
        startActivity(intent);
    }

    @Override
    public void onUpdate(PluginConfiguration pluginConfiguration) {
        /*What to do when the plugin receives an update from the Amethyst app.
        This method is intended to be used to monitor Grid
        activity like change in device's Grid-State. We'll just log this too,
        'cause..well.. this is just an example.*/

        Log.i(LOG_TAG, "onUpdate: Update received.");
    }

    @Override
    public void onUnload() {
        /*This is the exit point of your plugin. By now, your connection with the
        Amethyst app has been terminated is
        in the process of termination. So, you know, clean up after yourself,
        like close any services you started,
        or save data to the device.*/   
    }

    @Override
    public void onMessageReceived(PluginMessage pluginMessage) {
        /*This method is called when you receive a message from someone
        on The Grid. Handle this the way you want.*/
        Log.i(LOG_TAG, "onUpdate: Received updates. They are:");
        // Describe the contents of this message
        pluginMessage.describeContents();
    }
{% endhighlight %}

##Moar plugins
We have 3 plugins lined up for you. The first one is a simple social network which runs on Grid.
Second we have `Aether`, it is the www of our network and the de facto browser for us.
Lastly, we have `Zeal`, it is a music app which streams the music located on your device to the
nearby Grid users.

![Zeal](/images/zeal.jpg)



##The Grid app

We have been working on it since a year now, and there was a plan of having a private beta
but we had to scrap that up because things broke too easily. The API and the network, both
have been tested extensively now, and the results are promising. We upgraded our plugin framework, and
the network as well. It is now far more easier to use the API and the host app's battery usage
has been brought down too. We plan to have an alpha in February and a private beta in March.

And now we are on the same page regarding the project. You have a clear idea of it now and we would
really love to talk more about it if you want. And it would be really awesome if you helped us
in building Grid and its plugins. Hit us up at [team@amethystlabs.org](mailto:team@amethystlabs.org), and
be a part the change.

>Never doubt that a small group of thoughtful, committed citizens can change the world; indeed, it's the only thing that ever has.
>
>-Margaret Mead

![mockup](/images/tada.jpg)
