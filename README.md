gitaar
======

Build and publish EPrints Package Manager (EPM) packages from the command line.

````
$ cd /opt/eprints3/lib/epm
$ git submodule add git@github.com:eprintsug/bootstrap.git

# can't enable package without lib/epm/bootstrap/bootstrap.epmi
$ tools/epm link_lib bootstrap 
Error! 'bootstrap' is not installed or is an invalid epm identifier

# generate bootstrap.epmi
$ gitaar/gitaar build_epmi foo bootstrap
Wrote /opt/eprints3/lib/epm/bootstrap/bootstrap.epmi
$ tools/epm link_lib
/opt/eprints3/lib/lang/en/phrases/bootstrap.xml
/opt/eprints3/lib/themes/bootstrap/templates/default.xml
/opt/eprints3/lib/themes/bootstrap/static/bootstrap_assets/Scripts/admin_menus.js
[...]
$ tools/epm enable foo bootstrap
Message! Repository configuration reloaded!

# to create a distributable EPM you can either use the UI or:
$ gitaar/gitaar build_epm foo bootstrap
Wrote /opt/eprints3/var/cache/epm/bootstrap-1.0.0.epm

# to publish your EPM to the EPrints Bazaar you can either use the UI or:
$ gitaar/gitaar publish foo bootstrap
````
