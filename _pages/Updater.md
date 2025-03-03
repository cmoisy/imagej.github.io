---
autogenerated: true
title: Updater
layout: page
categories: Plugins,ImageJ2
description: test description
---

{% include component-stats content='net.imagej:imagej-updater' %}The purpose of the ImageJ Updater is to keep you up-to-date with all components of ImageJ (or Fiji), i.e. the macros, scripts, plugins and the core components (libraries) needed by the plugins.

As of 2011, the ImageJ Updater can handle [3rd-party update sites](#Adding_update_sites "wikilink"), i.e. anybody can set up their own update site which users can follow.

Automatic Update
----------------

The Updater is a mechanism to update individual packages. It is automatically run when all the following conditions are met:

-   ImageJ was just started
-   ImageJ was started without parameters (i.e. no Drag 'n Drop onto the ImageJ icon)
-   ImageJ's files can be updated by the current user
-   There is a network connection

If there were updates since the Updater was run the last time, the user will be asked whether you want to run the Updater now or later:

![](/media/Up-to-date-check.png "Up-to-date-check.png")

In case you do not want to run the Updater upon startup, you can choose *Never*.

Starting the Updater explicitly
-------------------------------

The Updater can be run via {% include bc content='Help | Update...'%}.

Easy mode
---------

The Updater has two modes, the *Easy Mode* and the *Advanced Mode*. In the easy mode, you will only see the files that can be updated. The easy mode looks like this:

![](/media/Updater-easy-mode.png "Updater-easy-mode.png")

For technical reasons, a restart of ImageJ is required before the changes take effect. You can read about technical details [here](Uploading_plugins).

### Resolve dependencies

Some plugins require other components to be updated. For example, the [Simple Neurite Tracer](Simple_Neurite_Tracer) needs the [3D Viewer](3D_Viewer). If you have a locally modified version of the dependency (i.e. the Updater does not know that particular version), the Updater will ask you what to do:

![](/media/Updater-Resolve dependencies.png "Updater-Resolve_dependencies.png")

A typical scenario when you can have a locally modified version of a component is when you asked the respective plugin author for a change in a certain component and got a test version that you [installed manually](Installing_3rd_party_plugins).

You can keep the local version if you are certain that the version you have is new enough to work with the plugin noted under the text *A newer version might be required by*, otherwise you should consider to choose *Update <component>* instead.

Advanced mode
-------------

In the advanced mode, you can see details about the files, choose to skip updating selected components, and search by filename.

Note: in the advanced mode you can also upload plugins to your [update site](Update_Sites). The details for each component can be edited by writing below the respective entry. To save the changes, you have to upload the plugin to the server.

<figure><img src="/media/Snapshot of the Advanced Mode of the Updater.png" title="Snapshot_of_the_Advanced_Mode_of_the_Updater.png" width="750" alt="Snapshot_of_the_Advanced_Mode_of_the_Updater.png" /><figcaption aria-hidden="true">Snapshot_of_the_Advanced_Mode_of_the_Updater.png</figcaption></figure>

Starting the Updater manually
-----------------------------

Just click on the {% include bc content='Help | Update...'%} menu item:

![](/media/Fiji Updater-screenshot.png "Fiji_Updater-screenshot.png")

Adding update sites
-------------------

If you want to update plugins from other update sites than the principal one, follow [these instructions](How_to_follow_a_3rd_party_update_site).

You can also [set up and populate your own update site](How_to_set_up_and_populate_an_update_site).

Command-line usage
------------------

It is possible to drive the Updater through the command-line option *--update*. If you call that without arguments, it will show you what subcommands are available:

    ./ImageJ-<platform> --update

The simplest usage is to update either single files:

    ./ImageJ-<platform> --update update jars/ij.jar plugins/Simple_Neurite_Tracer.jar

or all files that would be marked for update in the interactive Updater by default:

    ./ImageJ-<platform> --update update

If you configured upload sites, you can also use the command-line version of the Updater to upload files:

    ./ImageJ-<platform> --update upload plugins/My_New_Cool_Plugin.jar

The full list of options available when running ImageJ from command line looks like this:

    Commands:
        diff [ --list-files | --javap | --class-file-diff | --hex-diff ] [<files>]
        list [<files>]
        list-uptodate [<files>]
        list-not-uptodate [<files>]
        list-updateable [<files>]
        list-modified [<files>]
        list-current [<files>]
        list-local-only [<files>]
        list-from-site <name>
        show [<files>]
        update [<files>]
        update-force [<files>]
        update-force-pristine [<files>]
        upload [--simulate] [--[update-]site <name>] [--force-shadow] [--forget-missing-dependencies] [<files>]
        upload-complete-site [--simulate] [--force] [--force-shadow] [--platforms <platform>[,<platform>...]] <name>
        list-update-sites [<nick>...]
        add-update-site <nick> <url> [<host> <upload-directory>]
        edit-update-site <nick> <url> [<host> <upload-directory>]

In order to update from command line using a specific update site (for example the BigDataViewer) use the following command:

    ./ImageJ-<platform> --update add-update-site BigDataViewer http://sites.imagej.net/Pietzsch/

Bootstrapping the updater
-------------------------

If you do not have ImageJ yet, you can download [bootstrap.js](http://update.imagej.net/bootstrap.js) and run it like this:

    jrunscript bootstrap.js help

This uses the **jrunscript** executable of your Java installation to run the Javascript file tracked in ImageJ's {% include github org='imagej' repo='imagej-updater' path='bin/bootstrap.js' label='source code repository' %}.

The `bootstrap.js` script was originally intended to fix broken [Fiji](Fiji) installations, and was subsequently enhanced to initialize the updater in an ImageJ 1.x-only directory -- or even from a complete fresh state.

Managing a mirror of ImageJ update sites
----------------------------------------

This instructions only cover the setting up of the synchronization. It does not cover the details of the actual server. The mirror can be server both via HTTP or FTP. Such configuration details are outside the scope of this.

-   Why would you want to do this?



The main reason is if you have systems with ImageJ installed that are behind a firewall with blocked internet access. Another reason is if you have multiple systems to update and a local mirror would be faster for you (and nicer for the ImageJ servers). Yet another reason is if you are not on North America, the updater runs very slow.

There is no rsync daemon to support for anonymous synchronization. If you want to keep a mirror of ImageJ update sites, please make a post on the [ImageJ Forum](http://forum.imagej.net/) to obtain an ssh account.

The rough idea is to have a cronjob to run rsync on ssh. Since this needs authentication, we use a ssh key with no passphrase. We also create a system user to do all of this and limit this ssh key for this function.

`$ sudo adduser --system fiji_mirror_sync`  
`$ sudo fiji_mirror_sync ssh-keygen -t rsa -b 4096 -C "Your institution"`

These instructions are valid for Ubuntu 14.04. Other distributions may handle system users differently and may not even create a home directory for them. In such case, the ssh key can be placed in {% include path content='/etc/ssh' %}, and the config options used with 'ssh -o' .

{% include file content='/home/fiji\_mirror\_sync/.ssh/config\|\|

    Host imagej
      Hostname code.imagej.net
      User your_account_username
    Host fiji
      Hostname fiji.sc
      User your_account_username
      ProxyCommand  ssh code.imagej.net netcat -w 120 %h %p

' %}

To prepare the known hosts files:

`$ ssh-keyscan -t rsa code.imagej.net | sudo -u fiji_mirror_sync tee -a /home/fiji_mirror_sync/.ssh/known_hosts`  
`$ sudo -u fiji_mirror_sync ssh imagej ssh-keyscan -t rsa fiji.sc | sudo -u fiji_mirror_sync tee -a /home/fiji_mirror_sync/.ssh/known_hosts`

Finally set up the cronjob with 'sudo crontab -u fiji\_mirror\_sync -e'

{% include file content='/var/spool/cron/...\|\|

    00 06 * * * rsync -azL --delete -e ssh imagej:imagej-update-site/ /var/www/fiji_update/mirrors/imagej
    10 06 * * * rsync -azL --delete -e ssh fiji:fiji-update-site/ /var/www/fiji_update/mirrors/fiji

' %}

Once the mirrors get populated, you can start using them on your ImageJ installations. Editing the URL of the existing ImageJ and Fiji update sites is not a good idea because any changes to them will be undone once the system gets internet access (it reads the original URLs from the Fiji wiki). There is a command line option to remove update-sites but it will not work for the ImageJ update site. Since there is no command-line option to disable an update site, ImageJ must be started with root permissions to do that. URLs for the new mirrors can be added with:

`$ ImageJ-linux64 --update add-update-site Fiji_mirror url_for_your_fiji_mirror`  
`$ ImageJ-linux64 --update add-update-site ImageJ_mirror url_for_your_imagej_mirror`

History
-------

The original updater was written in a frantic week in October 2008 in preparation for the first public [Fiji](Fiji) release, to be able to keep Fiji up-to-date.

In the course of one of two successful Google Summer of Code projects, the updater was rewritten from scratch (but in a [backwards-compatible manner](Backwards_Compatibility)) by Yap Chin Kiet under the mentorship of Mark Longair and Johannes Schindelin in 2009.

Johannes Schindelin got stuck with the maintainership and introduced third-party update sites (a feature that many claimed to desire, though no pinky was harmed by contributing any code) in the course of a very successful [hackathon](Hackathon#ImageJ_hackathons) at the Lawrence Berkeley National Laboratory in October 2010 and another one in February 2011 hosted by [LOCI](LOCI).

As of September 2012, the Fiji Updater has moved to [ImageJ2](ImageJ2). Details can be found in the announcement: [2012-09-14 - The Updater moved](2012-09-14_-_The_Updater_moved).
