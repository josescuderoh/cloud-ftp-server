# FTP Server for Data Enablement

This container was created as a temporary solution for sharing intermediate data available on EC2 instance for data processing. It leverages the [`stilliard/pure-ftpd`](https://github.com/stilliard/docker-pure-ftpd) image to launch the server and enable active and passive ports.

In order to quickly launch this container:

1. Edit the remote directory that is mapped to the `home/files` directory in the `docker-compose.yml` file to mount the volume. Then, if required change the `FTP_USER_HOME` using the container path that was mapped.
2. Modify the username and password using the `.env` file.
3. Run `./start.sh` to run the container and `./stop.sh` to stop it.

Passive ports can be modified in `docker-compose` file and data inside the `home/files` directory is accessed through curl (or wget) using:

```sh
curl ftp://remote_ip/file_of_interest --user $FTP_USER:$FTP_PASS -o /local/path/file_of_interest
```

Or using ftp with active port 21 through command line (or FileZilla).