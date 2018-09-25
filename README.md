gitaar
======

Build and publish EPrints Package Manager (EPM) packages from the command line.

The example below installs the `bootstrap` theme.

# Install gitaar

when `/opt/eprints3/` is a git repository
```
$ cd /opt/eprints3
$ git submodule add https://github.com/eprintsug/gitaar.git
```

or for a packaged install use `git clone`
```
$ cd /opt/eprints3
$ git clone https://github.com/eprintsug/gitaar.git
```

# Pull in git-hosted package

Same caveat as installing WRT `git submodule` vs `git clone`.
```
$ git submodule add https://github.com/eprintsug/bootstrap.git lib/emp/bootstrap
```

# Install package

`epm` can't enable package a without a `.epmi` file (for example `lib/epm/bootstrap/bootstrap.epmi`)
```
$ tools/epm link_lib bootstrap 
Error! 'bootstrap' is not installed or is an invalid epm identifier
```

If required generate `bootstrap.epmi`
```
$ gitaar/gitaar build_epmi REPOID bootstrap
Wrote /opt/eprints3/lib/epm/bootstrap/bootstrap.epmi
```

Once a new `.epmi` is written, perform the linking and enable the package.
```
$ tools/epm link_lib bootstrap
/opt/eprints3/lib/lang/en/phrases/bootstrap.xml
/opt/eprints3/lib/themes/bootstrap/templates/default.xml
/opt/eprints3/lib/themes/bootstrap/static/bootstrap_assets/Scripts/admin_menus.js
[...]

$ tools/epm enable REPOID bootstrap
Message! Repository configuration reloaded!
```

# Publishing

To create a distributable EPM you can either use the UI or:
```
$ gitaar/gitaar build_epm REPOID bootstrap
Wrote /opt/eprints3/var/cache/epm/bootstrap-1.0.0.epm
```

To publish your EPM to the EPrints Bazaar you can either use the UI or:
```
$ gitaar/gitaar publish REPOID bootstrap
```
