---
layout: post
title: "How to disable ALSA power save"
author: "Bruno Fusieger"
categories: "Reference"
---

Some speakers may show a buzzing sound when the sound card enters power save mode.
To avoid this problem you can disable the sound card’s power save mode completely

## Disable power save in this session only

Open a terminal and **as root** run the following command

{% highlight sh %}
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
{% endhighlight %}

## Disable power save permanently

To avoid this problem create a file in `/etc/modprobe.d/` named `audio_disable_powersave.conf`

{% highlight sh %}
sudo touch /etc/modprobe.d/audio_disable_powersave.conf
{% endhighlight %}

Now edit this file with the editor of your choice and add the following line

{% highlight sh %}
options snd_hda_intel power_save=0
{% endhighlight %}
