Autoconnect wifi ubuntu

    #!/bin/bash

    wlan=`/sbin/ifconfig wlan0 | grep inet\ addr | wc -l` 
    if [ $wlan -eq 0 ]; then
    service network-manager restart 
    else
    echo WIFI IS UP
    fi

Save the script and make it executable.

    sudo chmod +x filename.sh

Now there are several ways of making sure that our script is being executed every x minutes. The easiest way of accomplishing that I think is by using the command watch.
    sudo su
    watch -n 600 sh filename.sh

What it does is execute our filename.sh script every 600 seconds.
Or you implement a so called cron job  

    sudo crontab -e

Add the following

    PATH=/usr/sbin:/usr/bin:/sbin:/bin
    */5 * * * * sh /home/username/filename.sh

*/5 * * * * means that the task will run every 5 minutes.

[source](http://linhost.info/2013/09/automatically-mount-a-usb-drive-in-ubuntu-server/)
