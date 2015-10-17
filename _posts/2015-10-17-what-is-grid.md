---
layout: post
title: "What is Amethyst Grid?"
description: "Answering the whats and hows and whys."
category: existence
tags: [grid, amethyst]
imagefeature: hompage-picture-01.jpg
share: true
comments: true
featured: true
author: io
---

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

We have devoted around a year to this project and have built an ecosystem
of applications, which don't need to rely on a third party connectivity media to operate.
In simpler words, we have made a layer, or a platform over current technologies,
which is basically what Internet would be if it didn't have so much of centralization.
Think of Grid as your portal to an independent network. Grid never ever depends on a third
variable. It will always build it's own network if needed or if a base is provided, it will use it
to craft out a decentralized network. One thing is for sure, there won't be central points of failures
in Grid and you wouldn't have to depend on someone else's service to connect.

##What exactly is Grid?
The world today is binary, you are either online or offline and Grid aims to change this scenario.
Talking about offline, a large percentage of population has Internet availability and uses it on the go.
I mean who doesn't have 3g or at least 2g on their phones, almost no one. Then what is the point of making
Grid work for offline cases, you might ask. You know the answer yourself, you are aware of the anxiety when
your Internet stops for 3 seconds. If the stalling of your social life can make you this much anxious, then imagine the plight
of people who really need to connect. Imagine a disaster struck city, with communications wiped out. Or imagine yourself walking
hurriedly towards home through an unsafe neighborhood at night with no signal on phone. These example clearly show the need of
a backup network, one which is independent and and controlled by the people themselves.

####Off the Internet

To become independent, Grid uses the resources of your smartphone to make a network of its own. Currently on Android, the
app will first search for Grid hotspots(phones which have tethering mode on) and if one is found, will connect to it and your
phone will become a part of a larger Grid. If there are no hotspots available, the app will turn your phone into one.
With such a network, which is formed by you and other users, it is impossible for it to fail because of conventional
problems. There are no central servers which can be brought down, there are no strings which control the network. It can
be a lifesaver in places which are often affected by floods or any disaster. Only a few minutes of connectivity too can help
in tracking survivors. Or if you find yourself in a dangerous neighborhood, you can always leverage Grid to contact and ask for help.

####On the Internet

We have you covered when you don't get a signal on your phone, but why would you need us when you are on Internet.
There is everything, literally the world, on net, so what is the purpose of Grid on Internet? To answer that, let us first look
at the current state of Internet. There are thousands of platforms which offer many services for users, they can use them to
connect, chat, or do anything they like. Users join the platform they wish to use and enjoy the services.Now take a moment to realize that you are so dependent on these platforms that if you are not on them then you are simply isolated. If you want to use
a service, you need to be on a platform. And if you think about it, these platforms control what you can do and can not.

With Grid we aim to change that. The app checks if Internet is available and if it is, then the users are connected directly
to each other without any central intervention, just like the offline case above. And now you don't need to depend on any platform to use a service. While working on it, I realized one thing, that Internet is great for long distance connections, without it we just can't do anything, but the way we have been using it renders it impossible for us to connect around us.
It's like everyone around you is invisible or simply non existent unless you visit the central park. In the park, you get everything, there are people, shops, everything, but outside of it, nothing.

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
        This is your launcher activity.
        Add it to the AndroidManifest.xml. Or dont, we will talk about the Manifest soon anyways.*/

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
We have 3 plugins lined up for you. The first one is a simple messenger which runs on Grid.
Second we have `Aether`, it is the www of our network and the de facto browser for us.
Lastly, we have `Zeal`, it is a music app which streams the music located on your device to the
nearby Grid users.

![Zeal](/images/zeal.jpg)



##The Grid app

We have been working on it since a year now, and there was a plan of having a private beta
but we had to scrap that up because things broke too easily. The API and the network, both
have been tested extensively now, and the results are promising. We upgraded our plugin framework, and
the network as well. It is now far more easier to use the API and the host app's battery usage
has been brought down too. We plan to have an alpha in december and a private beta in january(could start from Jan 15th).

And now we are on the same page regarding the project. You have a clear idea of it now and we would
really love to talk more about it if you want. And it would be really awesome if you helped us
in building Grid and its plugins. Hit us up at [team@amethystlabs.org](mailto:team@amethystlabs.org), and
be a part the change.

>Never doubt that a small group of thoughtful, committed citizens can change the world; indeed, it's the only thing that ever has.
>
>-Margaret Mead

![mockup](/images/tada.jpg)
