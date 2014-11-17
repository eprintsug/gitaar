gitaar
======

"git submodule" is a useful way to pull/push updates to a bazaar module in a development or deployment enviroment:

$ cd /opt/eprints3/lib/epm
$ git submodule add git@github.com:eprintsug/bootstrap.git

...however, the tools/epm utility bundled with EPrints won't work unless you maintain a .epmi file in your git repository too:

$ cd /opt/eprints3
$ tools/epm link_lib bootstrap # this fails unless there is a lib/epm/bootstrap/bootstrap.epmi

gitaar is a simple script to build a stub .epmi:

$ cd /opt/eprints3
$ git submodule add git@github.com:eprintsug/gitaar.git
$ gitaar/gitaar myrepo bootstrap
$ tools/epm link_lib bootstrap
$ tools/epm enable myrepo bootstrap
