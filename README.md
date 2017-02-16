# docker-tools

## Note

I just found a script that probably works better. You can find it here:

* https://gist.github.com/mortensteenrasmussen/512f0566dbc3ef1cc4a2c47dd9cdb973
* https://github.com/docker/distribution/issues/2190#issuecomment-279343010

## registry-delete-untagged

Finds out untagged manifests and delete them.


## Setup

* Copy settings-sample to settings
* Edit the file with the correct settings


## Usage

USE AT YOUR OWN RISK

Run it from the current directory (backup your registry first)

    ./registry-delete-untagged
    
Afterwards you can do a garbage collection to delete the files for real

    docker exec registry /bin/registry garbage-collect /etc/docker/registry/config.yml
    
    
## Known issues

* The script has not been tested very well but it seems to work
* The script tries to delete things that have been deleted before (MANIFEST_UNKNOWN)
* Some things seem to be left behind that could have been deleted
* There's probably a better way to get an ubuntu container with curl inside


## Pull requests

Yes please!

I'm not an expert at the internals of the Docker Registry.
I just quickly hacked this thing together to free up some needed disk space.
If you know how to improve this script, please do so!
