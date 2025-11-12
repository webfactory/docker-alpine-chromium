# Docker Image with Chromium

This repo is used to build Alpine-based Docker images with a current version of Chromium installed.

No extra fuss, just the bare minimum to run Behat tests with a real, headless browser.

Based on the work in https://github.com/jlandure/alpine-chrome/. Since that repository is not maintained anymore and no new images are published, we build them ourselves.

Currently, no fancy versioning scheme for the resulting images has been set up, and there is no way to (re-)build a targeted Chromium version.

## Running with a `seccomp` profile

Launch the container using:

`docker container run --security-opt seccomp=$(pwd)/chrome.json ...`

The security profile is necessary to modify the allowed syscalls. See https://blog.jessfraz.com/post/how-to-use-new-docker-seccomp-profiles/ for the blog post and 
https://github.com/jessfraz/dotfiles/blob/main/etc/docker/seccomp/chrome.json for the original source of this profile.

Since then, it seems the Chromium requirements have evolved, so [another set of permissions needed to be granted](https://github.com/jlandure/alpine-chrome/issues/272).
