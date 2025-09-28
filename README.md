XFCE-SUPERKEY
=============

> [!IMPORTANT]
> This project is no longer maintained and is no longer necessary.
>
> When you press the **Left Super** key on its own, it will simulate the `Alt+Pause` shortcut
>   (verified on XUbuntu 24.04 with XFCE 4.18).
>
> For customization, please use **XFCE’s built-in keyboard shortcut editor** instead.

---

xfce-superkey allows you to open the whisker menu launcher in XFCE using the
Super key (also known as "Meta" or "the Windows key").
If you hold down the Super key it will still act as a modifier key, allowing
you to use it for other keyboard shortcuts.

xfce-superkey is a small desktop-agnostic application that runs in the background
as a daemon. It was forked from [ksuperkey][ksuperkey] by hanschen, which was
forked from [xcape][xcape] by Albin Olsson.


Installation
------------

Below are some generic instructions for how to compile xfce-superkey from source.

1. Install dependencies. 

    On Debian-based systems (including Ubuntu and Linux Mint), run:

    ```
    $ sudo apt-get install git gcc make libx11-dev libxtst-dev pkg-config
    ```

    On Fedora-based systems, run:
    ```
    $ sudo dnf install git gcc make libX11-devel libXtst-devel pkgconfig
    ```

    On some systems you also need to install the `build-essential` (or
    equivalent) package.

2. Clone project and compile:

    ```
    $ git clone https://github.com/JixunMoe/xfce-superkey.git
    $ cd xfce-superkey
    $ make
    ```

3. Install system-wide using e.g. `sudo` (optional):

    ```
    $ sudo make install
    ```

4. Launch xfce-superkey.

5. Set `xfce-superkey` as auto start. See [Xfce#Autostart][xfce-autostart].

Usage
-----

    $ xfce-superkey [-d] [-t <timeout ms>]

`-d`

Debug mode. Does not fork into the background.

`-t <timeout ms>`

If you hold a key longer than this timeout, xfce-superkey will not open the
menu. Default is 500 ms.


#### Example

    xfce-superkey

Makes left Super key to execute `xfce4-popup-whiskermenu` when pressed and
released on its own (does not affect existing keyboard combinations using the
Super key).


Note regarding xmodmap (may not relate to `xfce-superkey`)
----------------------------------------------------------

If you are in the habit of remapping keycodes to keysyms (e.g. using xmodmap),
there are two issues you may encounter:

1) You will need to restart xfce-superkey after every time you modify the mapping 
   from keycodes to keysyms (e.g. with xmodmap), or xfce-superkey will still use 
   the old mapping.
   
2) The key you wish to send must have a defined keycode. So for example, with
   `Control_L=Escape`, you need an Escape key defined in your xmodmap mapping. 
   (A workaround is to use 255, which some keyboards cannot send.)


Contact
-------

* Find the latest version of `ksuperkey` at
    https://github.com/hanschen/ksuperkey

    The author of `ksuperkey` can be reached at
    contact at hanschen dot org

* Find the latest version of `xfce-superkey` at
    https://github.com/JixunMoe/xfce-superkey

    The author of `xfce-superkey` can be reached at
    i at jixun dot moe

[ksuperkey]: https://github.com/hanschen/ksuperkey
[xcape]: https://github.com/alols/xcape
[xfce-autostart]: https://wiki.archlinux.org/index.php/Xfce#Autostart
