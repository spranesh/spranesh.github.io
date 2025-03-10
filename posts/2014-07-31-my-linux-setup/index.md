# My lightweight linux setup


<!-- image:
  feature: https://raw.githubusercontent.com/spranesh/customisations/master/screenshot.png -->

My primary computing device for the last few years has been a 2009 netbook with
an SU2300 dual core processor, and 2GB memory. I've managed to keep it up to
date while being extremely performant and responsive by choosing the right set
of tools and avoiding software bloat. My entire desktop boots up in less than
70MB of RAM and is extremely responsive. Here are the various components that
make up my desktop:

<br />

![Screenshot of xmonad in the default spiral
tiling](https://raw.githubusercontent.com/spranesh/customisations/master/screenshot.png)

* *Operating System* : **Lubuntu**: For a scaffolding installation, I use the
  latest LTS of Lubuntu, a lightweight version of Ubuntu[^1]. This satisfies my
  requirements of stability, a large user community and regular updates. 

* *Window Manager* : **xmonad**: While the LXDE is a fairly functional and
  responsive desktop environment, I use xmonad as my window manager. It's a
  light weight, fast, tiling window manager written in Haskell. I am generally
  allergic to the mouse as an input device, and prefer to use the 70+ keys on my
  keyboard whenever possible. I've spent a good amount of time
  [customising](http://www.github.com/spranesh/customisations/tree/master/xmonad)
  my window manager setup -- it's configured to run standalone.

* *File Explorer* : **pcmanfm**: If there ever was a fast, lightweight, X file
  system browser, this is it. It's the default with LXDE and Lubuntu for a good
  reason.  Besides being extremely fast to startup, it can run in daemon mode
  (making startups even faster), and manage desktop wallpaper.

* *Network Manager* : **wicd**: It's been my choice of network managers for a
  while now, being able to handle any sort of Wifi network, auth, strength that
  I have had to deal with. I optionally use the wicd-curses UI via screen or the
  wicd-cli if I am connecting to a pre-configured network.

* *Terminal Emulator* : **lxterminal**: The default terminal emulator for LXDE,
  it is lightweight, and does a good job of staying out of one's way -- which is exactly
  what I require since I delegate most of my terminal management to screen (which also
  I [customise](http://www.github.com/spranesh/customisations/screen)).

* *Shell* : **zsh**: While bash is the unanimous choice for scripting, I don't
  think anything beats the power of zsh for interactive sessions. Previously
  complex configuration has also become much easier with
  [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh) to manage themes and
  plugins. It completes everything from arguments to git branch names and even suggests
  corrections for typos! Again, I have
  [customised](http://github.com/spranesh/customisations/zsh) my zsh configuration (this has
  gotten much smaller after oh-my-zsh).

* *Volume Control*: **alsamixer**: Good old alsamixer and it's command line
  cousin amixer to the rescue. Nothing to see here, really, except more lightweight
  tools!

* *Status Bar* : **dzen2**: I use dzen 2 as my panel / status bar. It consists
  of two sections -- the top left bar which xmonad manages (and pretty prints the
  current workspace and tiling modes), and the top right bar, which via a lightweight, completely
  non-portable[^2] hand written C-program displays memory, CPU, and battery statistics.

* *Music Player* : **cmus**, **audacious**: I switch betwee cmus, and audacious
  depending on whether I want to listen to a saved playlist (audacious), or my
  library (cmus). cmus is a console curses-based program, and does a very good
  job of library management, IMO. The latter is sort of a Winamp-clone on Linux.

* *Browser* : **chrome**, **firefox**,  **dwb** : I switch heavily between
  firefox and chrome as I have found that firefox does better at managing 20+
  tabs, and Chrome is more responsive in the fewer tabs scenarios. I use dwb, a
  lightweight, webkit based, browser that was inspired by the vimperator plugin,
  for most other light browsing (quick google search, etc..) as it has extremely
  good startup times for me - YMMV. With both chrome and firefox, I use vimium and
  vimperator respectively to keep my usage of the mouse to a minimum.

So, there you have it -- my light weight linux setup that's fast, functional, and
kind to my 5 year old netbook!

[^1]: Arch Linux would be a very good choice as well.
[^2]: It may work on other machines; I have not tested it. YMMV.

