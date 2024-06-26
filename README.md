# `music tech`

music tech and home studio stuff.

## `contents`

1. linux studio computer setup
2. my plugins and instruments

## `instruments`

### `Yellotron`

Mellotron emulation based on [this patch](https://guitarextended.wordpress.com/2014/11/11/yellotron-a-mellotron-with-pure-data/) converted to a camomile plugin (tested as a VST3 in Ardour).

You need to download and add the sounds from [here](http://leisureland.us/mellotron.htm) as per [these instructions](https://patchstorage.com/mellowtron-rework/)

## `studio setup notes`

Here are my notes on using [Camomile](https://github.com/pierreguillot/Camomile) to create VST instruments and Effects plugins using pure data under the hood. This makes it really nice to collaborate on plugins.

### `linux computer setup`

* install linux
* my external usb sound card is class compliant and worked without drivers
* download and donate to [Ardour](https://ardour.org/)
* install pure data eg `sudo apt-get install puredata`
* install https://github.com/pierreguillot/Camomile

```
sudo apt-get -qq update
sudo apt-get install -y libx11-dev libxrandr-dev libxinerama-dev libxcursor-dev libfreetype6-dev alsa libasound2-dev
git clone --recursive https://github.com/pierreguillot/Camomile.git
cd Camomile
cd Dependencies/LibPdBuild/LinuxMakefile && cmake .. -DCMAKE_BUILD_TYPE=Release && cd ../../..
make -Release # I needed to use the release flag to get it too work later on
cd ./plugins
./camomile
```

In ardour add `PATH_TO/camomile/plugins/build` to the VST3 path and re-scan.

## `creating and re-compiling plugins`

Add new plugins to the examples folder and re-run `plugins/camomile` to re-generate the plugin. 

## `using my instruments`

* clone the repo
* add the plugins to ./plugins/examples and re-generate them `cd .. && ./camomile`
* open the DAW and scan for VST3 plugins
* check the plugins show up in the menu system

## `credits`

* [Miller Puckette](http://msp.ucsd.edu/software.html)
* [Pierre Guillot](https://github.com/pierreguillot)
* [Pierre Massat](https://guitarextended.wordpress.com/2014/11/11/yellotron-a-mellotron-with-pure-data/)
