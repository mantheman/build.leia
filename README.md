# build.leia - A shell script to build Kodi Leia from source

## Description
This is a complete hack to fetch(clone), update(pull), compile and install [Kodi](https://github.com/xbmc/xbmc) from source.

It uses the Z Shell (ZSH) as I find it more than capable for my needs.

The script also uses **sudo** to install Kodi and the binary-addons. Please make sure you are in the **sudoers** list.

Default installation dir is **/opt/Leia**. This can be changed by editing the PREFIX variable in **build.leia**.

See **build.leia --help** for your options.

## Options

### Fresh start

The script will first check to see if you have the Kodi Leia source in the directory specified in **etc/build.leia.conf**. If it's not there, it will ask you if you want it to clone the source from Github.

It will then ask you if you also want to compile the binary-addons later.

### Command line options

**build.leia --help** will show you a few examples of use

**build.leia --with=** - This is where the magic happens.

Your options are:

**--with=clean** - This will remove the **build-kodi** directory and recreate it.

**--with=dirty** - This will simply pull the updated source and compile as is.

**--with=addons** - This will clean and compile the binary-addons.

**--with=force** - This will compile Kodi even if there are no new updates.

You can use any of these options together, except from **clean** and **dirty**.

**build.leia --with=clean,addons,force** will remove the **kodi-build** directory, recreate it, check to see if there are updates from Github and even if there are no new updates, it will continue with the compilation and lastly it will do a **distclean** for the binary-addons and re-compile them.

## Troubleshooting

If you're experiencing problems, it really doesn't have anything to do with the script.

Please cd into your Leia source code: **cd ${HOME}/kodi/Leia/kodi-build** and run the following command: **cmake .. -DCMAKE_INSTALL_PREFIX=/opt/Leia**

You will see the complete output of the command and possibly find you're missing some libraries and/or tools necessary to compile Kodi. Install the missing libraries and/or tools and try again. Once you've sorted all this out, you're ready to run the script.

## Translations

I only know two languages, Norwegian and English, and therefore there are only these two availale.

If you want to help out with translation, please fork the project and copy the language files from **include/build.leia/language/**.

The **en_US.inc** is the most up-to-date file. I haven't fixed the Norwegian one yet.
