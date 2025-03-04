# Apache WebDAV

This image is based on [`docker-apachewebdav`](https://github.com/mgutt/docker-apachewebdav) by mgutt.

## Configuration

Three settings are required for proper functioning:

* path to webdav share
  * expected under `/var/lib/dav/data`
  * **mount shared data volume as `/data/webdav:/var/lib/dav/data`**
* users/password
  * the expected location `/user.passwd` is sym-linked to `/var/lib/dav/private/user.passwd`
  * **mount shared data volume as `/data/private/webdav:/var/lib/dav/private`**
  * use `htpasswd -B /var/lib/dav/private/user.passwd name-of-the-user` to set up users (password will be queried interactively and stored as an encrypted string)
* file and folder permissions
  * set the environment variable `PUMASK` to `006` to create files with `660` and folders with `770`
