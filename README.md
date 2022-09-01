This repo contains a workflow to download the current DellDisplayManager and a scoop bucket definition for the same.
The workflow runs each day at 2:30 UTC.
It runs as a docker build on ubuntu:latest and add the necessary binaries via apt to the base image.
The workflow downloads the latest binary from the homepage via wget.
The binary gets extracted via innoextract. 
The version string is determined from the downloaded executable via peres.

If the version already exists in the repo, the "Get version" step exits with 1 and the steps afterwards get skipped due to the unsuccessful build. 

Otherwise this is a new version. 
It will be uploaded as release to this repository and the corresponding version and url path gets written to the ddm.json file.
The updated ddm.json gets commited to this repo to make the scoop bucket having the most recent version.

The scoop bucket can be added with:

scoop bucket add DellDisplayManager https://github.com/SaschaJohn/DellDisplayManager

The ddm binary can be installed via:

scoop install ddm
