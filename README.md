# Raspberry Pi Media Server

I will show you have to setup a miniDLNA server using Raspberry Pi (RPI). When you are finished configuring the server, you will be able to access your videos, photo or music from this server. It would be advisable to have some form of external storage connect via usb.

## Getting Started

These instructions will specifically show how to setup video streaming.
If you followed my instruction on how to setup [Torrent Server](https://github.com/asparatu/raspberrypi-transmission-daemon-client), you will be able to use the same Raspberry Pi as media server.

**Disclaimer** \
I will assume you already have Rasbian Lite installed and you can connect to the RPi via ssh server. This will not show how to install Rasbian OS. I will only show you how to install media server and to configure it.

### Media Players

In order to watch the stream from media server, you can use [VLC media player](https://www.videolan.org/vlc/) or [Windows Media Player](https://www.microsoft.com/en-us/download/windows-media-player-details.aspx). VLC media player is good, but in order to see newly added videos you need to close VLC and reopen it. Windows Media Player automatically updates the streams play list.

## Installation

Step-by-step instructions on how to setup the media server.

### How to install miniDLNA server

We are going install the miniDLNA server from the RPi repository. I would recommend that we update and upgrade the RPi before installing the miniDLNA server.

```bash
sudo apt-get update && sudo apt-get dist-upgrade -y
```

We are going install the miniDLNA server now. The installation is easy and should only take about 1 or 2 minutes depending out your internet speed.

```bash
sudo apt-get install minidlna -y
```

### How to configure the Media Server

In order to configure the media server, we need to edit the configuration file. We do it by entering this command.

```bash
sudo nano /etc/minidlna.conf
```

Since, we are going to make so streams videos, we have to change the **media_dir** path to point the torrent complete directory, if you are using this on the torrent Server, but if not will be on the what directory you would like to use.

The is examples of how you can configure the different **media_dir**.

```bash
#   * "A" for audio    (eg. media_dir=A,/var/lib/minidlna/music)
#   * "P" for pictures (eg. media_dir=P,/var/lib/minidlna/pictures)
#   * "V" for video    (eg. media_dir=V,/var/lib/minidlna/videos)
```

To configure for the videos we will use the third option in the examples.

```bash
media_dir=V,/media/storage/torrent/complete
```

**Note**: You can have more then one **media_dir** in the config file, but you need to prefix the path with **A,** or **P,** like in the example.

If would looks something like this:

```bash
media_dir=V,/media/storage/torrent/complete
media_dir=P,/media/storage/pictures
media_dir=A,/media/storage/music
```

Enable the logging on the media server buy removing to **#** next to **log_level**, **db_dir**, **log_dir**, **inotify**, **minissdpdsocket**, **album_art_names** and leave the default values.

We need to change the value and enable **notify_interval** like before remove **#** to enable and change the value to **300**.

```bash
notify_interval=300
```

Set the name that will show up on the clients. Just remove the **#** to enable and the name can have spaces in them like my example.

```bash
friendly_name=Test Server
```

Save the file by pressing **ctrl + x**, press **Y** and press **Enter**

Restart the service by using this command:

```bash
sudo service minidlna restart
```

If does not work you can force to restart by using this command:

```bash
sudo service minidlna force-reload
```

If you do not have VLC media player installed, open Windows Media Player and goto playlist and you should see your server name listed under **Other Libraries**.

## Authors

**Shane Saunders** - *Initial work* - [asparatu](https://github.com/asparatu)


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
