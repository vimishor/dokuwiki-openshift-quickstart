Dokuwiki on OpenShift
=====================

This git repository helps you get up and running quickly w/ a Dokuwiki installation
on OpenShift.


Running on OpenShift
----------------------------

Create an account at https://www.openshift.com

Create a php application (you can call your application whatever you want)

    rhc app create dokuwiki php-5.4

Add this upstream dokuwiki repo

    cd dokuwiki
    git remote add upstream -m master git://github.com/openshift/dokuwiki-quickstart.git
    git pull -s recursive -X theirs upstream master
    # note that the git pull above can be used later to pull updates to Dokuwiki

Then push the repo upstream

    git push

That's it, you can now checkout your application at:

    http://dokuwiki-$yournamespace.rhcloud.com

The default user is 'admin' and the password should be printed out to console
after first `git push`. Please change the default password after first login.

* * *

### NOTES:

  Script from `GIT_ROOT/.openshift/action_hooks/deploy` is executed with every 
`git push`. Feel free to modify this script to learn how to use it to your 
advantage.  By default, this script will move content from Dokuwiki's `data` 
directory in `$OPENSHIFT_DATA_DIR`, where persistent storage is supported.

### Dokuwiki Security:

If you're doing more than just 'playing' be sure to change login credentials and 
read [security page](http://www.dokuwiki.org/security) from Dokuwiki website.
